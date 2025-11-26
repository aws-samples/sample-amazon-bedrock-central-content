---
title: "Amazon Bedrock AgentCore"
description: "Agentic platform to build, deploy, and operate highly capable agents securely at scale with any framework and any model"
url: "https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/agentcore-get-started-toolkit.html"
image: "/images/aws-logo.svg"
type: "getting-started"
authors:
  - name: "rodzanto"
    url: "https://github.com/rodzanto"
date: "2025-11-26"
skillLevel: "Intermediate"
---

# Amazon Bedrock AgentCore

Amazon Bedrock AgentCore is an agentic platform to build, deploy, and operate highly capable agents securely at scale. AgentCore provides fully-managed services that work with any framework (CrewAI, LangGraph, LlamaIndex, Google ADK, OpenAI Agents SDK, Strands Agents) and any foundation model—eliminating the choice between open-source flexibility and enterprise-grade security.

## Getting Started

1. **Set up AWS permissions**: Attach the `AmazonBedrockAgentCoreFullAccess` managed policy to your user/role
2. **Install the AgentCore Starter Toolkit**:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install "bedrock-agentcore-starter-toolkit>=0.1.21" strands-agents strands-agents-tools boto3
   ```
3. **Create your agent**: Write your agent code using any framework (e.g., Strands)
4. **Configure**: Run `agentcore configure -e agent.py` to set up deployment options
5. **Deploy**: Run `agentcore launch` to deploy to AgentCore Runtime
6. **Test**: Use `agentcore invoke '{"prompt": "Hello!"}'` to test your agent

## Key Services

- **Runtime**: Serverless deployment with session isolation and support for workloads up to 8 hours
- **Memory**: Persistent short-term and long-term memory across interactions
- **Gateway**: Transform existing APIs into agent-compatible tools
- **Identity**: Secure authentication and access management
- **Code Interpreter**: Secure code execution in isolated sandboxes
- **Browser Tool**: Fast, secure browser runtime for web interactions
- **Observability**: Real-time monitoring, tracing, and debugging via CloudWatch

## Key Benefits

- **Framework Agnostic**: Works with any agent framework or custom code
- **Zero Infrastructure**: Fully managed, no servers to provision
- **Enterprise Security**: Complete session isolation, VPC connectivity, PrivateLink support
- **Production Ready**: Built-in observability, scaling, and reliability

## Use Cases

- Deploy production-ready AI agents at scale
- Build agents with persistent memory and context
- Connect agents to enterprise tools and APIs
- Monitor and debug agent behavior in production

## Resources

- [Official Getting Started Guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/agentcore-get-started-toolkit.html)
- [AgentCore Console](https://console.aws.amazon.com/bedrock-agentcore/)
- [AgentCore Documentation](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/)
