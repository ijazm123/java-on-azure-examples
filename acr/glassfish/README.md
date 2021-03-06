
# Push a Glassfish Docker image

![acr/glassfish/README.md](https://github.com/Azure-Samples/java-on-azure-examples/workflows/acr/glassfish/README.md/badge.svg)

## Prerequisites

This example assumes you have previously completed the following examples.

1. [Create an Azure Resource Group](../../group/create/)
1. [Create an Azure Container Registry](../create/)

<!-- workflow.cron(0 4 * * 2) -->
<!-- workflow.include(../create/README.md) -->

## Build the WAR file

<!-- workflow.run()

cd acr/glassfish

  -->

To build the WAR file use the following command line:

```shell
  mvn package
```

## Build and push the Docker image to your Azure Container Registry

To build and push the Docker image to your ACR use the command line below:

```shell
  export ACR_GLASSFISH_IMAGE=glassfish:latest

  az acr build --registry $ACR --image $ACR_GLASSFISH_IMAGE .
```

<!-- workflow.run()

cd ../..

  -->

<!-- workflow.directOnly()

export RESULT=$(az acr repository show --name $ACR --image $ACR_GLASSFISH_IMAGE)
az group delete --name $RESOURCE_GROUP --yes || true

if [[ -z $RESULT ]]; then
  echo "Unable to find $ACR_GLASSFISH_IMAGE image"
  exit 1
fi

  -->

## Cleanup

Do NOT forget to remove the resources once you are done running the example.

3m
