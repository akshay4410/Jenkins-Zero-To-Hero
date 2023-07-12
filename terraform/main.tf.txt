terraform {
required_providers {
        aws = {
        source  = "hashicorp/aws"
        version = "~> 4.16"
}
}
        required_version = ">= 1.2.0"
}

provider "aws" {
region = "us-east-2"
}

locals {
	instances = {"Tilu":"0430580de6244e02e"}
}

resource "aws_instance" "aws_ec2_test" {
        for_each = local.instances
        ami = each.value
        instance_type = "t2.micro"
        tags = {
     Name = each.key
  }
}
