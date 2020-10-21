# infrastructure.azure.observability.tracing

The `infrastructure.azure.observability.tracing` repository stores the resource configuration files for
[Terraform](https://www.terraform.io/) to deploy a
[resource group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview#terminology) containing a distributed tracing cluster to an Azure subscription. The resources created by the configuration in this repository are expected to be connected to a [Spoke network](https://github.com/Calvinverse/infrastructure.azure.network.spoke).

## Use

In order to run the Terraform configuration in this repository you need to have an Azure subscription and be [connected to that subscription](https://www.terraform.io/docs/providers/azurerm/index.html).

Once you are signed in run the Terraform [plan](https://www.terraform.io/docs/commands/plan.html) command to preview the changes that will be made.

    tf plan -var subscription_production=<SUBSCRIPTION_ID> -var subscription_test=<SUBSCRIPTION_ID> -var meta_source=<GIT_COMMIT_HASH> -var meta_version=<VERSION> -var consul_cert_path=<LOCAL_MACHINE_PATH_TO_CERT_DIR> -var encrypt_consul=<CONSUL_ENCRYPT_KEY> -out ./build/tf/plan

When you are happy with the plan execute the plan with the Terraform [apply](https://www.terraform.io/docs/commands/apply.html) command.

    tf apply ./build/tf/plan

