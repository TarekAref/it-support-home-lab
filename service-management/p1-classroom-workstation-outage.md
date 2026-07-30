# Simulated P1 Classroom Workstation Outage

> **This is a simulated educational service-desk scenario. It does not represent access to Wake Tech systems or an actual employer incident.**

## Scenario Summary

An instructor reports that the primary classroom workstation is not functioning immediately before a scheduled class. The instructor cannot access required instructional software or display course materials, and the issue is affecting the start of class.

## Business and Academic Impact

- A scheduled class cannot begin normally
- The instructor cannot access required teaching tools
- Multiple students are affected
- The disruption is time-sensitive
- Delayed restoration could result in lost instructional time

## ITIL Classification

- **Record type:** Incident
- **Category:** End-user computing / Classroom technology
- **Impact:** High — one class and multiple students affected
- **Urgency:** High — class is beginning now
- **Priority:** P1 in this simulated scenario
- **Initial objective:** Restore instructional service as quickly as possible

Priority definitions vary by organization. In a real environment, the ticket would follow the college’s approved priority matrix and escalation procedures.

## Initial User Communication

Acknowledge the issue immediately and set expectations:

> I understand the workstation issue is preventing your class from starting. I’m treating this as urgent. I’ll first work on the fastest safe way to restore instruction, then continue diagnosing the underlying cause.

## Initial Questions

1. What happens when the workstation is powered on?
2. Is the computer completely unresponsive, or is only one application affected?
3. Is the display blank, frozen, or showing an error?
4. Can the instructor sign in?
5. Is the projector or classroom display receiving a signal?
6. Did the workstation work during the previous class?
7. Were any updates, installations, or hardware changes recently made?
8. Are network-dependent applications also unavailable?
9. Is an alternate instructor workstation or loaner device available?

## Rapid Triage Process

### 1. Confirm the Scope

Determine whether the problem affects:

- Only the workstation
- The monitor or projector
- The instructor account
- A specific application
- Network access
- Multiple classroom devices
- A broader campus service

### 2. Check Physical and Power Conditions

- Confirm power to the workstation and displays
- Check power cables and power strips
- Verify video, keyboard, mouse, and network connections
- Look for status lights, fan activity, or startup sounds
- Confirm the correct display input is selected

### 3. Identify the Fastest Safe Workaround

Possible temporary service-restoration options:

- Reconnect or restart the affected display
- Use an alternate video connection
- Move the instructor to an available classroom workstation
- Provide an approved loaner laptop
- Use a web-accessible version of the instructional material
- Assist the instructor with a temporary alternate classroom setup

The goal is to restore teaching first when a safe workaround is available.

### 4. Perform Basic Workstation Diagnostics

If the device powers on:

- Observe startup and sign-in behavior
- Record any error message exactly
- Check keyboard and mouse response
- Test local applications
- Test network connectivity
- Confirm whether the issue affects one user or all users
- Check Task Manager if the system is responsive
- Review Device Manager or Event Viewer when appropriate

If the device does not power on:

- Verify outlet and power cable
- Test a known-good power source when permitted
- Check docking station or power adapter status
- Avoid opening equipment unless authorized and trained

## Example Diagnostic Commands

Use only when the system is responsive and policy permits:

```powershell
hostname
whoami
ipconfig /all
ping 127.0.0.1
ping <default-gateway>
nslookup example.edu
```

Sensitive information such as internal hostnames, usernames, IP addresses, and asset identifiers should not be placed in a public portfolio.

## Escalation Criteria

Escalate immediately when:

- The outage appears to affect multiple classrooms or a shared service
- There is evidence of a network, authentication, or infrastructure outage
- The workstation has a suspected hardware failure
- Administrative credentials or restricted tools are required
- The issue involves classroom-control systems outside the technician’s authority
- A security incident is suspected
- The approved response-time target may be missed

The escalation should include:

- Ticket number
- Classroom location
- Number of users affected
- Exact symptoms
- Troubleshooting already completed
- Workaround status
- Error messages
- Requested assistance

## Example Ticket Notes

**Reported issue:** Instructor unable to use primary classroom workstation at class start.

**Impact:** One scheduled class and multiple students affected.

**Actions taken:**

1. Contacted instructor and confirmed the issue.
2. Verified workstation power, display input, and cable connections.
3. Determined whether sign-in, application, display, or network access was failing.
4. Attempted an approved temporary workaround to restore instruction.
5. Documented error messages and diagnostic results.
6. Escalated to the appropriate support team when needed.

**Current status:** Simulated scenario — no actual device was serviced.

## Resolution Verification

Before closing the incident, confirm:

- The instructor can sign in
- Required instructional software opens
- Course materials are accessible
- The classroom display functions
- Network access is available if required
- Audio and peripherals work when needed
- The instructor confirms that class can continue

## Closure Communication

> The classroom workstation and required teaching functions have been tested, and the instructor confirmed that instruction can continue. The incident record includes the troubleshooting steps, resolution, and any follow-up work required.

## Follow-Up and Problem Management

If similar incidents recur:

- Review ticket history for patterns
- Identify common hardware, software, or configuration causes
- Consider preventive maintenance
- Review classroom startup procedures
- Update the knowledge base
- Escalate recurring failures for problem management

## Knowledge Article Opportunity

A knowledge-base article could be created for:

- Classroom workstation has power but no display
- Projector displays no signal
- Instructor cannot access approved software
- Classroom workstation cannot reach the network
- Approved temporary classroom workstation workaround

## Skills Demonstrated

- Incident classification and prioritization
- Rapid response to business disruption
- Customer communication under time pressure
- Hardware, software, and network triage
- Workaround selection
- Ticket documentation
- Escalation judgment
- Resolution verification
- Knowledge management
- Continuous improvement

## Lessons Learned

A high-priority support case is not only about finding the technical root cause. The immediate objective is restoring the user’s essential service safely, communicating clearly, documenting actions, and escalating quickly when the issue exceeds the technician’s authority or tools.
