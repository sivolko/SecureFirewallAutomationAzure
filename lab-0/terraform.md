---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 👨‍💻 Terraform

## Stages of Terraform&#x20;

| stage             | Description                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------- |
| terraform init    | Initialize the Terraform code by installing all required providers in the working directory |
| terraform plan    | Plan the changes, based on the current state and the Terraform code                         |
| terraform apply   | Apply the plan                                                                              |
| terraform destroy | Destroy all the resources that were created by Terraform                                    |

## Terraform code to create VNET

```hcl
// main.tf

terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = ">= 3.62.1"
    }
  }
}

provider "azurerm" {
  features {}
  subscription "<your_azure_subscription_id_not recommended for production store locally>"
}

resource "azurerm_virtual_network" "myVirtualNetwork" {
  name                = "myVirtualNetwork"
  resource_group_name = "<yourResourceGroupName>"
  location            = "<yourResourceGroupLocation>"
  address_space       = ["10.1.0.0/16"]
}
```

* Terraform using **azurerm** to create services inside the Azure&#x20;
* Replace resource\_group\_name = "" with yours from Azure , if you don't have Resource Group then create a new&#x20;
*

