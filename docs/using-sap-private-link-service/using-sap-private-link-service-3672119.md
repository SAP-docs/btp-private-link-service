<!-- loio3672119271fe4b319eaf3624870044b0 -->

# Using SAP Private Link Service

SAP Private Link service lets you consume selected Azure native services of your Azure subscription in SAP BTP.



<a name="loio3672119271fe4b319eaf3624870044b0__section_asm_51b_hdc"/>

## Announcement



<a name="loio3672119271fe4b319eaf3624870044b0__section_evm_pzg_hdc"/>

## SAP Private link service keys will no longer contain the hostname of the connected resource, but instead the private IP address

In order to remove the restrictions in [Consume Azure Services in SAP BTP](consume-azure-services-in-sap-btp-e9cc677.md), preventing customers to mix public and private endpoints for Azure resources in their Azure subscription when connected via SAP BTP using SAP Private Link, we plan to delete the SAP private link service managed Private DNS zones attached to the BTP Cloud Foundry regions.

The following changes are to be expected:

-   SAP Private link service keys will no longer contain the hostname of the connected resource, but instead the private IP address. Due date is **January 2025**.

-   SAP managed Private DNS Zones to Azure native services will be deleted from the BTP Cloud Foundry regions. Due date is **March 31, 2025**.



<a name="loio3672119271fe4b319eaf3624870044b0__section_fvm_pzg_hdc"/>

## SAP managed Private DNS Zones to Azure native services will be deleted from the BTP Cloud Foundry regions

Service keys credentials will no longer contain the hostname but only the private IP address of the provisioned private endpoint. This information can be used for testing the connection. If you want to consume the linked Azure/AWS resource over TLS \(thus using its private hostname\) you'll need to create a service binding to the consuming application and get the hostname information from the binding credentials. This would affect only service keys created after January 2025.



As result DNS resolution of hostnames provisioned by SAP private link service will work in BTP Cloud Foundry environment only if the SAP private link service instance is bound to the consuming application. In order to prevent disruptions in your private link connectivity please check the **applicability criteria** to evaluate if you're affected, and if yes, make sure to go through the **Actions to take before March 31, 2025**.



<a name="loio3672119271fe4b319eaf3624870044b0__section_u4q_5zg_hdc"/>

## Applicability Criteria:



-   You have created instances of SAP Private link service in your SAP BTP cockpit accounts.
-   You use the SAP private link service instance to connect to one of the native services in [Consume Azure Services in SAP BTP](consume-azure-services-in-sap-btp-e9cc677.md), except for [Azure Private Link Service \(generic LB scenario for VMs and others\)](azure-private-link-service-generic-lb-scenario-for-vms-and-others-e8bc0c6.md).
-   You **have** created service keys in your SAP private link service instances **before January 2025**.
-   You**have not** created service bindings to consuming applications in your SAP Private link service instances.



<a name="loio3672119271fe4b319eaf3624870044b0__section_mkf_wzg_hdc"/>

## Actions to take:



-   Bind the SAP Private link service instances to the consuming applications.


-   **[Consume Azure Services in SAP BTP](consume-azure-services-in-sap-btp-e9cc677.md "SAP Private Link service  establishes
		a private connection between selected SAP BTP services and selected
		services in your own Microsoft Azure subscriptions.")**  
SAP Private Link service establishes a private connection between selected SAP BTP services and selected services in your own Microsoft Azure subscriptions.
-   **[Consume Amazon Web Services in SAP BTP](consume-amazon-web-services-in-sap-btp-5753419.md "SAP Private Link service establishes a private connection between
		selected SAP BTP services and selected services in your own Amazon Web Service  (AWS)
		accounts.")**  
SAP Private Link service establishes a private connection between selected SAP BTP services and selected services in your own Amazon Web Service \(AWS\) accounts.

