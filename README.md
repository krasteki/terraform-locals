# Learn Terraform locals

Terraform locals allow you to simplify your Terraform configuration and avoid
repetition. Local values can also help you write more readable configuration by
using meaningful names rather than hard-coding values. Follow along with [this
tutorial](https://learn.hashicorp.com/tutorials/terraform/locals?in=terraform/configuration-language) on HashiCorp Learn.


This repository is using Terraform to deploy a web application on AWS. The infrastructure includes a VPC, load balancer, and EC2 instances. `Local values` will be reduce repetition in the configuration. The combination of local values with input values will help to use a minimal set of resource tags.

# Prerequisites

- The [Terraform CLI](https://learn.hashicorp.com/tutorials/terraform/install-cli), version used 1.1.7
- AWS Credentials [configured for use with Terraform](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#authentication).
- The [git CLI](https://git-scm.com/downloads).

*** Note: Some of the infrastructure in this tutorial may not qualify for the AWS free tier. Destroy the infrastructure at the end of the guide to avoid unnecessary charges. We are not responsible for any charges that you incur.


I. Create Infrastructure
Clone the repo
```
$ git clone https://github.com/krasteki/terraform-locals.git
$ cd terraform-locals
```

Initialize and apply this configuration.
```
$ terraform init
$ terraform apply
```