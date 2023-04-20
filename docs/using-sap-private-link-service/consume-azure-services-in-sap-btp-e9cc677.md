<!-- loioe9cc67716a3a41c9885862661e6c4234 -->

# Consume Azure Services in SAP BTP

SAP Private Link service establishes a private connection between selected SAP BTP services and selected services in your own Microsoft Azure subscriptions.



<a name="loioe9cc67716a3a41c9885862661e6c4234__section_mpr_tmz_cpb"/>

## Overview

To privately access a service in your Azure subcription, SAP Private Link service creates a private endpoint and reuses the private link functionality of Azure:

 ![Consuming Azure services in SAP BTP.](images/Private_Link_-_Scenario_1_0745a1a.png) 



<a name="loioe9cc67716a3a41c9885862661e6c4234__section_sll_bjz_cpb"/>

## Prerequisites

-   See [Initial Setup](../initial-setup-f2dce1d.md).

-   You have created a Microsoft Azure service in the Azure Portal.




<a name="loioe9cc67716a3a41c9885862661e6c4234__section_slk_1jz_cpb"/>

## Supported Services

The following Azure services can currently be consumed from SAP BTP:

-   [Azure Private Link Service \(generic LB scenario for VMs and others\)](azure-private-link-service-generic-lb-scenario-for-vms-and-others-e8bc0c6.md)

-   [Azure Database for MariaDB](azure-database-for-mariadb-862fa29.md)

-   [Azure Database for MySQL](azure-database-for-mysql-5c70499.md)

-   [Azure Storage Account](azure-storage-account-75b307e.md)

-   [Azure Key Vault](azure-key-vault-407fb19.md)

-   [Azure CosmosDB](azure-cosmos-db-663ed56.md)

-   [Azure App Service or Azure Functions](azure-app-service-or-azure-functions-d5f96f9.md)

-   [Azure Application Gateway \(Beta\)](azure-application-gateway-beta-af86a45.md)

-   [Azure Automation](azure-automation-8064b46.md)

-   [Azure Machine Learning](azure-machine-learning-3421f1f.md)

-   [Azure Cognitive Services](azure-cognitive-services-3c1a30b.md)
-   [Azure Form Recognizer](azure-form-recognizer-570ee0d.md)


> ### Note:  
> If you would like to use a service or scenario with SAP Private Link service that is not available yet, please open a support ticket on BC-CP-PRIVATELINK.

> ### Restriction:  
> Mixing public and private endpoints for Azure resources in your Azure subscription when connected via SAP BTP using SAP Private Link, is not supported at this point.
> 
> Possible solutions to address such requirements are:
> 
> -   Use only private endpoints and add SAP Private Link service to your SAP BTP implementation.
> 
> -   Enable a mixed setup of private public access to the storage account via SAP BTP in parallel using Azure Application Gateway.
> 
> -   Use virtual hostname in the SAP Cloud Connector pointing to the internal IP of our azure native service.
> 
> -   Remove the private endpoint on Azure and consume publicly.



<a name="loioe9cc67716a3a41c9885862661e6c4234__section_zg3_cjz_cpb"/>

## Tutorial

To learn how to connect the SAP Private Link service to Microsoft Azure, see [Connect SAP Private Link Service to Microsoft Azure Private Link Service with Cloud Foundry CLI](https://developers.sap.com/tutorials/private-link-microsoft-azure.html).

-   **[Azure Private Link Service \(generic LB scenario for VMs and others\)](azure-private-link-service-generic-lb-scenario-for-vms-and-others-e8bc0c6.md "Consume Azure Private Link service with SAP Private Link service . ")**  
Consume Azure Private Link service with SAP Private Link service.
-   **[Azure Database for MariaDB](azure-database-for-mariadb-862fa29.md "Consume Azure Database for MariaDB with SAP Private Link service . ")**  
Consume Azure Database for MariaDB with SAP Private Link service.
-   **[Azure Database for MySQL](azure-database-for-mysql-5c70499.md "Consume Azure Database for MySQL with SAP Private Link service . ")**  
Consume Azure Database for MySQL with SAP Private Link service.
-   **[Azure Storage Account](azure-storage-account-75b307e.md "Consume Azure Storage Account with SAP Private Link service . ")**  
Consume Azure Storage Account with SAP Private Link service.
-   **[Azure Key Vault](azure-key-vault-407fb19.md "Consume Azure KeyVault and Azure Keyvault ManagedHSM with SAP Private Link
			service.")**  
Consume Azure KeyVault and Azure Keyvault ManagedHSM with SAP Private Link service.
-   **[Azure Cosmos DB](azure-cosmos-db-663ed56.md "Consume Cosmos DB with SAP Private Link service.")**  
Consume Cosmos DB with SAP Private Link service.
-   **[Azure App Service or Azure Functions](azure-app-service-or-azure-functions-d5f96f9.md "Consume Azure App Service or Azure Functions with SAP Private Link
			service.")**  
Consume Azure App Service or Azure Functions with SAP Private Link service.
-   **[Azure Application Gateway \(Beta\)](azure-application-gateway-beta-af86a45.md "Consume Azure Application Gateway with SAP Private Link service. ")**  
Consume Azure Application Gateway with SAP Private Link service.
-   **[Azure Automation](azure-automation-8064b46.md "Consume Azure Automation with SAP Private Link service.")**  
Consume Azure Automation with SAP Private Link service.
-   **[Azure Machine Learning](azure-machine-learning-3421f1f.md "Consume Azure Machine Learning with SAP Private Link service.")**  
Consume Azure Machine Learning with SAP Private Link service.
-   **[Azure Cognitive Services](azure-cognitive-services-3c1a30b.md "Consume Azure Cognitive Services with SAP Private Link service.")**  
Consume Azure Cognitive Services with SAP Private Link service.
-   **[Azure Form Recognizer](azure-form-recognizer-570ee0d.md "Consume Azure Form Recognizer with SAP Private Link service")**  
Consume Azure Form Recognizer with SAP Private Link service

