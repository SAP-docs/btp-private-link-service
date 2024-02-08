<!-- loio9f07803408244c289a3460edd53bcff8 -->

# Transport Layer Security Amazon Web Services

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

