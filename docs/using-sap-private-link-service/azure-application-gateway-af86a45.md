<!-- loioaf86a457ffd84324a6691c6ea1649dd6 -->

# Azure Application Gateway

Consume Azure Application Gateway with SAP Private Link service.



<a name="loioaf86a457ffd84324a6691c6ea1649dd6__section_npn_xpk_x5b"/>

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

Identifies the subresource on Azure the private link should be created for. This has to be the user-defined name of the <code><i>Frontend IP Configuration</i></code> of the <code><i>Private link configuration</i></code> the connection should be created for.



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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/applicationGateways/myAppGw",
>     "subResource": "myFrontendIPConfig",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loioaf86a457ffd84324a6691c6ea1649dd6__section_fqc_5qk_x5b"/>

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
<tr>
<td valign="top">

*additionalHostname* 



</td>
<td valign="top">

Additional private DNS entry to connect to the Azure resource.



</td>
</tr>
</table>

> ### Note:  
> Refer to the section **Transport Layer Security** at the end of this chapter for more details.

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "00000000-0000-0000-0000-000000000000.00000000000000000000000000000000000000000000000000000000.p1.pls.sap.internal",
>                 "additionalHostname": "00000000-0000-0000-0000-000000000000.p1.pls.sap.internal"
>             }
>         }
>     ]
> }
> ```



<a name="loioaf86a457ffd84324a6691c6ea1649dd6__section_qqt_crk_x5b"/>

## Transport Layer Security

Since the Azure Application Gateway doesn't provide its own PrivateLink DNS entries, the SAP Private Link service creates DNS names that can be used for proper TLS just like it does for connections to Azure Private Link services.

Please refer to the [documentation of the Private Link service](https://github.tools.sap/C5338252/btp-private-link-service/blob/dc41b9cd6024b8300c94d32a6b9baa1eaee84e1b/docs/using-sap-private-link-service/azure-private-link-service-e8bc0c6.md) for details. Instead of configuring the certificate in the backend service, for Azure Application Gateway the certificate has to be configured in the HTTPS listener of the gateway itself.



<a name="loioaf86a457ffd84324a6691c6ea1649dd6__section_dh3_wwk_x5b"/>

## Known Limitations

-   Azure Application Gateway requires a `V2` SKU to work with PrivateLink. The `V1` SKUs do not work with PrivateLink.



<a name="loioaf86a457ffd84324a6691c6ea1649dd6__section_jjt_r4c_svb"/>

## Tutorials

Martin Pankraz published a blog post outlining the steps how set up an Application Gateway and consume it via SAP Private Link:

[SAP private linky swear with Azure – to WAF or not to WAF with SAP Private Link](https://blogs.sap.com/2022/11/30/sap-private-linky-swear-with-azure-to-waf-or-not-to-waf%F0%9F%90%B6-with-sap-private-link/)

