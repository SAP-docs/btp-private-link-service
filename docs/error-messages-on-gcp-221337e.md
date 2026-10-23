<!-- loio221337ee4e5643d181c044bdd2f2d95b -->

# Error Messages on GCP

****


<table>
<tr>
<th valign="top">

Error Message

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

ResourceId: resourceId is a required field

</td>
<td valign="top">

Specify your valid input parameters. See [Connect SAP Private Link Service to Google Cloud Private Service Connect](https://github.tools.sap/privatelink/fork-btp-private-link-service/blob/pls-2254/tutorials/setup.md)

</td>
</tr>
<tr>
<td valign="top">

The resource ID you specified is incorrect. Provide the correct Google Service Attachment to establish a connection, for example 'projects/<gcp-project\>/regions/<gcp-region\>/serviceAttachments/<my-service-attachment\>'

</td>
<td valign="top">

See [Tutorial: Connect SAP Private Link Service to Google Cloud Private Service Connect](https://github.tools.sap/privatelink/fork-btp-private-link-service/blob/pls-2254/tutorials/setup.md)

</td>
</tr>
<tr>
<td valign="top">

Bindings can only be created for private endpoints in status 'succeeded'. Current status is 'failed'.

</td>
<td valign="top">

Please recreate the service instance and try again. For more information, see [Tutorial: Connect SAP Private Link Service to Google Cloud Private Service Connect](https://github.tools.sap/privatelink/fork-btp-private-link-service/blob/pls-2254/tutorials/setup.md)

</td>
</tr>
<tr>
<td valign="top">

Private endpoint wasn't approved within 24 hours. Please create a new Private Link service.

</td>
<td valign="top">

Please recreate the service instance and try again. For more information, see [Connect SAP Private Link Service to Google Cloud Private Service Connect](https://github.tools.sap/privatelink/fork-btp-private-link-service/blob/pls-2254/tutorials/setup.md)

</td>
</tr>
<tr>
<td valign="top">

Cross-provider consumption is forbidden.

</td>
<td valign="top">

Your SAP BTP subaccount cloud provider should be the same as the cloud provider of the service you are connecting via private link.

</td>
</tr>
<tr>
<td valign="top">

The Google Service Attachment you specified is running in region '<other-region\>', this SAP BTP landscape can only connect to service attachments in region '<btp-region\>'.

</td>
<td valign="top">

The region you want to connect to does not match the SAP BTP landscape region. Make sure your Google Service Attachment is in the same region as your SAP BTP landscape.

</td>
</tr>
<tr>
<td valign="top">

No availability zones of Google Service Attachment '<service-attachment\>' matched with supported availability zones.

</td>
<td valign="top">

The service attachment you want to connect to is not available in the supported availability zones for this SAP BTP landscape.

</td>
</tr>
</table>

