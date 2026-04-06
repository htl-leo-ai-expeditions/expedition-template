# Coding Agent Container

A Docker image for running isolated coding agents focused on TypeScript and .NET development.

## What's included

| Tool | Purpose |
|------|---------|
| Node.js / npm | TypeScript/JavaScript runtime and package manager |
| .NET SDK 10.0 | .NET development |
| Python 3 | Scripting support |
| Git | Version control |
| curl | HTTP requests |
| librsvg2-bin | SVG rendering (`rsvg-convert`) |
| ccusage | Claude token usage tracking |
| @mermaid-js/mermaid-cli | Diagram generation |
| @openai/codex | OpenAI Codex CLI |
| @github/copilot | GitHub Copilot CLI |
| Claude Code | AI coding agent (`claude`) |

## Security

The container runs as a non-root user (`appuser`) with passwordless `sudo` access, balancing isolation with the flexibility agents need to install dependencies or modify the environment.

## Usage

Build the image:

```bash
docker build -t coding-agent .
```

Run a container:

```bash
docker run -it coding-agent bash
```
