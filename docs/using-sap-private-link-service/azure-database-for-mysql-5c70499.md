<!-- loio5c70499ee70b415d954145a795e43355 -->

# Azure Database for MySQL

Consume Azure Database for MySQL with SAP Private Link service.



<a name="loio5c70499ee70b415d954145a795e43355__section_pxv_fb4_nrb"/>

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

## Binding Credentials

The following binding credentials are provided:

****


<table>
<tr>
<td valign="top">

*hostname*



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



<a name="loio5c70499ee70b415d954145a795e43355__section_okw_dtx_svb"/>

## Sample Applications

There is no custom configuration needed to connect to the MySQL server via SAP Private Link.

Just use a MySQL client library of your choice and configure it to use the hostname from the service binding \(and of course, username, password and any other settings\).



<a name="loio5c70499ee70b415d954145a795e43355__section_wn1_gtx_svb"/>

## Tutorials

Martin Pankraz published a blog post outlining the steps how set up a MySQL server and consume it via SAP Private Link:

[SAP private linky swear with Azure – connecting to PaaS DBs with SAP Private Link Service](https://blogs.sap.com/2022/01/12/btp-private-linky-swear-with-azure-connecting-to-cheap-paas-dbs-with-private-link-service/)

