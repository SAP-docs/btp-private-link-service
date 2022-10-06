<!-- loiod5f96f99a9034ce290cf4384b4166255 -->

# Azure App Service or Azure Functions

Consume Azure App Service or Azure Functions with SAP Private Link service.



<a name="loiod5f96f99a9034ce290cf4384b4166255__section_rnt_nwl_t5b"/>

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

Identifies the sub-resource on Azure the private link should be created for.

Must be `sites`.



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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Web/sites/myApp",
>     "subResource": "sites",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loiod5f96f99a9034ce290cf4384b4166255__section_crr_gxl_t5b"/>

## Binding Credentials

The following binding credentials are provided:

-   *hostname*: DNS entry to connect to the workload endpoint of the App or Function. This DNS entry resolves to the internal IP address associated with this private link.
-   *scmHostname*: DNS entry to connect to the SCM endpoint \(deployment/debugging interface\) of the App or Function. This DNS entry resolves to the internal IP address associated with this private link.

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "myapp.azurewebsites.net",
>                 "scmHostname": "myapp.scm.azurewebsites.net"
>             }
>         }
>     ]
> }
> ```



<a name="loiod5f96f99a9034ce290cf4384b4166255__section_z2g_nlp_55b"/>

## Custom Domains

If your application or function offers a [Custom DNS Name](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-tutorial-custom-domain?tabs=a%2Cazurecli), your app on SAP BTP can also connect to this DNS Name \(instead of the `hostname` from above\). This will work, since the custom DNS name will have a `CNAME` record pointing to the `hostname` above, which will in turn resolve to the private endpoint's private IP, establishing the connection over the private endpoint.



<a name="loiod5f96f99a9034ce290cf4384b4166255__section_qsb_rxl_t5b"/>

## Known Limitations

-   As highlighted in the [Azure documentation](https://docs.microsoft.com/en-us/azure/app-service/networking/private-endpoint), private endpoints are only supported for App service plans Basic and above.

-   For functions, private endpoints are only supported on the Functions Premium tier or if they run on an App service plan.


