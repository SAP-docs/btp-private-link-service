<!-- loio40d338b015114f26b923b5a948fe6b7c -->

# Azure Cosmos DB for PostgreSQL

Consume Azure Cosmos DB for PostgreSQL with SAP Private Link service.



<a name="loio40d338b015114f26b923b5a948fe6b7c__section_pgs_lqg_4yb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:

****


<table>
<tr>
<td valign="top">

**resourceId**

</td>
<td valign="top">

Identifies the resource on Azure the private link should be created for.

</td>
</tr>
<tr>
<td valign="top">

**subResource**

</td>
<td valign="top">

Identifies the subresource on Azure the private link should be created for. Must be either `coordinator` or `worker-<num>` to create a Private Link service instance for a specific worker node.

</td>
</tr>
<tr>
<td valign="top">

**requestMessage**

</td>
<td valign="top">

Specifies a message which is shown for the approval request on Azure for the specified resource.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> {
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/my-cosmos-db",
>     "subResource": "coordinator",
>     "requestMessage": "Please approve connection"
> }
> 
> ```



<a name="loio40d338b015114f26b923b5a948fe6b7c__section_vlg_yqg_4yb"/>

## Binding Credentials

The following binding credentials are provided:

****


<table>
<tr>
<td valign="top">

**hostname**

</td>
<td valign="top">

DNS entry to connect to the Azure resource. This DNS entry resolves to the internal IP address associated with this private link.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "c-my-cosmos-db.00000000000000.postgres.cosmos.azure.com"
>             }
>         }
>     ]
> }
> 
> ```



<a name="loio40d338b015114f26b923b5a948fe6b7c__section_eyn_drg_4yb"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure CosmosDB for PostgreSQL via Private Link.

You can follow any tutorial using a suitable client library for the language of your choice.

