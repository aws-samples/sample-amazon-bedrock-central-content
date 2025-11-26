---
title: "Strands Agents"
description: "Open-source SDK for building AI agents with a model-driven approach, supporting multiple model providers and deployment options"
url: "https://strandsagents.com/latest/documentation/docs/user-guide/quickstart/"
image: "/images/strands-logo.svg"
type: "getting-started"
authors:
  - name: "rodzanto"
    url: "https://github.com/rodzanto"
date: "2025-11-26"
skillLevel: "Beginner"
---

# Strands Agents

Strands Agents is an open-source SDK that takes a model-driven approach to building and running AI agents. It provides a simple, powerful way to create agents with tools, memory, and multi-agent capabilities while supporting multiple model providers including Amazon Bedrock, Anthropic, OpenAI, and more.

## Getting Started

1. **Install the SDK**:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install strands-agents strands-agents-tools
   ```

2. **Configure credentials**: Set up AWS credentials for Amazon Bedrock (default provider):
   ```bash
   aws configure
   ```

3. **Create your first agent**:
   ```python
   from strands import Agent, tool
   from strands_tools import calculator, current_time

   # Define a custom tool
   @tool
   def greet(name: str) -> str:
       """Greet someone by name."""
       return f"Hello, {name}!"

   # Create an agent with tools
   agent = Agent(tools=[calculator, current_time, greet])

   # Run the agent
   agent("What time is it and what is 25 * 48?")
   ```

4. **Run your agent**:
   ```bash
   python my_agent.py
   ```

## Key Features

- **Simple API**: Create agents in just a few lines of code
- **Multiple Model Providers**: Amazon Bedrock (default), Anthropic, OpenAI, Ollama, Mistral, and more
- **Built-in Tools**: Calculator, shell, file operations, and community-contributed tools
- **Custom Tools**: Easy `@tool` decorator for creating your own tools
- **Multi-Agent Patterns**: Support for Swarm, Graph, Workflow, and Agent-to-Agent (A2A) patterns
- **Streaming**: Real-time streaming of agent responses
- **Observability**: Built-in traces, metrics, and OpenTelemetry support

## Model Providers

```python
# Amazon Bedrock (default)
agent = Agent(model="anthropic.claude-sonnet-4-20250514-v1:0")

# OpenAI
from strands.models import OpenAIModel
agent = Agent(model=OpenAIModel(model_id="gpt-4"))

# Ollama (local)
from strands.models import OllamaModel
agent = Agent(model=OllamaModel(model_id="llama3"))
```

## Use Cases

- Building conversational AI assistants
- Creating tool-using agents for automation
- Multi-agent systems for complex workflows
- Rapid prototyping of agentic applications

## Resources

- [Official Quickstart Guide](https://strandsagents.com/latest/documentation/docs/user-guide/quickstart/)
- [GitHub Repository](https://github.com/strands-agents/sdk-python)
- [Community Tools](https://strandsagents.com/latest/documentation/docs/user-guide/concepts/tools/community-tools-package/)
- [Examples](https://strandsagents.com/latest/documentation/docs/examples/)
