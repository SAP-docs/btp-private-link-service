<!-- loioa0ba5f2a3629435b92977f5c89b22a78 -->

# Amazon Simple Notification Service \(SNS\)

Consume Amazon Simple Notification Service \(SNS\) with SAP Private Link service.



<a name="loioa0ba5f2a3629435b92977f5c89b22a78__section_k5m_zlt_45b"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)



</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon SNS, the value is always in the form com.amazonaws<region\>.sns.



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
>     "serviceName": "com.amazonaws.us-east-1.sns",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": {
>                   "AWS": "arn:aws:iam:123456789012:user/MyUser"
>               },
>               "Action": [
>                   "sns:Publish"
>               ],
>               "Effect": "Allow",
>               "Resource": "arn:aws:sns:us-east-2:123456789012:MyTopic"
>           }]
>     }
> }
> ```



<a name="loioa0ba5f2a3629435b92977f5c89b22a78__section_qc2_lmt_45b"/>

## Binding Credentials

The following binding credentials are provided:

-   *hostname*: Regional DNS hostname to connect to the AWS interface endpoint.


> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.sns.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



<a name="loioa0ba5f2a3629435b92977f5c89b22a78__section_yf2_dyq_nvb"/>

## Sample Applications

Please find a sample app demonstrating the necessary configuration of the AWS SDK on [Github](https://github.com/SAP-samples/private-link-aws-services/tree/main/sns).

