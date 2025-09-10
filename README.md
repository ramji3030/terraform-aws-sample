# Terraform AWS Sample

A comprehensive sample Terraform project demonstrating AWS infrastructure provisioning using the [HashiCorp AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest).

## Overview

This project provides practical examples of how to use Terraform to provision and manage AWS infrastructure resources declaratively. It serves as a learning resource for Infrastructure as Code (IaC) practices with AWS and demonstrates creating EC2 instances, S3 buckets, IAM roles, and networking components.

## Prerequisites

Before running this project, ensure you have:

- [Terraform](https://www.terraform.io/downloads.html) installed (v1.0+)
- [AWS CLI](https://aws.amazon.com/cli/) configured with appropriate credentials
- AWS account with sufficient permissions to create resources
- Valid AWS access keys configured (via `aws configure` or environment variables)

## Project Structure

```
terraform-aws-sample/
├── main.tf          # Main Terraform configuration
├── README.md        # This file
└── .gitignore       # Git ignore file for Terraform
```

## Usage

### 1. Clone the Repository

```bash
git clone https://github.com/ramji3030/terraform-aws-sample.git
cd terraform-aws-sample
```

### 2. Configure AWS Credentials

Ensure your AWS credentials are configured:

```bash
aws configure
```

Or set environment variables:

```bash
export AWS_ACCESS_KEY_ID="your-access-key-id"
export AWS_SECRET_ACCESS_KEY="your-secret-access-key"
export AWS_DEFAULT_REGION="us-east-1"
```

### 3. Initialize Terraform

```bash
terraform init
```

### 4. Plan the Deployment

```bash
terraform plan
```

### 5. Apply the Configuration

```bash
terraform apply
```

### 6. Verify the Deployment

Check the created resources in AWS Console or using AWS CLI:

```bash
aws ec2 describe-instances --filters "Name=tag:Name,Values=terraform-sample-instance"
aws s3 ls | grep terraform-sample
aws iam list-roles | grep terraform-sample
```

### 7. Clean Up Resources

When you're done, destroy the resources to avoid charges:

```bash
terraform destroy
```

## What This Project Creates

- **EC2 Instance**: A t2.micro instance with security group and key pair
- **S3 Bucket**: A private S3 bucket with versioning enabled
- **IAM Role**: An IAM role with basic S3 access permissions
- **Security Group**: A security group allowing SSH access
- **Key Pair**: An EC2 key pair for instance access

## Configuration Details

The main.tf file includes:

- **AWS Provider**: Configuration to connect to your AWS account
- **EC2 Instance**: Creates a Linux instance with proper tags and security
- **S3 Bucket**: Private bucket with versioning for storage
- **IAM Resources**: Role and policies for secure access
- **Networking**: Security groups for controlled access
- **Output Values**: Displays important resource information

## Customization

You can customize the deployment by modifying variables in main.tf:

- **Region**: Change the AWS region for deployment
- **Instance type**: Modify EC2 instance specifications
- **Bucket name**: Adjust S3 bucket naming
- **Tags**: Update resource tags for organization

## Key Features Demonstrated

- **Resource Management**: Creating, updating, and destroying AWS resources
- **Dependencies**: Managing resource dependencies and creation order
- **Tags**: Proper tagging strategy for resource organization
- **Security**: IAM roles and security groups for secure access
- **Storage**: S3 bucket configuration with best practices
- **Compute**: EC2 instance provisioning with proper networking

## Learning Resources

- [Terraform AWS Provider Documentation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [Terraform Documentation](https://www.terraform.io/docs/)
- [AWS Documentation](https://docs.aws.amazon.com/)
- [Terraform Best Practices](https://www.terraform.io/docs/cloud/guides/recommended-practices/)

## Official Provider Repository

This project uses the official HashiCorp AWS Provider:

- GitHub Repository: [hashicorp/terraform-provider-aws](https://github.com/hashicorp/terraform-provider-aws)
- Terraform Registry: [AWS provider](https://registry.terraform.io/providers/hashicorp/aws/latest)

## Contributing

Feel free to submit issues and enhancement requests! Contributions are welcome.

## License

This project is provided as-is for educational purposes.

## Additional Examples

For more advanced examples and use cases, check out:

- [Terraform AWS Provider Examples](https://github.com/hashicorp/terraform-provider-aws/tree/main/examples)
- [AWS Infrastructure with Terraform](https://learn.hashicorp.com/tutorials/terraform/aws-build)
