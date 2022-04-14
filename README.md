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

II. Use locals to name resources

In the configuration's `main.tf` file, several of the resources have `name` arguments created by interpolating the `project` and `environment` values from the `resource_tags` variable with another value that describes the resource. Reduce duplication and make this configuration clearer by setting the shared part of each `name` as a local value to re-use across your configuration. Define the local `name_suffix`
Update the `name` attributes in the configuration to use this new local value.

III. Combine variables with local values
Unlike variable values, local values can use dynamic expressions and resource arguments. The `resource_tags` map in `variables.tf` defines the tags for the local `name_suffix` as defaults
- Add new variable definitions to `variables.tf`
- Add new locals block to `main.tf` to create a map combining both required tags and user defined tags.
- Update the definition of the `name_suffix` local to use the new variables for `project_name` and `environment`.
- Update the five references to tags in `main.tf` to use the new local value.
- Add an output named `tags` to the `output.tf`. This value should be a combination of var.resource_tags and local.required_tags.

IV. Destroy the infrastructure
```
$ terraform destroy
```
Confirm with yes.
