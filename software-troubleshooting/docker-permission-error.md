# Docker Socket Permission Troubleshooting

## Case Status

**Resolution requires verification.** This case documents the troubleshooting workflow for a Docker permission error in my Ubuntu home lab. The final root cause and successful fix should be updated only after the commands and results are confirmed on the system.

## Environment

- Host platform: VMware virtual machine
- Guest operating system: Ubuntu 24.04
- Application stack: Docker and Open WebUI
- User context: Standard Linux user account

## Reported Problem

Docker commands returned a permission-related error when attempting to communicate with the Docker daemon.

A typical message may look similar to:

```text
permission denied while trying to connect to the Docker daemon socket
```

The exact error message from the system should be added here after verification.

## User Impact

The user could not start, stop, inspect, or manage Docker containers without elevated privileges. This blocked access to locally hosted applications such as Open WebUI.

## Initial Questions

- Is Docker installed correctly?
- Is the Docker service running?
- Does the command work with `sudo`?
- Is the current user a member of the `docker` group?
- What permissions are assigned to the Docker socket?
- Did the issue begin after installation, an update, or a user-account change?
- Has the user logged out and back in after a group-membership change?

## Diagnostic Process

### 1. Confirm Docker installation

```bash
docker --version
```

Expected result: Docker returns an installed version number.

### 2. Check Docker service status

```bash
systemctl status docker
```

Expected result: The Docker service is listed as active and running.

### 3. Test access with the current user

```bash
docker ps
```

If this returns a permission error, the problem may involve access to the Docker socket rather than the Docker service itself.

### 4. Compare the result with elevated privileges

```bash
sudo docker ps
```

If the command works with `sudo` but fails without it, the issue is likely related to user permissions or group membership.

### 5. Review the current user and groups

```bash
whoami
groups
```

Check whether the current user is listed as a member of the `docker` group.

### 6. Review Docker socket permissions

```bash
ls -l /var/run/docker.sock
```

A common configuration assigns the socket to the `root` user and `docker` group.

### 7. Add the user to the Docker group if appropriate

```bash
sudo usermod -aG docker "$USER"
```

After this change, the user normally needs to log out and sign back in, or restart the system, before the new group membership becomes active.

### 8. Verify updated group membership

```bash
groups
```

### 9. Test Docker without `sudo`

```bash
docker ps
docker run hello-world
```

## Possible Root Cause

A likely cause is that the standard user account does not have permission to access `/var/run/docker.sock` because the account is not an active member of the `docker` group.

This must remain listed as a **possible root cause** until the actual command outputs confirm it.

## Resolution Criteria

The case can be marked resolved only when all of the following are true:

- The Docker service is running
- The user is intentionally authorized to manage Docker
- Docker commands work without an unexpected permission error
- `docker run hello-world` completes successfully
- Open WebUI or the intended container starts and remains accessible

## Security Considerations

Membership in the `docker` group provides highly privileged access and can effectively allow root-level control of the system. It should only be granted to trusted users who require Docker administration.

The following shortcuts should be avoided:

- Changing the Docker socket to world-writable permissions
- Using insecure `chmod 777` fixes
- Granting Docker access to unnecessary accounts
- Publishing screenshots that reveal usernames, tokens, private IP addresses, or sensitive configuration data

## Escalation Decision

Escalate or investigate further if:

- The Docker service will not start
- The socket is missing
- The user is in the correct group but access still fails after a new login
- System logs show repeated daemon failures
- Storage, networking, or container-runtime errors appear
- The issue affects multiple users or services

Useful follow-up commands may include:

```bash
journalctl -u docker --no-pager
sudo systemctl restart docker
docker info
```

## User Communication

A clear explanation to a nontechnical user would be:

> Docker is installed, but your account may not currently have permission to communicate with the Docker service. I am checking the service, your account permissions, and the Docker connection before applying a secure fix.

## Lessons Demonstrated

This case demonstrates:

- Linux user and group permissions
- Service-status troubleshooting
- Docker daemon and socket concepts
- Testing with and without elevated privileges
- Secure access-control decisions
- Verification before closing a support case

## Final Result

**Pending verification.** Add the exact error, relevant command outputs, confirmed root cause, successful resolution, and final verification results after testing the Ubuntu system.
