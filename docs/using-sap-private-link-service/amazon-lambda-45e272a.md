<!-- loio45e272a9f2cf465f8817e16d0e032ec9 -->

# Amazon Lambda

Consume Amazon Lambda with SAP Private Link service.



<a name="loio45e272a9f2cf465f8817e16d0e032ec9__section_v33_s12_4vb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)



</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon Lambda, the value is always in the form com.amazonaws.<region\>.lambda.



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
>     "serviceName": "com.amazonaws.us-east-1.lambda",
>     "policyDocument": {
>         "Statement": [
>             {
>                 "Principal": "*",
>                 "Action": [
>                     "lambda:InvokeFunction"
>                 ],
>                 "Effect": "Allow",
>                 "Resource": "arn:aws:lambda:us-east-1:123456789012:function:myFunction"
>             }
>         ]
>     }
> }
> ```



<a name="loio45e272a9f2cf465f8817e16d0e032ec9__section_cs5_lb2_4vb"/>

## Binding Credentials

The following binding credentials are provided:

****


<table>
<tr>
<td valign="top">

*hostname*



</td>
<td valign="top">

Regional DNS hostname to connect to the AWS interface endpoint.



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
>                 "hostname": "vpce-00000000000000000-00000000.lambda.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



<a name="loio45e272a9f2cf465f8817e16d0e032ec9__section_dz5_rb2_4vb"/>

## Sample Application

Please find a sample app demonstrating the necessary configuration of the AWS SDK on [Github](https://github.com/SAP-samples/private-link-aws-services/tree/main/lambda).

