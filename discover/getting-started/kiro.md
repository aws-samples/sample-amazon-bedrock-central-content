---
title: "Kiro"
description: "Agentic AI IDE that helps developers build from prototype to production with specs, steering, and agent hooks"
url: "https://kiro.dev/docs/getting-started/installation/"
image: "/images/kiro-logo.svg"
type: "getting-started"
authors:
  - name: "rodzanto"
    url: "https://github.com/rodzanto"
date: "2025-11-26"
skillLevel: "Beginner"
---

# Kiro

Kiro is an agentic AI IDE designed to help developers build from prototype to production. It combines the power of AI assistance with structured development workflows through specs, steering rules, and agent hooks—enabling you to guide AI with custom rules and context while keeping code secure with privacy controls.

## Getting Started

1. **Download Kiro**: Get the installer for your operating system from [kiro.dev/downloads](https://kiro.dev/downloads/)

2. **Install and launch**: Run the installer and open Kiro IDE

3. **Sign in**: Log in with GitHub, Google, AWS Builder ID, or AWS IAM Identity Center

4. **Open a project**: Open an existing project or create a new one

5. **Start coding**: Use the chat interface to interact with Kiro's AI assistant

## Key Features

- **Specs**: Structured way to build and document features with requirements, design, and implementation tasks
- **Steering**: Custom rules and context that guide AI behavior across your project (`.kiro/steering/*.md`)
- **Agent Hooks**: Automated agent executions triggered by events (file saves, messages, etc.)
- **MCP Integration**: Connect external tools and data sources via Model Context Protocol
- **Privacy Controls**: Keep code secure with configurable privacy settings

## Specs Workflow

Specs provide a formalized approach to feature development:

1. **Requirements**: Define what you want to build with acceptance criteria
2. **Design**: Create technical design with correctness properties
3. **Tasks**: Break down implementation into manageable steps
4. **Implementation**: Let Kiro work through tasks with your guidance

## Steering Rules

Guide AI behavior with steering files in `.kiro/steering/`:

```markdown
# Project Guidelines

## Code Style
- Use TypeScript for all new code
- Follow functional programming patterns
- Write tests for all new features

## Architecture
- Use the repository pattern for data access
- Keep components small and focused
```

## Agent Hooks

Automate workflows with hooks triggered by:
- File saves (e.g., update tests when code changes)
- Messages sent to the agent
- Session creation
- Manual triggers via UI

## Use Cases

- Structured feature development with AI assistance
- Maintaining consistent coding standards across teams
- Automating repetitive development tasks
- Building complex features with incremental guidance

## Resources

- [Official Documentation](https://kiro.dev/docs/)
- [Installation Guide](https://kiro.dev/docs/getting-started/installation/)
- [Specs Documentation](https://kiro.dev/docs/features/specs/)
- [Steering Guide](https://kiro.dev/docs/features/steering/)
