<!-- loio75b307e216e04d1eb93ba590c4474a53 -->

# Azure Storage Account

Consume Azure Storage Account with SAP Private Link service.



<a name="loio75b307e216e04d1eb93ba590c4474a53__section_lpf_fl4_rsb"/>

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

Currently supported values for Azure Storage Account are: `table`, `table_secondary`, `queue`, `queue_secondary`, `file`, `web`, `web_secondary`, `blob`, `blob_secondary`, `dfs` and `dfs_secondary`.

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
>     "resourceId": "/subscriptions/<subscription>/resourceGroups/<rg>/providers/Microsoft.Storage/storageAccounts/<my-storage-account>",
>     "subResource": "queue",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio75b307e216e04d1eb93ba590c4474a53__section_kpl_jyn_nrb"/>

## Binding Credentials

The following binding credentials are provided:


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
>                 "hostname": "myStorageAccount.queue.core.windows.net"
>             }
>         }
>     ]
> }
> ```



<a name="loio75b307e216e04d1eb93ba590c4474a53__section_ykl_l14_nrb"/>

## Further Information

> ### Note:  
> Storage Account kind *Storage \(general purpose v1\)* is not supported since it does not allow Private Endpoint creation.



<a name="loio75b307e216e04d1eb93ba590c4474a53__section_rm1_vvj_gxb"/>

## Tutorials

Harutyun Ter-Minasyan published a blog post outlining more use cases for SAP Private Link connectivity: [SAP Private Link service use cases for SAP Cloud Integration and SAP Build Work Zone, Standard Edition](https://blogs.sap.com/2022/08/22/sap-private-link-service-use-cases-for-sap-cloud-integration-and-sap-launchpad/)

