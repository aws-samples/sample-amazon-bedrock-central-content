# AWS Agentic AI Central

A hub to aggregate and search resources on agentic AI and how to implement it with AWS.

## Overview

This repository contains content for the Agentic AI Central website, designed to help customers:

- **Discover**: Service-agnostic design patterns for agentic AI and getting started guides for AWS services
- **Learn**: Search for AWS blogs, videos, workshops, and other resources on agentic AI
- **Build**: Blueprints for step-by-step implementation and code samples for specific use cases

## Content Structure

```
├── discover/
│   ├── design-patterns/       # Agentic AI design patterns
│   │   ├── react/             # ReAct: Reasoning and Acting
│   │   ├── tool-use/          # Tool Use: Function Calling Agents
│   │   ├── multi-agent/       # Multi-Agent Orchestration
│   │   ├── routing/           # Intelligent Request Distribution
│   │   ├── memory-augmented/  # Memory-Augmented Agents
│   │   ├── reflection/        # Self-Evaluation and Refinement
│   │   ├── parallelization/   # Concurrent Task Execution
│   │   ├── prompt-chaining/   # Sequential Task Decomposition
│   │   └── human-in-the-loop/ # Supervised Autonomy
│   └── getting-started/       # Getting started guides
│       ├── amazon-bedrock.md
│       ├── amazon-bedrock-agentcore.md
│       ├── amazon-bedrock-agentcore-starter-toolkit.md
│       ├── strands-agents.md
│       └── kiro.md
└── build/
    └── blueprints/            # Step-by-step implementation guides
        ├── agentcore-runtime-memory/
        ├── agentcore-code-interpreter/
        └── agentcore-gateway/
```

## Design Patterns

| Pattern | Description |
|---------|-------------|
| ReAct | Interleaves reasoning with actions in a feedback loop |
| Tool Use | Agents that invoke external functions and APIs |
| Multi-Agent | Multiple specialized agents collaborating |
| Routing | Directing requests to specialized handlers |
| Memory-Augmented | Agents with short-term and long-term memory |
| Reflection | Self-evaluation and iterative refinement |
| Parallelization | Concurrent execution of independent tasks |
| Prompt Chaining | Sequential task decomposition |
| Human-in-the-Loop | Human oversight at critical decision points |

## Getting Started Guides

- **Amazon Bedrock** - Foundation models through a unified API
- **Amazon Bedrock AgentCore** - Platform to deploy and operate agents at scale
- **AgentCore Starter Toolkit** - CLI tools for deploying agents to AgentCore
- **Strands Agents** - Open-source SDK for building AI agents
- **Kiro** - Agentic AI IDE for development

## Blueprints

- **AgentCore Runtime with Memory** - Deploy agents with persistent memory
- **AgentCore with Code Interpreter** - Agents with secure code execution
- **AgentCore with Gateway** - Connect agents to external APIs

## Contributing

See [CONTRIBUTING](CONTRIBUTING.md) for guidelines on how to contribute to this project.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
