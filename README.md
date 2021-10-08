# Shadab-Terraform

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

