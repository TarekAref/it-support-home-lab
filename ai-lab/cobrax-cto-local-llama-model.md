# CobraX CTO — Local Llama Model Lab

## Project Status

**In development**

This case documents my work building a local, private AI assistant using **Llama 3.2 3B**, **Ollama**, Python, and an Ubuntu Linux environment.

The goal is to create an AI system that can operate locally without depending on a cloud-hosted model, helping protect private company data and support future internal engineering workflows.

## Project Objective

The CobraX CTO model is designed as an early local AI technical advisor that can support:

- Technical planning
- Architecture discussions
- Troubleshooting guidance
- Security-focused decision-making
- Documentation and internal knowledge workflows
- Future coordination with additional local AI agents

This is an experimental educational project and is not presented as a production-ready enterprise system.

## Lab Environment

- Ubuntu Linux virtual-machine environment
- Python
- Ollama
- Llama 3.2 3B base model
- Custom Ollama Modelfile
- Docker and local development tools
- Git and GitHub
- Documentation and test folders

The original CobraX Core workspace was organized under:

```text
~/CobraX_Core
```

## Base Model Setup

The base model was pulled locally with Ollama:

```bash
ollama pull llama3.2:3b
```

Running the model locally allows testing without sending prompts or project information to a third-party cloud model provider.

## Custom Model Creation

A custom Ollama model was created from a project Modelfile:

```bash
ollama create cobrax-CTO -f models/cobrax-CTO.Modelfile
```

The custom model name is:

```text
cobrax-CTO
```

The Modelfile is intended to define the model's role, instructions, behavior, and response expectations.

## Application Execution

The model was designed to be called through a Python application:

```bash
python src/main.py --model cobrax-CTO
```

This separates the application logic from the local model runtime and makes it easier to test or replace models later.

## Local-First Architecture

The project follows a local-first approach:

1. The Llama model runs through Ollama on the local machine.
2. Python sends prompts to the local Ollama service.
3. The custom model instructions guide the CTO assistant's behavior.
4. Project documentation and security rules remain in the local workspace.
5. Future agents may communicate through controlled internal workflows.

## Privacy and Security Goals

The design goals include:

- Reduce unnecessary cloud dependency
- Keep sensitive prompts and company data local
- Avoid storing API keys in source code
- Separate configuration from application logic
- Document restart and recovery procedures
- Apply least-privilege principles where possible
- Review model output before acting on recommendations

A local model does not automatically make a system secure. The host, Docker configuration, permissions, logs, backups, model files, and user access still require protection.

## Documentation Completed

The project workspace includes or has included documentation for:

- Build instructions
- Ollama restart procedures
- Security rules
- Model configuration
- Testing structure
- Local development workflow

Examples of planned or created documentation paths include:

```text
docs/manual/BUILD_GUIDE.md
docs/runbooks/OLLAMA_RESTART.md
docs/runbooks/SECURITY_RULES.md
```

## Troubleshooting Areas

Areas tested or considered during development include:

- Confirming that Ollama is installed and running
- Pulling the correct base model
- Creating a custom model from a Modelfile
- Resolving Docker and Linux permission issues
- Confirming the local Ollama service is reachable
- Testing model names and command syntax
- Restarting Ollama after service interruption
- Separating application errors from model-runtime errors

Useful checks include:

```bash
ollama list
ollama ps
systemctl status ollama
```

Where Ollama is running as a user process rather than a system service, the exact service check may differ.

## Verification Plan

The model should be considered verified only after confirming:

- `llama3.2:3b` is available locally
- `cobrax-CTO` appears in `ollama list`
- The model responds directly through Ollama
- The Python application can call the correct model
- No credentials or sensitive data are written to GitHub
- Expected behavior is tested with repeatable prompts
- Failures and limitations are documented honestly

## Current Limitations

- The project is still under development.
- Model responses may be inaccurate or inconsistent.
- The model has not been independently security audited.
- Enterprise scalability has not been demonstrated.
- Human review is required before using model output for important technical, security, financial, or business decisions.
- Future multi-agent architecture remains a planned phase.

## Skills Demonstrated

- Linux administration fundamentals
- Local LLM deployment
- Ollama model management
- Python application integration
- Modelfile configuration
- Docker and permissions troubleshooting
- Security-conscious system design
- Technical documentation
- Testing and verification planning
- Honest communication of project limitations

## Next Development Steps

1. Verify the current Ubuntu and Ollama versions.
2. Record the exact hardware resources assigned to the VM.
3. Add sanitized Modelfile examples that contain no private instructions.
4. Add repeatable test prompts and expected outcomes.
5. Document service recovery after a restart.
6. Measure response time and system-resource use.
7. Add an architecture decision record for the local-first design.
8. Define secure communication rules for future AI agents.

## Portfolio Note

This file documents the architecture, commands, troubleshooting process, and security considerations for the project. It does not publish proprietary prompts, private company information, passwords, tokens, or confidential model configuration.
