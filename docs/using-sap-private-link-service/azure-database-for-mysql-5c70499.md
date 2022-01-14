<!-- loio5c70499ee70b415d954145a795e43355 -->

# Azure Database for MySQL

Consume Azure Database for MySQL with SAP Private Link service \(Beta\).



<a name="loio5c70499ee70b415d954145a795e43355__section_pxv_fb4_nrb"/>

## Request Reference

The following Cloud Foundry service specific configuration parameters are supported during a service instance creation:

> ### Sample Code:  
> ```
> 
> {
>     "resourceId": "/subscriptions/<subscription>/resourceGroups/<rg>/providers/Microsoft.DBforMySQL/servers/<my-mysql>",
>     "subResource": "mysqlServer",
>     "requestMessage": "request message"
> }
> 
> ```



<a name="loio5c70499ee70b415d954145a795e43355__section_uxk_gb4_nrb"/>

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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DBforMySQL/servers/myMySQL",
>     "subResource": "mysqlServer",
>     "requestMessage": "Please approve connection"
> }
> 
> ```



<a name="loio5c70499ee70b415d954145a795e43355__section_lql_gb4_nrb"/>

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



<a name="loio5c70499ee70b415d954145a795e43355__section_b3m_gb4_nrb"/>

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
>                 "hostname": "MySQL.mysql.database.azure.com"
>             }
>         }
>     ]
> }
> 
> ```



<a name="loio5c70499ee70b415d954145a795e43355__section_mln_gb4_nrb"/>

## Further Information

> ### Note:  
> `Basic` version of MySQL is not supported since it does not allow Private Endpoints creation. All supported versions can be found in the official [Azure Database for MySQL documentation](https://docs.microsoft.com/en-us/azure/mysql/concepts-limits#vnet-service-endpoints).

