<!-- loioe8bc0c6440834a47a0ff57cb4efc0dc2 -->

# Azure Private Link Service

Consume Azure Private Link service with SAP Private Link service \(Beta\).



<a name="loioe8bc0c6440834a47a0ff57cb4efc0dc2__section_nzf_fyn_nrb"/>

## Request Reference

The following Cloud Foundry service specific configuration parameters are supported during a service instance creation:

> ### Sample Code:  
> ```
> 
> {
>     "resourceId": "/subscriptions/<subscription>/resourceGroups/<rg>/providers/Microsoft.Network/privateLinkServices/<my-private-link-service>",
>     "requestMessage": "request message"
> }
> 
> ```



<a name="loioe8bc0c6440834a47a0ff57cb4efc0dc2__section_osr_3yn_nrb"/>

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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/privateLinkServices/myPrivateLinkService",
>     "requestMessage": "Please approve connection"
> }
> 
> ```



<a name="loioe8bc0c6440834a47a0ff57cb4efc0dc2__section_kpl_jyn_nrb"/>

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
>                 "additionalHostname": "<private link additional hostname>"
>             }
>         }
>     ]
> }
> 
> ```



<a name="loioe8bc0c6440834a47a0ff57cb4efc0dc2__section_qtm_jyn_nrb"/>

## Credentials


<table>
<tr>
<td valign="top">

*hostname*



</td>
<td valign="top">

Private DNS entry to connect to the Azure resource.



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
>                 "hostname": "db0ebb6b-d6b9-edfb-85a6-a22076438dd0.43c6b4ab075f566feb1541589d570cd2c164c5d4acda6617f6e5139b.p1.pls.sap.internal",
>                 "additionalHostname": "db0ebb6b-d6b9-edfb-85a6-a22076438dd0.p1.pls.sap.internal"
>             }
>         }
>     ]
> }
> ```



<a name="loioe8bc0c6440834a47a0ff57cb4efc0dc2__section_xvn_jyn_nrb"/>

## Transport Layer Security

The SAP Private Link service creates private DNS entries for Azure Private Link services. These entries can be used to issue TLS certificates so that connected systems can identify themselves.

The binding credentials of a Cloud Foundry service instance contain information about the created private DNS entries.

The *hostname* sticks to the pattern `<CF service instance ID>.<resource ID hash>.<private DNS zone>`, whereas *additionalHostname* sticks to `<CF service instance ID>.<private DNS zone>`.

The connected system might identify itself with a wildcard TLS certificate issued for `*.<resource ID hash>.<private DNS zone>`, basically a subset of the domain provided via *hostname*. This ensures validity of the certificate across different Private Link service instances for the same resource ID. Thus, we recommend installing a TLS certificate for `*.<resource ID hash>.<private DNS zone>` on your backing system and connecting via hostname.

After a service instance has been deleted, Private Link service \(Beta\) ensures that the hostname of a new service instance carries the same `<resource ID hash>.<private DNS zone>` for three months. This ensures that wildcard certificates continue to work even after the re-creation of a service instance.

In case TLS certificate validity across different Private Link service instances is technically not possible, the connected system might identify itself with a certificate for `<CF service instance ID>.<private DNS zone>`which equals to the provided *additionalHostname*.

