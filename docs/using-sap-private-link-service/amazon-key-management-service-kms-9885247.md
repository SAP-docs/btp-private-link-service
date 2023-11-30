<!-- loio9885247061744904a197b1572049aa35 -->

# Amazon Key Management Service \(KMS\)

Consume Amazon Key Management Service \(KMS\) with SAP Private Link service.



<a name="loio9885247061744904a197b1572049aa35__section_gyw_vpm_mwb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)

</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon KMS, the value is always in the form com.amazonaws.<region\>.kms.

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
>  
>  {
>      "serviceName": "com.amazonaws.us-east-1.kms",
>      "policyDocument": {
>          "Statement": [
>              {
>                  "Principal": "*",
>                  "Action": [
>                      "kms:Decrypt",
>                      "kms:DescribeKey",  
>                      "kms:ListAliases", 
>                      "kms:ListKeys"
>                  ],
>                  "Effect": "Allow",
>                  "Resource": "*"
>              }
>          ]
>      }
>  }
>  
> ```



<a name="loio9885247061744904a197b1572049aa35__section_d2m_yqm_mwb"/>

## Binding Credentials

The following binding credentials are provided:


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
>      ...
>      "privatelink": [
>          {
>              ...
>              "credentials": {
>                  "hostname": "vpce-00000000000000000-00000000.kms.us-east-1.vpce.amazonaws.com"
>              }
>          }
>      ]
>  }
> ```



<a name="loio9885247061744904a197b1572049aa35__section_i3s_frm_mwb"/>

## Known Limitations

SAP Private Link service supports the `kms` `serviceName` in the public AWS Cloud, `kms-fips` in the AWS GovCloud \(US\) is not supported.

