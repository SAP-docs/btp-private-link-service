<!-- loio407fb1909cbf46058d47937802a1fa2b -->

# Azure Key Vault

Consume Azure KeyVault and Azure Keyvault ManagedHSM with SAP Private Link service.



<a name="loio407fb1909cbf46058d47937802a1fa2b__section_hkd_sdp_p5b"/>

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
> KeyVault
> 
> ```
>  {
>      "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVault",
>      "subResource": "vault",
>      "requestMessage": "Please approve connection"
>  }
> ```

> ### Sample Code:  
> KeyVault ManagedHSM
> 
> ```
> {
>      "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/managedHSMs/myHSM",
>      "subResource": "managedhsm",
>      "requestMessage": "Please approve connection"
>  }
> ```



<a name="loio407fb1909cbf46058d47937802a1fa2b__section_utb_s2p_p5b"/>

## Binding Credentials

The following binding credentials are provided:

-   *\*hostname\**: DNS entry to connect to the Azure resource. This DNS entry resolves to the internal IP address associated with this private link.


> ### Sample Code:  
> KeyVault
> 
> ```
> {
>      ...
>      "privatelink": [
>          {
>              ...
>              "credentials": {
>                  "hostname": "my-keyvault.vault.azure.net"
>              }
>          }
>      ]
>  }
> ```

> ### Sample Code:  
> KeyVault ManagedHSM
> 
> ```
> {
>      ...
>      "privatelink": [
>          {
>              ...
>              "credentials": {
>                  "hostname": "my-hsm.managedhsm.azure.net"
>              }
>          }
>      ]
>  }
> ```



<a name="loio407fb1909cbf46058d47937802a1fa2b__section_t2g_mtx_svb"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure Key Vault via Private Link.

You can follow any tutorial using the Azure SDK for the language of your choice.

