<!-- loio862fa2958c574c3cbfa12a927ce1d5fe -->

# Azure Database for MariaDB

Consume Azure Database for MariaDB with SAP Private Link service \(Beta\).



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_brl_k14_nrb"/>

## Request Reference

The following Cloud Foundry service specific configuration parameters are supported during a service instance creation:

> ### Sample Code:  
> ```
> 
> {
>     "resourceId": "/subscriptions/<subscription>/resourceGroups/<rg>/providers/Microsoft.DBForMariaDB/servers/<my-maria-db>",
>     "subResource": "mariadbServer",
>     "requestMessage": "request message"
> }
> 
> ```



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_z2j_l14_nrb"/>

## Parameters


<table>
<tr>
<td valign="top">

*resourceID* \(required\)



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

Identifies the subresource on Azure the private link should be created for.



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
> 
> {
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DBForMariaDB/servers/myMariaDB",
>     "subResource": "mariadbServer",
>     "requestMessage": "Please approve connection"
> }
> 
> ```



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_exj_l14_nrb"/>

## Binding Reference

The following binding credentials are provided:

> ### Sample Code:  
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "<private link hostname>", 
>             }
>         }
>     ]
> }
> 
> ```



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_kqk_l14_nrb"/>

## Credentials

-   *hostname*: DNS entry to connect to the Azure resource. This DNS entry resolves to the internal IP address associated with this private link.




> ### Sample Code:  
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "myMariaDB.mariadb.database.azure.com"
>             }
>         }
>     ]
> }
> 
> ```



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_ykl_l14_nrb"/>

## Further Information

> ### Note:  
> `Basic` version of MariaDB is not supported since it does not allow Private Endpoints creation. All supported versions can be found in the official [Azure Database for MariaDB documentation](https://docs.microsoft.com/en-us/azure/mariadb/concepts-limits#vnet-service-endpoints).

