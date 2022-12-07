<!-- loiocf3528f219f1439b899267dc56500040 -->

# Amazon Relational Database Service \(RDS\) - Aurora Data API

Consume Amazon Relational Database Service \(RDS\) - Aurora DATA API with SAP Private Link service.



<a name="loiocf3528f219f1439b899267dc56500040__section_vns_h4t_45b"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)



</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon RDS Data API, the value is always in the form com.amazonaws.<region\>.rds-data.



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
>     "serviceName": "com.amazonaws.us-east-1.rds-data",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": "*",
>               "Action": [
>                   "rds-data:BatchExecuteStatement",
>                   "rds-data:BeginTransaction",
>                   "rds-data:CommitTransaction",
>                   "rds-data:ExecuteStatement",
>                   "rds-data:RollbackTransaction"
>               ],
>               "Effect": "Allow",
>               "Resource": "*"
>           }]
>     }
> }
> ```



<a name="loiocf3528f219f1439b899267dc56500040__section_pb5_s4t_45b"/>

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
>                 "hostname": "vpce-00000000000000000-00000000.rds-data.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



<a name="loiocf3528f219f1439b899267dc56500040__section_g5d_mxq_nvb"/>

## Sample Application

Please find a sample app demonstrating the necessary configuration of the AWS SDK on [Github](https://github.com/SAP-samples/private-link-aws-services/tree/main/rds-data).



<a name="loiocf3528f219f1439b899267dc56500040__section_v2v_y4t_45b"/>

## Known Limitations

-   Be aware that the Aurora Data API only allows interacting with the HTTPS API. It does **not** allow interacting with the regular SQL API. Neither SAP nor AWS offers a supported way to connect to the RDS SQL listener over Private Link, but there [are some community articles](https://blog.andreev.it/?p=9118) leveraging AWS Endpoint Service to achieve it.

-   The Data API is only supported for [Aurora Serverless v1](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/data-api.html), not v2.

