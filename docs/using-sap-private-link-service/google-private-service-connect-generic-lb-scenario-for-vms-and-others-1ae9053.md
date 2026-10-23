<!-- loio1ae90538333d4f4387ad34528840a678 -->

# Google Private Service Connect \(generic LB scenario for VMs and others\)

Consume Google Private Service Connect with SAP Private Link service.



<a name="loio1ae90538333d4f4387ad34528840a678__section_nzf_fyn_nrb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:




<table>
<tr>
<td valign="top">

*resourceId* \(required\)

</td>
<td valign="top">

Identifies the resource on Google the private link should be created for.

</td>
</tr>
<tr>
<td valign="top">

*requestMessage* \(optional\)

</td>
<td valign="top">

Specifies a message which is shown for the approval request on Google for the specified resource.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> {
>     "resourceId": "projects/my-project/regions/gcp-region/serviceAttachments/psc-attachment",
>     "requestMessage": "Please approve connection"
> }
> 
> ```



<a name="loio1ae90538333d4f4387ad34528840a678__section_kpl_jyn_nrb"/>

## Binding Credentials

The following binding credentials are provided:




<table>
<tr>
<td valign="top">

*hostname*

</td>
<td valign="top">

Hostname to connect to the Google resource. This hostname resolves to the internal IP address associated with this private link.

</td>
</tr>
<tr>
<td valign="top">

*additionalHostname*

</td>
<td valign="top">

Additional hostname to connect to the Google resource.

</td>
</tr>
</table>

> ### Note:  
> Refer to the section **Transport Layer Security** at the end of this chapter for more details.

> ### Sample Code:  
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "additionalHostname": "db0ebb6b-d6b9-edfb-85a6-a22076438dd0.43c6b4ab075f566feb1541589d570cd2c164c5d4acda6617f6e5139b.pls.sap.internal",
>                 "hostname": "db0ebb6b-d6b9-edfb-85a6-a22076438dd0.pls.sap.internal"
>             }
>         }
>     ]
> }
> 
> ```



<a name="loio1ae90538333d4f4387ad34528840a678__section_xvn_jyn_nrb"/>

## Transport Layer Security

The SAP Private Link service creates hostnames for connections established via [Google Private Service Connect](https://docs.cloud.google.com/vpc/docs/private-service-connect). These hostnames can be used to issue TLS certificates so that connected systems can identify themselves.

The binding credentials of a Cloud Foundry service instance contain information about the created hostnames.

The *additionalHostname* sticks to the pattern `<CF service instance ID>.<resource ID hash>.<hostname suffix>`, whereas *hostname* sticks to `<CF service instance ID>.<hostname suffix>`.

The connected system might identify itself with a wildcard TLS certificate issued for `*.<resource ID hash>.<hostname suffix>`, basically a subset of the domain provided via *additionalHostname*. This ensures validity of the certificate across different Private Link service instances for the same resource ID. Thus, we recommend installing a TLS certificate for `*.<resource ID hash>.<hostname suffix>` on your backing system and connecting via additionalHostname.

After a service instance has been deleted, Private Link service ensures that the additionalHostname of a new service instance carries the same `<resource ID hash>.<hostname suffix>` for three months. This ensures that wildcard certificates continue to work even after the re-creation of a service instance.

In case TLS certificate validity across different Private Link service instances is technically not possible, the connected system might identify itself with a certificate for `<CF service instance ID>.<hostname suffix>`which equals to the provided *hostname*.

