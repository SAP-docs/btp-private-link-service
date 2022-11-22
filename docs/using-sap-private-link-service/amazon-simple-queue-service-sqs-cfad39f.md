<!-- loiocfad39f9b9d544c09b90b273b27a9a8e -->

# Amazon Simple Queue Service \(SQS\)

Consume the Amazon Simple Queue Service \(SQS\) with SAP Private Link service.



<a name="loiocfad39f9b9d544c09b90b273b27a9a8e__section_phf_vkt_45b"/>

## Creation Request

The following Cloud Foundry service specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

 



</th>
</tr>
<tr>
<td valign="top">

*serviceName* \(required\)



</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon SQS, the value is always in the form com.amazonaws<region\>.sqs.



</td>
</tr>
<tr>
<td valign="top">

*policyDocument* \(optional\)



</td>
<td valign="top">

A JSON document specifying a [VPC endpoint policy](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-access.html).



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.sqs",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": {
>                   "AWS": "arn:aws:iam:123456789012:user/MyUser"
>               },
>               "Action": [
>                   "sqs:SendMessage"
>               ],
>               "Effect": "Allow",
>               "Resource": "arn:aws:sqs:us-east-2:123456789012:MyQueue"
>           }]
>     }
> }
> ```



<a name="loiocfad39f9b9d544c09b90b273b27a9a8e__section_gy5_jlt_45b"/>

## Binding Credentials

The following binding credentials are provided:

-   *hostname*: Regional DNS hostname to connect to the AWS interface endpoint

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.sqs.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



<a name="loiocfad39f9b9d544c09b90b273b27a9a8e__section_egt_vxq_nvb"/>

## Sample Application

Please find a sample app demonstrating the necessary configuration of the AWS SDK on [Github](https://github.com/SAP-samples/private-link-aws-services/tree/main/sqs).

