<!-- loio663ed5631cfd4ef0a4bd89ca00266943 -->

# Azure Cosmos DB

Consume Cosmos DB with SAP Private Link service.



<a name="loio663ed5631cfd4ef0a4bd89ca00266943__section_lcx_nhp_p5b"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*resourceId* \(required\)



</td>
<td valign="top">

Identifies the resource on Azure the private link should be created for.



</td>
</tr>
<tr>
<td valign="top">

*subResource* \(required\)



</td>
<td valign="top">

Identifies the sub-resource on Azure the private link should be created for. Must be one of `Sql`, `MongoDB`, `Cassandra`, `Gremlin` or `Table`. Consult the [Azure documentation](https://docs.microsoft.com/en-us/azure/cosmos-db/how-to-configure-private-endpoints#private-zone-name-mapping) to see which sub-resource is available for the Cosmos DB instance.



</td>
</tr>
<tr>
<td valign="top">

*cosmosDb.regions* \(required\)



</td>
<td valign="top">

A list of *all* regions the CosmosDB is running in. This information can be found under *Read Locations* and *Write Locations* in the overview of the CosmosDB in the Azure Portal. Must be in the region ID format which can be retrieved via `az account list-locations -o table`.



</td>
</tr>
<tr>
<td valign="top">

*requestMessage* \(optional\)



</td>
<td valign="top">

Specifies a message which is shown for the approval request on Azure for the specified resource.



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DocumentDB/databaseAccounts/myCosmosDB",
>     "subResource": "Sql",
>     "cosmosDb": {
>         "regions": ["germanywestcentral", "uksouth", "ukwest"]
>     },
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio663ed5631cfd4ef0a4bd89ca00266943__section_z1c_c3p_p5b"/>

## Binding Credentials

The following binding credentials are provided:

****


<table>
<tr>
<td valign="top">

*hostname*



</td>
<td valign="top">

DNS entry to connect to the global endpoint of the Cosmos DB. This DNS entry resolves to the internal IP address associated with this private link.



</td>
</tr>
<tr>
<td valign="top">

*regions*



</td>
<td valign="top">

Object containing DNS entries to connect to the regional endpoints of the Cosmos DB. The key of the object is the region ID, the value the FQDN of the regional Cosmos DB endpoint.



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "mycosmosdb.documents.azure.com",
>                 "regions": {
>                     "germanywestcentral": "mycosmosdb.documents.azure.com",
>                     "uksouth": "mycosmosdb-uksouth.documents.azure.com",
>                     "ukwest": "mycosmosdb-ukwest.documents.azure.com",
>                 }
>             }
>         }
>     ]
> }
> ```



<a name="loio663ed5631cfd4ef0a4bd89ca00266943__section_uxv_33p_p5b"/>

## Known Limitations

-   If a region is removed from the Cosmos DB with an existing private endpoint, the regional endpoint of this region will no longer work. However, the existing endpoints \(global and in other regions\) will continue to work.
-   If an additional region is added to a Cosmos DB, the endpoint for the new region will not automatically become available on the private endpoint. To make the endpoint of the additional region available, a new service instance must be created.



<a name="loio663ed5631cfd4ef0a4bd89ca00266943__section_n4f_bmx_svb"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure CosmosDB via Private Link.

You can follow any tutorial using a suitable client library for the language of your choice.



<a name="loio663ed5631cfd4ef0a4bd89ca00266943__section_nhj_rwj_gxb"/>

## Tutorials

Martin Pankraz published a blog post outlining the steps on how to set up a multi-region with emphasis on private connectivity to the distributed database Azure Cosmos DB from your SAP BTP apps: [SAP private linky swear with Azure – global scale with Azure Cosmos DB and SAP Private Link](https://blogs.sap.com/2023/01/27/sap-private-linky-swear-with-azure-global-scale-with-azure-cosmos-db-with-sap-private-link/)

