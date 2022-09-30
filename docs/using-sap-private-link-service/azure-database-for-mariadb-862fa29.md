<!-- loio862fa2958c574c3cbfa12a927ce1d5fe -->

# Azure Database for MariaDB

Consume Azure Database for MariaDB with SAP Private Link service.



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_brl_k14_nrb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:



<a name="loio862fa2958c574c3cbfa12a927ce1d5fe__section_z2j_l14_nrb"/>

## Parameters


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

## Binding Credentials

The following binding credentials are provided:

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

