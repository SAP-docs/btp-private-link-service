<!-- loiob7b0e391d04048a2a20499cd1b67d907 -->

# Amazon S3

Consume AWS S3 with SAP Private Link service.



<a name="loiob7b0e391d04048a2a20499cd1b67d907__section_l2p_djt_45b"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)



</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon S3, the value is always in the form com.amazonaws<region\>.s3.



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
>     "serviceName": "com.amazonaws.us-east-1.s3",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": "*",
>               "Action": [
>                   "s3:Get*",
>                   "s3:List*"
>               ],
>               "Effect": "Allow",
>               "Resource": "*"
>           }]
>     }
> }
> ```



<a name="loiob7b0e391d04048a2a20499cd1b67d907__section_wzg_5jt_45b"/>

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
>                 "hostname": "*.vpce-068c84244a1b70734-r9rznuj8.s3.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



<a name="loiob7b0e391d04048a2a20499cd1b67d907__section_cmg_lyq_nvb"/>

## Sample Application

Please find a sample app demonstrating the necessary configuration of the AWS SDK on [Github](https://github.com/SAP-samples/private-link-aws-services/tree/main/s3).



<a name="loiob7b0e391d04048a2a20499cd1b67d907__section_w2c_bkt_45b"/>

## Known Limitations

-   [S3 Multi-Region Access Points](https://docs.aws.amazon.com/AmazonS3/latest/userguide/MultiRegionAccessPoints.html) are currently not supported by SAP Private Link service.


