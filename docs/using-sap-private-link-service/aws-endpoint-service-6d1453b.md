<!-- loio6d1453baa5fa4e8fb3297e53ceb96bf6 -->

# AWS Endpoint Service

Consume AWS Endpoint Services with SAP Private Link service.



<a name="loio6d1453baa5fa4e8fb3297e53ceb96bf6__section_z35_zks_45b"/>

## Creation Request

The following Cloud Foundry service-specific configuration parameters are supported during a service instance creation:


<table>
<tr>
<td valign="top">

*serviceName* \(required\)

</td>
<td valign="top">

The serviceName on AWS side that uniquely identifies the AWS endpoint service to connect to.

</td>
</tr>
<tr>
<td valign="top">

*desiredAZs* \(optional\)

</td>
<td valign="top">

SAP BTP CF runs in three AWS availability zones.

By default, SAP Private Link service expects the customer's endpoint service to also run in three availability zones. This ensures that the connection runs in the highest available fashion possible.

If the SAP Private Link detects that the endpoint service on customer side runs in fewer zones than three, the connection will be rejected unless `desiredAZs` is set to the number of present availability zones.

This is a precautionary measure to ensure that the connection cannot accidentally run with fewer than three zones.

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.vpce.us-east-1.vpce-svc-018072c5ac6df60dd",
>     "desiredAZs": 2
> }
> ```



<a name="loio6d1453baa5fa4e8fb3297e53ceb96bf6__section_dj3_jms_45b"/>

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
>                 "hostname": "vpce-00000000000000000-00000000.vpce-svc-00000000000000000.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



<a name="loio6d1453baa5fa4e8fb3297e53ceb96bf6__section_elt_5ms_45b"/>

## Transport Layer Security

If applications require to connect to the endpoint over TLS, the following two approaches can be used. While the first might be sufficient for development and testing, we recommend the latter option for productive scenarios.



### Use the AWS-provided Hostname

In the binding credentials above, customers can find the AWS-provided endpoint DNS names in the *hostname* field.

Customers can create self-signed certificates, or certificates signed by an internal company PKI for this hostname and install it on the system backing the endpoint service \(or on the AWS NLB\).

Be aware that without additional configuration, those \(self-signed\) certificates will most likely not be trusted by the client applications connecting from SAP BTP, so it's preferable to follow the approach below.



### Use your own Hostname and TLS Certificate

You can bring your own hostname and certificates with the following procedure:

1.  Create the service instance as described before. Note down the provided *hostname*.

2.  In the customer’s public DNS provider, choose a hostname in an internet-resolvable domain.

    For example:

    > ### Sample Code:  
    > ```
    > my-pls-1.services.example.com and create a CNAME record pointing to the hostname
    > ```

    For example:

    > ### Sample Code:  
    > ```
    > my-pls-1.services.example.com CNAME vpce-00000000000000000-00000000.vpce-svc-00000000000000000.us-east-1.vpce.amazonaws.com
    > ```

    > ### Note:  
    > Be aware that this record must be *created in a DNS zone that’s resolvable from the internet*, so that apps in SAP BTP can resolve the hostname.

3.  Retrieve a TLS certificate for the customer hostname from a preferred certificate supplier. This can be either a public PKI like AWS ACM, DigiCert, LetsEncrypt, Symantec public PKIs, or a company-internal PKI.

4.  Install the TLS key and certificate on the system that backs the AWS Endpoint service \(if AWS ACM is used, the certificate can automatically be assigned to the AWS NLB backing the Endpoint service\).

5.  Applications running in SAP BTP will now be able to connect to the AWS Endpoint service by connecting to `my-pls-1.example.com`. The certificate presented by the server will match the hostname, and the connection will be established flawlessly.


This approach allows customers to use their existing DNS & TLS certificate procedures together with service instances provided by the SAP Private Link service.



<a name="loio6d1453baa5fa4e8fb3297e53ceb96bf6__section_xtn_gzv_dvb"/>

## Known Limitations

-   Only AWS Endpoint services in the same region as the CF region are supported. If you want to consume workloads in a different region via Private Link, you can create a dedicated Endpoint Service \(and Network Load Balancer\) in the local region which accesses the workload in the other region via VPC peering: [Official AWS setup guide for inter-region endpoint services](https://docs.aws.amazon.com/whitepapers/latest/aws-privatelink/use-case-examples.html#inter-region-endpoint-services).


