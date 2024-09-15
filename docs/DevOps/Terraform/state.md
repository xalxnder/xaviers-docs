# State
Terraform must store state about your managed infrastructure and configuration. This state is used by Terraform to map real world resources to your configuration, keep track of metadata, and to improve performance for large infrastructures.

This state is stored by default in a local file named "terraform.tfstate", but we recommend [storing it in Terraform Cloud](https://developer.hashicorp.com/terraform/cloud-docs/migrate) to version, encrypt, and securely share it with your team.

Terraform uses state to determine which changes to make to your infrastructure. Prior to any operation, Terraform does a [refresh](https://developer.hashicorp.com/terraform/cli/commands/refresh) to update the state with the real infrastructure.

**The primary purpose of Terraform state is to store bindings between objects in a remote system and resource instances declared in your configuration. When Terraform creates a remote object in response to a change of configuration, it will record the identity of that remote object against a particular resource instance, and then potentially update or delete that object in response to future configuration changes.**