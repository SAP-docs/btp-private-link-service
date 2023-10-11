<!-- loioc9be70f6e4814a6db31e54ae29d21c1d -->

# Error Messages on Azure




<table>
<tr>
<th valign="top">

Error Message



</th>
<th valign="top">

More Information



</th>
</tr>
<tr>
<td valign="top">

ResourceId: resourceId is a required field



</td>
<td valign="top">

Specify your valid input parameters. See [Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/tutorials/private-link-onboarding/tutorials/private-link-microsoft-azure.html).



</td>
</tr>
<tr>
<td valign="top">

The resource ID you specified is incorrect. Provide the correct Microsoft Azure resource ID to establish a connection, for example '/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/ providers/Microsoft.DBforPostgreSQL/servers/myServer'.



</td>
<td valign="top">

See [Tutorial: Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/tutorials/private-link-microsoft-azure.html).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Subscription <invalid-subscription-id\> of remote resource /subscriptions/<invalid-subscription-id\>/resourceGroups/westcentralus-test/providers/Microsoft.Network/privateLinkServices/westcentralus is not registered with Microsoft.Network resource provider.



</td>
<td valign="top">

The subscription ID that is part of your resource ID is incorrect. Provide the correct Microsoft Azure resource ID to establish a connection, for example '/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/ providers/Microsoft.DBforPostgreSQL/servers/myServer'. See [Tutorial: Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/tutorials/private-link-microsoft-azure.html).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Provider Microsoft.DBforPostgreSQL/flexibleServers do not support private endpoint



</td>
<td valign="top" rowspan="2">

The service you want to connect to does not support private endpoints. For an overview of supported services, see [Consume Azure Services in SAP BTP](using-sap-private-link-service/consume-azure-services-in-sap-btp-e9cc677.md).



</td>
</tr>
<tr>
<td valign="top">

SAP Private Link service currently does not support this Azure service. Please contact your customer representative if you would like to see it supported in the future.



</td>
</tr>
<tr>
<td valign="top">

subResource <name\> does not exist for resource type Microsoft.DBforMySQL/servers, only valid value: mysqlServer

subResource <name\> does not exist for resource type Microsoft.DBForMariaDB/servers, only valid value: mariadbServer



</td>
<td valign="top">

The subResource you requested for your resourceID is invalid. For an overview of supported services, see [Consume Azure Services in SAP BTP](using-sap-private-link-service/consume-azure-services-in-sap-btp-e9cc677.md).



</td>
</tr>
<tr>
<td valign="top">

Your current instance count of <number\> exceeds your allowed quota of <number\>. To create a new service instance, please increase your quota.



</td>
<td valign="top">

See [Managing Entitlements and Quotas Using the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/c8248745dde24afb91479361de336111.html?locale=en-US).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Call to Microsoft.DBforMySQL/servers failed. Error message: Private endpoint is not supported for Basic Servers

Microsoft Azure reported the following message: Call to Microsoft.DBforMariaDB/servers failed. Error message: Private endpoint is not supported for Basic Servers



</td>
<td valign="top">

The private endpoint doesn't support the tier of the backing service. To create a private link to a MySQL/MariaDB, you need a higher tier. See [Storage account overview](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Call to Microsoft.Storage/storageAccounts failed. Error message: The operation is not allowed on account kind Storage.



</td>
<td valign="top">

Creating private endpoints is not supported for this storage account type. Upgrade to a newer storage account type on Microsoft Azure first. See [Storage account overview](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Call to Microsoft.Storage/storageAccounts failed. Error message: Values for request parameters are invalid: GroupId: blob\_secondary.



</td>
<td valign="top">

Creating private endpoints for a storage account without secondary endpoints is not supported. For more information, see [Storage account overview](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-overview).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Call to Microsoft.Storage/storageAccounts failed. Error message: The scope '/subscriptions/...' cannot perform write operation because following scope\(s\) are locked: '/subscriptions/.../Microsoft.Storage/storageAccounts/plsintegrtestdreadlocked'. Please remove the lock and try again.



</td>
<td valign="top">

The Azure resource you want to create a private link for is locked. Remove the ReadOnly lock and try again.



</td>
</tr>
<tr>
<td valign="top">

An error occurred while creating the private endpoint. Please check your input parameters and try again.



</td>
<td valign="top" rowspan="5">

See [Tutorial: Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/tutorials/private-link-microsoft-azure.html).



</td>
</tr>
<tr>
<td valign="top">

Private endpoint wasn’t approved within 24 hours. Please create a new Private Link service.



</td>
</tr>
<tr>
<td valign="top">

Connection for private endpoint 'sap-privatelink-<GUID\>' rejected with the following message: <rejection-message-from-user\>. Initiate a new connection by creating a new Private Link service instance.



</td>
</tr>
<tr>
<td valign="top">

Connection for private endpoint 'sap-privatelink-<GUID\>' removed by the Azure resource owner. Initiate a new private endpoint connection by creating a new Private Link service instance.



</td>
</tr>
<tr>
<td valign="top">

The private endpoint <private endpoint\> has been deleted on Microsoft Azure. Initiate a new private endpoint connection by creating a new Private Link service instance.



</td>
</tr>
<tr>
<td valign="top">

Private endpoint for Azure resource 'my-mysql-service' already exists in this SAP BTP Cloud Foundry region. To allow others access to the private endpoint, share the service instances to another space.



</td>
<td valign="top">

See [Sharing Service Instances](https://docs.cloudfoundry.org/devguide/services/sharing-instances.html).



</td>
</tr>
<tr>
<td valign="top">

The private endpoint cannot be deleted because its Azure resource, parent resource group, or subscription has a lock that prevents deletion. Temporarily remove the lock to allow the deletion of the private endpoint.



</td>
<td valign="top">

See [Lock resources to prevent unexpected changes.](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources?tabs=json)



</td>
</tr>
<tr>
<td valign="top">

Bindings can only be created for private endpoints in status 'succeeded'. Current status is 'failed'.



</td>
<td valign="top">

Please recreate the service instance and try again. For more information, see [Tutorial: Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/tutorials/private-link-microsoft-azure.html).



</td>
</tr>
<tr>
<td valign="top">

No CosmosDB regions specified, please specify all regions your CosmosDB instance is replicated to in the creation parameters.



</td>
<td valign="top">

You are creating a private link to an Azure CosmosDB and did not specify its regions. Creating such a private link requires the CosmosDB regions to be explicitly specified.Please specify all regions during creation, see [Azure Cosmos DB](using-sap-private-link-service/azure-cosmos-db-663ed56.md).



</td>
</tr>
<tr>
<td valign="top">

CosmosDB replication region 'invalidregion' unknown.



</td>
<td valign="top">

You are creating a private link to an Azure CosmosDB and specified an invalid region. The SAP Private Link service will validate all region names against a static list.

Please specify only valid regions during creation. See [Azure Cosmos DB](using-sap-private-link-service/azure-cosmos-db-663ed56.md).



</td>
</tr>
<tr>
<td valign="top">

CosmosDB replication region "eastus2" has been specified multiple times. Please specify every region the CosmosDB is geo-replicated to only once.



</td>
<td valign="top">

You are creating a private link to an Azure CosmosDB and specified a region multiple times.

Please specify each region only once, see [Azure Cosmos DB](using-sap-private-link-service/azure-cosmos-db-663ed56.md).



</td>
</tr>
<tr>
<td valign="top">

CosmosDB requires all configured regions to be explicitly specified in the creation parameters. At last one region is missing from the creation parameters.



</td>
<td valign="top">

You are creating a private link to an Azure CosmosDB and specified some regions, but at least one is missing.

Please specify all regions of the CosmosDB, see [Azure Cosmos DB](using-sap-private-link-service/azure-cosmos-db-663ed56.md).



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Call to Microsoft.Web/sites failed. Error message: SkuCode 'Free' is invalid.



</td>
<td valign="top">

You specified an Application/Function that runs on a tier that does not support private endpoints.

Consult the [Azure documentation](https://docs.microsoft.com/en-us/azure/app-service/networking/private-endpoint) to see which tier supports private endpoints.



</td>
</tr>
<tr>
<td valign="top">

Application Gateway does not support PrivateLink on V1 SKUs. Please switch to one of the V2 SKUs.



</td>
<td valign="top">

The Application Gateway only works with the `V2` SKUs. Please switch to one of the `V2` SKUs.



</td>
</tr>
<tr>
<td valign="top">

Application Gateway does not have a Private link configuration with a Frontend IP configuration with the given name set or the required feature is not registered in target subscription. Please configure a Private link configuration for the given Frontend IP Configuration in the target Application Gateway and register the feature "Microsoft.Network/AllowApplicationGatewayPrivateLink" in the target subscription. Make sure that the given subResource matches the name of the Frontend IP Configuration configured for the Private link configuration you want to connect to.



</td>
<td valign="top">

Using PrivateLink with an Azure Application Gateway requires the mentioned feature to be registered as well as a Private link configuration to be set. Please register the feature and [configure a Private link configuration](https://docs.microsoft.com/en-us/azure/application-gateway/private-link-configure) in the target.

Additionally, the name of the Frontend IP Configuration that has a Private link configuration assigned must be used as subResource, please make sure that the given subResource is a valid Frontend IP Configuration name that has a Private link configuration assigned.



</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure reported the following message: Call to Microsoft.DocumentDB/databaseAccounts failed. Error message: GroupId "groupID" is not supported.



</td>
<td valign="top">

You are trying to create a private endpoint for a subResource to a CosmosDB instance which is not supported. For example, the "CosmosDB for MongoDB" does only support subResource `MongoDB` \(and not the others\), "CosmosDB for Cassandra" only `Cassandra` etc.



</td>
</tr>
<tr>
<td valign="top">

Azure Speech service requires a custom domain name to be set to be used with Private Link. Please see [Use Speech service through a private endpoint](https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-services-private-link?tabs=portal).



</td>
<td valign="top">

Azure Speech service requires additional configuration to support private link connectivity. Please check the linked documentation.



</td>
</tr>
</table>

