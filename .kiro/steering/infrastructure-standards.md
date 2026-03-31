---
name: Infrastructure & Deployment Standards
description: AWS CDK standards, deployment safety rules, cost awareness guidelines, and approved infrastructure patterns for IaC projects.
inclusion: fileMatch
fileMatchPattern: "**/{cdk,infra,infrastructure,deploy,cloudformation}/**/*"
---

# Infrastructure & Deployment Standards

These guidelines activate when working with infrastructure code.

## Approved Infrastructure Patterns

- **IaC Tool**: AWS CDK with TypeScript (preferred) or CloudFormation
- **Hosting**: AWS Amplify, Vercel, or AWS Lambda + API Gateway
- **Database**: Amazon RDS (PostgreSQL), DynamoDB, or Aurora Serverless
- **Storage**: Amazon S3 with appropriate bucket policies
- **CDN**: CloudFront for static assets

## AWS CDK Standards

- Use L2 constructs over L1 (Cfn) constructs whenever available
- Enable encryption at rest for all storage resources (S3, RDS, DynamoDB)
- Enable access logging for S3 buckets and API Gateway
- Use `RemovalPolicy.RETAIN` for production databases and storage
- Tag all resources with: `project`, `environment`, `owner`, `cost-center`
- Never use `*` in IAM policy resources — scope to specific ARNs
- Enable point-in-time recovery for DynamoDB tables
- Use VPC for database resources — no public database endpoints

## Deployment Safety

- All infrastructure changes must go through `cdk diff` before `cdk deploy`
- Enable termination protection on production stacks
- Use separate AWS accounts or at minimum separate stacks for dev/staging/prod
- Never deploy directly to production — always go through staging first
- Implement health checks and rollback triggers for deployments

## Cost Awareness

- Use auto-scaling where appropriate — don't over-provision
- Set billing alarms for unexpected cost spikes
- Prefer serverless (Lambda, DynamoDB on-demand) for prototypes to minimize idle costs
- Clean up unused resources — delete old stacks, unused S3 buckets, etc.
