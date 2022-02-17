# Azure App Server Demo
## Overview
In this demo we will be showing some of the functionality of using Terraform to deploy and manage Azure Resources. In this demo we will be deploying an app server cluster in Azure. We will be first deploying the necessary Azure Storage resources to store our Terraform State for our app server deployment. We will be using the outputs from this deployment to create our backend configuration. Below are the instructions for this demo.

## Instructions:
 # Create an Azure Storage Account for use with Terraform for storing your state remotely:

 1) First (if using our ACG Azure Sandbox) you will need to import the resource group into Terraform.
     a) Initialize the `remote_state_storage` working directory.
     b) Use the Azure CLI to find your resource group and subscription ID.
     c) Use the `terraform import` command to import the resource group into Terraform.

 2) After import, uncomment the values in the `create-remote-state-storage.tf` file and add your resource group name and location to the resource group block of the configuration file.
   
 3) Deploy your resources with Terraform. The outputs from the apply will be used in the `backend.tf` configuration file in the `app_servers` project folder.

# Create an app server cluster  with Terraform:
1) First add the information from the outputs from the `create-remote-state-storage.tf` file to the `backend.tf` file in the `app_servers` project folder.

2) Next move over to the `app_servers` project folder and initialize the working directory.

3) Next import the resource group into Terraform (if you are using the ACG Azure Sandbox).

4) Add the resource group name and location to the resource group block of the `networking.tf` configuration file.

5) Next move to the `variables.tf` configuration file and replace the values for `<LOCATION>`, `<RESOURCE_GROUP>`, `<STORAGE_ACCOUNT_NAME>`, and `<CONTAINER_NAME>` with the proper values and save all files.

6) Next validate your configuration, do a dry-run to make sure it all checks out, and them apply your configuration.

7) Confirm that the app server cluster was created successfully.

8) Once satisfied, destroy your infrastructure with Terraform (Make sure if using the ACG Azure Sandbox that you remove the resource group from your state before the destroy).

## Good luck!