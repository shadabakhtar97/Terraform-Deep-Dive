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
