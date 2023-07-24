<!-- loio8064b46e99d140d8b38c1ac7f12aa513 -->

# Azure Automation

Consume Azure Automation with SAP Private Link service.



<a name="loio8064b46e99d140d8b38c1ac7f12aa513__section_exv_hts_x5b"/>

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

Identifies the subresource on Azure the private link should be created for. Must be one of `DSCAndHybridWorker` or `Webhook`. See the [official documentation](https://learn.microsoft.com/en-us/azure/automation/how-to/private-link-security) for a description of the endpoints.



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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Automation/automationAccounts/myAutomationAccount",
>     "subResource": "DSCAndHybridWorker",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio8064b46e99d140d8b38c1ac7f12aa513__section_xvy_f5s_x5b"/>

## Binding Credentials

**Webhook Subresource**

The following binding credentials are provided:


<table>
<tr>
<td valign="top">

*hostname*



</td>
<td valign="top">

Private DNS entry to connect to the Azure resource. This DNS entry resolves to the internal IP address associated with this private link.



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
>                 "hostname": "00000000-0000-0000-0000-000000000000.webhook.dewc.azure-automation.net"
>             }
>         }
>     ]
> }
> ```

**DSCAndHybridWorker Subresource** 

The following binding credentials are provided:


<table>
<tr>
<td valign="top">

*agentSvcHostname*



</td>
<td valign="top">

Private DNS entry to connect to the AgentSvc endpoint of the Azure resource.



</td>
</tr>
<tr>
<td valign="top">

*jrdsHostname*



</td>
<td valign="top">

Private DNS entry to connect to the JRDS endpoint of the Azure resource.



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
>                 "agentSvcHostname": "00000000-0000-0000-0000-000000000000.agentsvc.dewc.azure-automation.net",
>                 "jrdsHostname": "00000000-0000-0000-0000-000000000000.jrds.dewc.azure-automation.net"
>             }
>         }
>     ]
> }
> ```



<a name="loio8064b46e99d140d8b38c1ac7f12aa513__section_szq_kvs_x5b"/>

## Known Limitations

-   The Azure API to create Private Endpoints to Azure Automation silently ignores the `requestMessage` field and always displays "Please approve my connection" when listing connection requests. The SAP Private Link service does not have a workaround for this issue.



<a name="loio8064b46e99d140d8b38c1ac7f12aa513__section_kjk_5lx_svb"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure Automation Account via Private Link.

You can follow any tutorial using the Azure SDK for the language of your choice.

