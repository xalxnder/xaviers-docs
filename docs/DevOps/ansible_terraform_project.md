# Dev Ops Project

Objective:
We will be deploying Grafana and Prometheus to EC2 instances using  Terraform, Ansible, and Jenkins

## The Terraform Part

### Lifecycle Policies
Lets say we want to change our VPC cidr block from "10.123.0.0/16" to "10.124.0.0/16". If we try to apply this, it will fail. But why? Because, to update the cidr block, our VPC resource has to be destroyed and then created. In this process our internet gateway wont have anything to connect to because the VPC was destroyed. To get arouund this, we can add a lifecycle policy. 

```hcl
resource "aws_vpc" "architech_vpc" {
  cidr_block           = var.vpc_cidr
  enable_dns_hostnames = true
  enable_dns_support   = true

  tags = {
    Name = "architech_vpc-${random_id.random.dec}"
  }

  lifecycle {
    create_before_destroy = true
  }

}

```

The `create_before_destroy` does just that. It creates the new VPC first, so that the internet gateway has something to connect to prior to destroying. 🎉
#### Connect to AWS

I'm connected to AWS via VS code, using a profile I created called `default`.

## The Ansible Part

## Introducing Jenkins