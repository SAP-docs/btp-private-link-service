<!-- loiob4bc64d542ee4b238139a3987a4d1713 -->

# Error Messages on AWS




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

serviceName: serviceName is a required field

</td>
<td valign="top">

Specify your valid input parameters. See [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html).

</td>
</tr>
<tr>
<td valign="top">

The serviceName you specified is incorrect. Provide the correct AWS VPC Endpoint Service Name to establish a connection, for example 'com.amazonaws.vpce.us-east-1.vpce-svc-0b57ce3e693490caf'.

</td>
<td valign="top">

Specify your valid input parameters. See [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html).

</td>
</tr>
<tr>
<td valign="top">

Could not access VPC Endpoint Service 'com.amazonaws.vpce.us-east-1.vpce-svc-0b57ce3e693490cae': code 'InvalidServiceName', message 'The Vpc Endpoint Service 'com.amazonaws.vpce.us-east-1.vpce-svc-0b57ce3e693490cae' does not exist'.

</td>
<td valign="top">

Specify your valid input parameters. See [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html).

</td>
</tr>
<tr>
<td valign="top">

Could not find a VPC Endpoint Service with type Interface for serviceName 'com.amazonaws.us-east-1.dynamodb'. Please provide the serviceName for a VPC Endpoint Service of type Interface.

</td>
<td valign="top">

The service you want to connect to does not support VPC Endpoint services. For an overview of supported services, see [Consume Amazon Web Services in SAP BTP](using-sap-private-link-service/consume-amazon-web-services-in-sap-btp-5753419.md).

</td>
</tr>
<tr>
<td valign="top">

VPC Endpoints to VPC Endpoint Services for 'appstream.api' are currently not supported.

</td>
<td valign="top">

The service you want to connect to does not support VPC Endpoint services. For an overview of supported services, see [Consume Amazon Web Services in SAP BTP](using-sap-private-link-service/consume-amazon-web-services-in-sap-btp-5753419.md).

</td>
</tr>
<tr>
<td valign="top">

The VPC Endpoint Service you specified is running in Region 'us-west-1', this SAP BTP landscape can only connect to VPC Endpoint Services in region 'us-east-1'.

</td>
<td valign="top">

The region you want to connect to does not support VPC Endpoint services.

</td>
</tr>
<tr>
<td valign="top">

No availability zones of VPC Endpoint Service 'com.amazonaws.vpce.us-east-1.vpce-svc-0b57ce3e693490cae' matched with supported availability zones. SAP BTP supports the following availability zone IDs: 'use1-az2, use1-az4, use1-az6'.

</td>
<td valign="top">

The endpoint service you want to connect to is not available in this zone. See  <?sap-ot O2O class="- topic/xref " href="6d1453baa5fa4e8fb3297e53ceb96bf6.xml" text="" desc="" xtrc="xref:6" xtrf="file:/home/builder/src/dita-all/nbu1622790870513/loioc337387b1cd14803bda2ccf11484b81b_en-US/src/content/localization/en-us/b4bc64d542ee4b238139a3987a4d1713.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

</td>
</tr>
<tr>
<td valign="top">

Only 2 availability zones of VPC Endpoint Service 'com.amazonaws.vpce.us-east-1.vpce-svc-0b57ce3e693490cae' matched with supported availability zones \('use1-az1', 'use1-az2', 'use1-az3'\). This means that the endpoint would only be available in 2 AZs \('use1-az1', 'use1-az2'\). If this is acceptable, please set the parameter 'desiredAZs' to 2 during service instance creation.

</td>
<td valign="top">

The endpoint service you specified is not deployed to all supported zones on SAP BTP. See  <?sap-ot O2O class="- topic/xref " href="6d1453baa5fa4e8fb3297e53ceb96bf6.xml" text="" desc="" xtrc="xref:7" xtrf="file:/home/builder/src/dita-all/nbu1622790870513/loioc337387b1cd14803bda2ccf11484b81b_en-US/src/content/localization/en-us/b4bc64d542ee4b238139a3987a4d1713.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

</td>
</tr>
<tr>
<td valign="top">

The VPC Endpoint connection was not approved within 24 hours. Please create a new Private Link service instance.

</td>
<td valign="top">

Please recreate the service instance and try again. For more information, see [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html).

</td>
</tr>
<tr>
<td valign="top">

Connection to VPC Endpoint Service ''com.amazonaws.vpce.us-east-1.vpce-svc-0b57ce3e693490caf' rejected. Initiate a new connection by creating a new Private Link service instance.

</td>
<td valign="top">

Please recreate the service instance and try again. For more information, see [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html).

</td>
</tr>
<tr>
<td valign="top">

Bindings can only be created for private endpoints in status "succeeded". Current status is "failed".

</td>
<td valign="top">

Please recreate the service instance and try again. For more information, see [Connect SAP Private Link Service to AWS Private Link Service](https://developers.sap.com/tutorials/private-link-aws.html).

</td>
</tr>
<tr>
<td valign="top">

AWS MSK VPC Connection is only supported with "SASL\_SCRAM" and "TLS" authentication types. Please provide one of these two options at creation.

</td>
<td valign="top">

For more information, see[Creation Request Configuration Parameters](https://help.sap.com/docs/private-link/private-link1/supported-services-for-amazon-web-services-in-sap-btp?version=CLOUD#creation-request-configuration-parameters).

</td>
</tr>
<tr>
<td valign="top">

AWS MSK cluster ARN is not provided. Please provide AWS MSK cluster ARN.

</td>
<td valign="top">

For more information, see [Creation Request Configuration Parameters](https://help.sap.com/docs/private-link/private-link1/supported-services-for-amazon-web-services-in-sap-btp?version=DEV#creation-request-configuration-parameters).

</td>
</tr>
<tr>
<td valign="top">

AWS MSK cluster cross-account access is not allowed from AWS account 1111122222. Please grant access by editing your MSK cluster policy. More details can be found at [Best Practices for Secure Endpoint Approval on AWS](best-practices-for-secure-endpoint-approval-on-aws-e045588.md).

</td>
<td valign="top">

For more information, see [.](best-practices-for-secure-endpoint-approval-on-aws-e045588.md)

</td>
</tr>
<tr>
<td valign="top">

Not equal or lower amount of availability zones of your MSK cluster 'demo' matched with supported availability zones. SAP BTP supports the following availability zone IDs: 'use1-az1', 'use1-az2', 'use1-az3' Please correct your AWS MSK cluster's availability zones to be equal or lower amount according SAP BTP supported.

</td>
<td valign="top">

For more information, see [Create an Amazon MSK Cluster](https://docs.aws.amazon.com/msk/latest/developerguide/create-cluster.html).

</td>
</tr>
<tr>
<td valign="top">

Only 3 subnets assigned to your MSK cluster with supported of \(6\) availability zones \('use1-az1', 'use1-az2', 'use1-az3', 'use1-az4', 'use1-az5', 'use1-az6'\). This means that the endpoint would only be available in 3 AZs \('use1-az1', 'use1-az2', 'use1-az3'\). If this is acceptable, please set the parameter 'desiredAZs' to 3 during service instance creation.

</td>
<td valign="top">

For more information, see [Creation Request Configuration Parameters](https://help.sap.com/docs/private-link/private-link1/supported-services-for-amazon-web-services-in-sap-btp?version=DEV#creation-request-configuration-parameters).

</td>
</tr>
<tr>
<td valign="top">

Cross-provider consumption is forbidden.

</td>
<td valign="top">

Your SAP BTP cockpit subaccount cloud provider should be the same as the cloud provider of the service you are connecting via private link.

</td>
</tr>
</table>

