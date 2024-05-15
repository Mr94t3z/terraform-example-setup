# Terraform Setup for REST API on AWS ECS

This repository contains the Terraform configuration files for deploying a REST API on AWS ECS. The architecture includes:
- HTTPS endpoint via an Application Load Balancer (ALB)
- ECS cluster with Fargate tasks
- Automated deployment using GitHub Actions

## Folder Structure
```
terraform-setup/
├── provider.tf
├── networking.tf
├── ecs.tf
├── load_balancer.tf
├── iam.tf
├── security_groups.tf
└── .github/
    └── workflows/
        └── deploy.yml
```

## Files Description
- **provider.tf**: Configures the AWS provider.
- **networking.tf**: Sets up VPC, subnets, internet gateway, and route tables.
- **ecs.tf**: Configures ECS cluster, task definition, and ECS service.
- **load_balancer.tf**: Sets up the Application Load Balancer, target group, and listener.
- **iam.tf**: Defines IAM roles and policies for ECS tasks.
- **security_groups.tf**: Configures security groups for the load balancer and ECS tasks.
- **deploy.yml**: GitHub Actions workflow for automating Terraform deployment on push to the production branch.

## Prerequisites
1. AWS account with necessary permissions.
2. GitHub repository with your REST API code.
3. Docker image of your REST API.
4. Terraform installed locally or in your CI/CD pipeline environment.

## Setup Instructions
1. **Clone the repository**:
   ```sh
   git clone https://github.com/Mr94t3z/terraform-example-setup
   cd terraform-example-setup
   ```

2. **Configure AWS credentials**:
   Ensure your AWS credentials are configured. You can use environment variables, AWS credentials file, or any other method supported by the AWS provider.

3. **Initialize Terraform**:
   ```sh
   terraform init
   ```

4. **Apply the Terraform configuration**:
   ```sh
   terraform apply -auto-approve
   ```

5. **GitHub Actions**:
   - Add the following secrets to your GitHub repository:
     - `AWS_ACCESS_KEY_ID`
     - `AWS_SECRET_ACCESS_KEY`
   - Push changes to the `production` branch to trigger the deployment workflow.

## Notes
- Replace `your-docker-image-url` and `your-certificate-arn` in the Terraform files with your actual Docker image URL and SSL certificate ARN.
- Adjust resource configurations as needed for your specific requirements.

## Cleanup
To destroy all resources created by Terraform, run:
```sh
terraform destroy -auto-approve
```

## Contact Me
Warpcast - https://warpcast.com/0x94t3z.eth