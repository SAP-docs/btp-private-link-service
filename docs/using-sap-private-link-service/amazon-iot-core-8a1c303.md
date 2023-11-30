<!-- loio8a1c303a2c8b49bab472377da537e8e5 -->

# Amazon IoT Core

Consume Amazon IoT Core with SAP Private Link service.



<a name="loio8a1c303a2c8b49bab472377da537e8e5__section_bkc_3g4_wwb"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:

****


<table>
<tr>
<td valign="top">

*serviceName* \(required\)

</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to. In case of Amazon IoT Core, the value is always in the form com.amazonaws.<region\>.iot.data.

</td>
</tr>
<tr>
<td valign="top">

*desiredAZs* \(optional\)

</td>
<td valign="top">

SAP BTP CF runs in three AWS availability zones. AWS IoT Core does not support VPC endpoints in some Availability Zones within a Region. This is a precautionary measure for [choosing an Availability Zone](https://docs.aws.amazon.com/iot/latest/developerguide/IoTCore-VPC.html#Create-VPC-endpoints) where AWS IoT Core is available in your specific AWS Region.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.iot.data",
>     "desiredAZs": 2
> }
> ```



<a name="loio8a1c303a2c8b49bab472377da537e8e5__section_skv_vg4_wwb"/>

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
>                 "hostname": "vpce-00000000000000000-00000000.data.iot.us-east-1.vpce.amazonaws.com", 
>             }
>         }
>     ]
> }
> ```



<a name="loio8a1c303a2c8b49bab472377da537e8e5__section_inr_1h4_wwb"/>

## Known Limitations

-   VPC endpoints are currently supported for [IoT data endpoints](https://docs.aws.amazon.com/iot/latest/developerguide/iot-connect-devices.html) only.

-   AWS IoT Core does not support [VPC endpoint policies](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-access.html#vpc-endpoint-policies) at this time.

-   See also the known limitations of AWS regarding AZs and Regions in their [documentation](https://docs.aws.amazon.com/iot/latest/developerguide/IoTCore-VPC.html#Create-VPC-endpoints).


