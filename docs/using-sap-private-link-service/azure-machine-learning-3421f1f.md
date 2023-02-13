<!-- loio3421f1fc47254c8187c31ba2a2d7d0aa -->

# Azure Machine Learning

Consume Azure Machine Learning with SAP Private Link service.



<a name="loio3421f1fc47254c8187c31ba2a2d7d0aa__section_p4x_qvv_fwb"/>

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

Identifies the subresource on Azure the private link should be created for. Must be `amlworkspace`.



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
>     "resourceId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.MachineLearningServices/workspaces/myAmlWorkspace",
>     "subResource": "amlworkspace",
>     "requestMessage": "Please approve connection"
> }
> ```



<a name="loio3421f1fc47254c8187c31ba2a2d7d0aa__section_es3_gwv_fwb"/>

## Binding Credentials

The following binding credentials are provided:

****


<table>
<tr>
<td valign="top">

*inferenceHostname*



</td>
<td valign="top">

DNS entry to connect to Azure Machine Learning endpoints of the connected Azure Machine Learning workspace. Should be used in combination with the managed online endpoint name provided by Azure, for example, `myManagedOnlineEndpoint.00000000-0000-0000-0000-00000000.inference.westeurope.privatelink.api.azureml.ms`.



</td>
</tr>
<tr>
<td valign="top">

*notebooksHostname*



</td>
<td valign="top">

DNS entry for connecting to the Azure Machine Learning Workspace's Jupyter Notebooks.



</td>
</tr>
<tr>
<td valign="top">

*workspaceCertHostname*



</td>
<td valign="top">

DNS entry for the certificate endpoint to access the Azure Machine Learning Workspace's management API.



</td>
</tr>
<tr>
<td valign="top">

*workspaceHostname*



</td>
<td valign="top">

DNS entry for accessing the Azure Machine Learning Workspace's management API.



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
>                 "inferenceHostname": "*.00000000-0000-0000-0000-00000000.inference.westeurope.privatelink.api.azureml.ms",
>                 "notebooksHostname": "ml-workspaceabc-westeurope-00000000-0000-0000-0000-00000000.westeurope.privatelink.notebooks.azure.net",
>                 "workspaceCertHostname": "00000000-0000-0000-0000-00000000.workspace.westeurope.cert.privatelink.api.azureml.ms",
>                 "workspaceHostname": "00000000-0000-0000-0000-00000000.workspace.westeurope.privatelink.api.azureml.ms",
>             }
>         }
>     ]
> }
> ```



<a name="loio3421f1fc47254c8187c31ba2a2d7d0aa__section_vcc_wwv_fwb"/>

## Sample Applications

There is no custom configuration needed for your application to consume the Azure Machine Learning via Private Link.

You can follow any tutorial using the Azure SDK for the language of your choice.

