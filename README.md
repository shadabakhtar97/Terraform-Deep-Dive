# Terraform Deep Dive

Terraform is an open-source infrastructure as code (IaC) tool developed by HashiCorp. It enables users to define and provision infrastructure in a declarative configuration language. Terraform allows you to create, modify, and version infrastructure efficiently and safely.

Here are some key concepts and features of Terraform:

1. **Declarative Syntax:** Terraform uses a declarative configuration language to define infrastructure. Users describe the desired state of their infrastructure, and Terraform takes care of provisioning and managing the resources to achieve that state.

2. **Providers:** Terraform supports various providers, which are plugins that allow it to interact with different infrastructure platforms and services. Examples of providers include AWS, Azure, Google Cloud Platform, and many others.

3. **Resources:** In Terraform, resources are the building blocks of infrastructure. They represent the components you want to create or manage, such as virtual machines, networks, or databases. Resources are declared in the Terraform configuration.

4. **Modules:** Modules in Terraform allow you to encapsulate and reuse configurations. They enable you to organize and modularize your infrastructure code, making it more maintainable and scalable.

5. **State Management:** Terraform keeps track of the current state of your infrastructure in a state file. This file is used to determine what changes need to be applied to achieve the desired state. State management is crucial for tracking changes and ensuring consistency.

6. **Plan and Apply:** Before making any changes to the infrastructure, Terraform generates an execution plan that outlines the actions it will take to move from the current state to the desired state. The plan is then applied to make the changes.

Here's a simple example of a Terraform configuration file:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

In this example, a configuration is defined to create an AWS EC2 instance in the specified region using a specific Amazon Machine Image (AMI) and instance type.

To use Terraform, you typically follow these steps:

1. Write the Terraform configuration.
2. Initialize the Terraform working directory using `terraform init`.
3. Create an execution plan using `terraform plan`.
4. Apply the changes using `terraform apply`.

Terraform simplifies the process of managing and provisioning infrastructure, making it easier to adopt infrastructure as code principles in your development and operations workflows.

### --------------------------------------------------------------------------------------------------------------------------

# Configure the AWS Provider
provider "aws" {
access_key = "*******************"
secret_key = "********************"
region = "us-west-1"
}

# Create EKS Cluster
 
module "eks" {
  source          = "terraform-aws-modules/eks/aws"

  cluster_version = "1.21"
  cluster_name    = "Sample"
  vpc_id          = "vpc-0d8ad7b2d3da80271"
  subnets         = ["subnet-055fa3665bb644a4d", "subnet-07c90e3d1835deeea"]

  worker_groups = [
    {
      instance_type = "m4.large"
      asg_max_size  = 5
    }
  ]
}

 Error: Post "http://localhost/api/v1/namespaces/kube-system/configmaps": dial tcp [::1]:80: connectex: No connection could be made because the target machine actively refused it.
│
│   with module.eks.kubernetes_config_map.aws_auth[0],
│   on .terraform\modules\eks\aws_auth.tf line 63, in resource "kubernetes_config_map" "aws_auth":   
│   63: resource "kubernetes_config_map" "aws_auth" {

# EKS with Terraform:
======================
# Prerequites
  # Need terraform.exe
  # Need Set environment variable for terraform.exe
  # Verify terraform
    terraform --version

  # Need AWS Account
  # Need AWSAccessKeyId and secret_key
  # Need AWS provider terraform script
  # Need AWS region name


    provider "aws" {
    access_key = "******************"
    secret_key = "*********************"
    region = "us-west-1"
    }
  ===================================================================================================================================================================
  # Private bucket with versioning enabled

module "s3_bucket" {

  source = "terraform-aws-modules/s3-bucket/aws"

  bucket = "my-s3-bucket"
  acl    = "private"

  versioning = {
    enabled = true
  }

}
===================================================================================================================================================================
# After configure Provider run command : terraform init

module "eks" {
  source          = "terraform-aws-modules/eks/aws"

  cluster_version = "1.21"
  cluster_name    = "Sample"
  vpc_id          = "vpc-03941b5564cb32cd4"
  subnets         = ["subnet-0c6a82b07df1314f5"]

  worker_groups = [
    {
      instance_type = "m4.large"
      asg_max_size  = 5
    }
  ]
}

    # After prepare scripts for ec2 instance run command: 
    D:\module1> terraform validate
    Success! The configuration is valid.

    # If Validation is success then run command: 
       D:\module1> terraform plan

    # Run terraform apply command to create ec2 instance
    D:\module1> terraform apply

