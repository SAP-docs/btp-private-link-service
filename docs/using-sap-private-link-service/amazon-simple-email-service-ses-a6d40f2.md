<!-- loioa6d40f23a1144a5cb0b12105a864236d -->

# Amazon Simple Email Service \(SES\)

Consume Amazon Simple Email Service \(SES\) with SAP Private Link service.



<a name="loioa6d40f23a1144a5cb0b12105a864236d__section_ksk_cnt_45b"/>

## Creation Request

The following Cloud Foundry service specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)



</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

In case of Amazon SES, the value is always in the form com.amazonaws<region\>.email-smtp.



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.email-smtp"
> }
> ```



<a name="loioa6d40f23a1144a5cb0b12105a864236d__section_tsf_jnt_45b"/>

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
>                 "hostname": "vpce-00000000000000000-00000000.email-smtp.us-east-1.vpce.amazonaws.com", 
>             }
>         }
>     ]
> }
> ```



<a name="loioa6d40f23a1144a5cb0b12105a864236d__section_czy_rxq_nvb"/>

## Sample Application

Please find a sample app demonstrating the necessary configuration of the AWS SDK on [Github](https://github.com/SAP-samples/private-link-aws-services/tree/main/ses) .



<a name="loioa6d40f23a1144a5cb0b12105a864236d__section_rsc_pnt_45b"/>

## Known Limitations

-   SES only offers private connection to the SMTP endpoint, not the HTTPS API endpoint.

-   Interface endpoints to SES do not support [VPC endpoint policies](https://docs.aws.amazon.com/vpc/latest/privatelink/aws-services-privatelink-support.html).
-   See also the known limitations of AWS regarding AZs and Regions in their [documentation](https://docs.aws.amazon.com/ses/latest/dg/send-email-set-up-vpc-endpoints.html).

