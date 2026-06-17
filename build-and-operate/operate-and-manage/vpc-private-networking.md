---
title: "Keep Bedrock traffic private"
description: "Stand up the Bedrock PrivateLink endpoints your workloads need, reach them from on-prem and other VPCs, scope who can use them, and audit the network path"
type: "operate-and-manage"
category: "security"
date: "2026-06-14"
services: ["Amazon Bedrock", "AWS PrivateLink"]
---

AWS PrivateLink gives Bedrock an interface endpoint inside your VPC, so API calls reach the service over private IPs instead of an internet gateway, NAT, or VPN. Networking Bedrock privately is four jobs: stand up the right endpoints, reach them from on-premises and other VPCs, scope who can use them, and audit the network path.

## Keep traffic private

Each API surface has its own endpoint (`com.amazonaws.<region>.<suffix>`): `bedrock-runtime` for inference, `bedrock` for the control plane, `bedrock-mantle` for the OpenAI-compatible engine, plus FIPS variants. Enable Private DNS so SDK calls resolve to private IPs with no code change.

- [Docs: See all Bedrock VPC endpoint service names](https://docs.aws.amazon.com/bedrock/latest/userguide/vpc-interface-endpoints.html)

## Reach endpoints from on-prem and other VPCs

The managed Private DNS only resolves inside the endpoint's own VPC, so hybrid and multi-VPC access needs a centralized endpoint VPC, Transit Gateway or Direct Connect/VPN, and shared Route 53 DNS. AWS documents the full reference architecture.

- [Docs: See centralized access to VPC private endpoints](https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/centralized-access-to-vpc-private-endpoints.html)

## Secure the path

Scope each endpoint with a VPC endpoint policy (principals, actions, models), restrict the endpoint security groups to HTTPS from your app subnets, and add an `aws:SourceVpce` condition so `bedrock:InvokeModel` only works through approved endpoints. For org-wide IAM and SCPs, see the Authenticate and control access card.

- [Docs: See Bedrock VPC endpoint policy examples](https://docs.aws.amazon.com/bedrock/latest/userguide/vpc-interface-endpoints.html#vpc-endpoint-policy)
- [Docs: See the aws:SourceVpce condition key](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-sourcevpce)

## Audit the network path

Enable VPC Flow Logs to capture the IP traffic to and from your endpoint network interfaces, so you can confirm Bedrock calls traverse the private endpoints.

- [Docs: See VPC Flow Logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html)
