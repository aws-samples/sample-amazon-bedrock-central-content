---
title: "Amazon Bedrock AgentCore Starter Toolkit"
description: "CLI tools and higher-level abstractions for deploying, managing, and operating agents on Amazon Bedrock AgentCore"
url: "https://aws.github.io/bedrock-agentcore-starter-toolkit/index.html"
image: "/images/aws-logo.svg"
type: "getting-started"
authors:
  - name: "rodzanto"
    url: "https://github.com/rodzanto"
date: "2025-11-26"
skillLevel: "Intermediate"
---

# Amazon Bedrock AgentCore Starter Toolkit

The AgentCore Starter Toolkit provides CLI tools and higher-level abstractions for deploying and managing agents on Amazon Bedrock AgentCore. It simplifies the path from local development to production deployment with minimal code changes.

## Getting Started

1. **Install the toolkit**:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install bedrock-agentcore-starter-toolkit strands-agents boto3
   ```

2. **Create your agent** with the `BedrockAgentCoreApp` wrapper:
   ```python
   from bedrock_agentcore.runtime import BedrockAgentCoreApp
   from strands import Agent

   app = BedrockAgentCoreApp()

   @app.entrypoint
   def invoke(payload, context):
       agent = Agent(model="us.anthropic.claude-sonnet-4-5-20250929-v1:0")
       result = agent(payload.get("prompt", ""))
       return {"response": str(result)}

   if __name__ == "__main__":
       app.run()
   ```

3. **Configure deployment**: `agentcore configure -e agent.py`
4. **Deploy to AgentCore**: `agentcore launch`
5. **Test your agent**: `agentcore invoke '{"prompt": "Hello!"}'`
6. **Monitor**: `agentcore status`

## Key Features

- **Direct Code Deploy**: Deploy Python agents directly without containerization
- **Container Deploy**: Full container support for complex scenarios
- **Import Agent**: Migrate existing Bedrock Agents to AgentCore
- **Memory Integration**: Easy setup for short-term and long-term memory
- **Observability**: Automatic X-Ray tracing and CloudWatch integration
- **Gateway Integration**: Transform APIs into agent tools

## CLI Commands

| Command | Description |
|---------|-------------|
| `agentcore configure` | Set up agent deployment configuration |
| `agentcore launch` | Deploy agent to AgentCore Runtime |
| `agentcore invoke` | Test deployed agent with a prompt |
| `agentcore status` | Check agent deployment status |
| `agentcore destroy` | Remove all deployed resources |

## Use Cases

- Rapid prototyping to production deployment
- Migrating existing agents to AgentCore
- Setting up memory-enabled agents
- Deploying framework-agnostic agents

## Resources

- [Starter Toolkit Documentation](https://aws.github.io/bedrock-agentcore-starter-toolkit/index.html)
- [GitHub Repository](https://github.com/aws/bedrock-agentcore-starter-toolkit)
- [Runtime Quickstart](https://aws.github.io/bedrock-agentcore-starter-toolkit/user-guide/runtime/quickstart/)
- [Examples](https://aws.github.io/bedrock-agentcore-starter-toolkit/examples/)
