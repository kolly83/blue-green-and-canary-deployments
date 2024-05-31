# Terraform Blue-Green Deployment Tutorial

This tutorial demonstrates blue-green deployments using Terraform to ensure minimal downtime by maintaining synchronized production environments.

## Overview
- Provision VPCs, security groups, and load balancers.
- Deploy web servers for blue and green environments.
- Use feature toggles for deployment strategies.
- Perform canary testing and promote the green environment.

## Blue-Green Deployment
This workflow lets you:

Test the green environment and identify any errors before promoting it. Your configuration still routes traffic to the blue environment while you test, ensuring near-zero downtime.
Easily roll back to the previous deployment in the event of errors by redirecting all traffic back to the blue environment.
![image](https://github.com/kolly83/blue-green-and-canary-deployments/assets/18192450/68935ab3-d942-42a4-980e-1f4de36b72f0)

## Canary and Rolling Deployment
You can use blue-green deployments for canary tests. After the green environment is ready, the load balancer sends a small fraction of the traffic to the green environment (in this example, 10%).
![image](https://github.com/kolly83/blue-green-and-canary-deployments/assets/18192450/101d5f23-f37f-4e81-be70-b297c70e2c54)

If the canary test succeeds without errors, you incrementally direct traffic to the green environment (50/50 — split traffic). Finally, you redirect all traffic to the green environment. After verifying the new deployment, you can destroy the old, blue environment. The green environment is now the current production service.
![image](https://github.com/kolly83/blue-green-and-canary-deployments/assets/18192450/95c73778-4f06-4aca-a345-cea8a6b388b0)


## Prerequisites
- Terraform installation.
- Basic AWS EC2 and VPC knowledge.
- AWS account access.

## Repository Files
- `main.tf`: Sets up the VPC, security groups, and load balancers.
- `variables.tf`: Defines essential variables like region and CIDR blocks.
- `blue.tf`: Configures two AWS instances with web servers as "version 1.0".
- `init-script.sh`: Script to initialize the web server.
- `terraform.tf`: Specifies Terraform and AWS provider versions.
- `.terraform.lock.hcl`: Locks dependencies for consistency.

## Steps
1. **Infrastructure Setup**: Establish networking and blue environment servers.
2. **Green Environment Setup**: Set up the alternative green servers.
3. **Feature Toggles and Testing**: Implement toggles and test with a canary release.
4. **Promotion**: Gradually shift traffic to the green environment.

## Conclusion
Leverage Terraform for efficient blue-green deployments to enhance CI/CD processes and minimize update risks.

# Notes
Learn how to use Terraform and AWS's Application Load Balancers for canary tests and blue/green deployments. Learn how to add feature flags to your Terraform configuration by using variables and conditionals. Follow along with [this
tutorial](https://learn.hashicorp.com/tutorials/terraform/blue-green-canary-tests-deployments) on HashiCorp Learn.
