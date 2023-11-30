<!-- loio7056d9b66cb149c3a6dc97d9a503e5c8 -->

# Azure OpenAI

Consume Azure OpenAI with SAP Private Link service.



<a name="loio7056d9b66cb149c3a6dc97d9a503e5c8__section_zzt_m3f_mxb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:

****


<table>
<tr>
<td valign="top">

**resourceId** \(required\)

</td>
<td valign="top">

Identifies the resource on Azure the private link should be created for.

</td>
</tr>
<tr>
<td valign="top">

**subResource** \(required\)

</td>
<td valign="top">

Identifies the subresource on Azure the private link should be created for.

</td>
</tr>
<tr>
<td valign="top">

**requestMessage** \(optional\)

</td>
<td valign="top">

Specifies a message which is shown for the approval request on Azure for the specified resource.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.CognitiveServices/accounts/my-openai-account",
>     "subResource": "account",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio7056d9b66cb149c3a6dc97d9a503e5c8__section_mxg_bjf_mxb"/>

## Binding Credentials

The following binding credentials are provided:


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
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "my-openai-account.openai.azure.com"
>             }
>         }
>     ]
> }
> ```



<a name="loio7056d9b66cb149c3a6dc97d9a503e5c8__section_czz_gjf_mxb"/>

## Sample Application

There is no custom configuration needed for your application to consume Azure OpenAI via Private Link.

You can follow any tutorial using the Azure SDK for the language of your choice.

