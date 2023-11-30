<!-- loio3c1a30b7fa704af0a14ff96cfb0a38a7 -->

# Azure Cognitive Services \(Azure AI Services\)

Consume Azure Cognitive Services \(Azure AI Services\) with SAP Private Link service.



<a name="loio3c1a30b7fa704af0a14ff96cfb0a38a7__section_tz4_dyp_5wb"/>

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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.CognitiveServices/accounts/my-cs-account",
>     "subResource": "account",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio3c1a30b7fa704af0a14ff96cfb0a38a7__section_m2k_5yp_5wb"/>

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
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "my-cs-account.cognitiveservices.azure.com"
>             }
>         }
>     ]
> }
> ```



<a name="loio3c1a30b7fa704af0a14ff96cfb0a38a7__section_e1p_zyp_5wb"/>

## Further Information

The standalone Azure Speech service requires an [additional setup](https://learn.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-services-private-link?tabs=portal) to work with Private Link.

