<!-- loio570ee0d48743474abd98609b77e5effe -->

# Azure Form Recognizer

Consume Azure Form Recognizer with SAP Private Link service



<a name="loio570ee0d48743474abd98609b77e5effe__section_tz4_dyp_5wb"/>

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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.CognitiveServices/accounts/my-fr-account",
>     "subResource": "account",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio570ee0d48743474abd98609b77e5effe__section_m2k_5yp_5wb"/>

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
>                 "hostname": "my-fr-account.cognitiveservices.azure.com"
>             }
>         }
>     ]
> }
> ```



<a name="loio570ee0d48743474abd98609b77e5effe__section_gfb_zmk_xwb"/>

## Further Information

The standalone Azure Form Recognizer requires an [additional setup](https://learn.microsoft.com/en-us/azure/applied-ai-services/form-recognizer/managed-identities-secured-access?view=form-recog-3.0.0) to work with Private Link.

