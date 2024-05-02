# Terraform Blue-Green Deployment Tutorial

This tutorial demonstrates blue-green deployments using Terraform to ensure minimal downtime by maintaining synchronized production environments.

## Overview
- Provision VPCs, security groups, and load balancers.
- Deploy web servers for blue and green environments.
- Use feature toggles for deployment strategies.
- Perform canary testing and promote the green environment.

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
