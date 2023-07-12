<!-- loio6c7c8a9282e344979295efb882637cd4 -->

# Concepts

Get to know the basic terms of the SAP Private Link service.



<a name="loio6c7c8a9282e344979295efb882637cd4__section_wwc_5hz_cpb"/>

## Components

To privately access a service in your **IaaS Provider account**, the SAP Private Link service creates a **private endpoint** that establishes a point-to-site connection between SAP BTP and the service:

 ![Components of the SAP Private Link service](images/SAP_Private_Link_Service_Components_2b28665.png) 


<dl>
<dt><b>

IaaS Provider Account

</b></dt>
<dd>

The account that contains the selected service to which you want to establish a private connection for a selected service from your application running on SAP BTP.



</dd><dt><b>

Private Endpoint

</b></dt>
<dd>

A connection point that provides an internal IP address to an IaaS provider service in your own IaaS provider account that would normally only be accessible via a public IP address.



</dd>
</dl>



<a name="loio6c7c8a9282e344979295efb882637cd4__section_zby_5hz_cpb"/>

## Establishing a Private Connection

To establish the private connection, you first create a **service instance** of the SAP Private Link service by providing the **identifier** of the IaaS provider service instance. After **approving** the creation of the private endpoint in your IaaS provider account, you **bind** the service instance to your application and can then start using the private endpoint.

However, this binding does not include any credentials for accessing the service in your own IaaS account. You need to provide the credentials to your application by different means, for example, by creating a user-provided service that contains the required information, and binding it to the application.

 ![Establishing a private connection using the SAP Private Link service](images/SAP_Private_Link_Service_Concepts_Flow_a76643c.png) 


<dl>
<dt><b>

Service Identifier

</b></dt>
<dd>

The unique identifier of a service instance of an IaaS provider service that has to be provided during the creation of the SAP Private Link service instance. The actual term depends on the IaaS provider, for example, in Azure, this unique service identifier is called *service resource*.



</dd><dt><b>

Service Instance

</b></dt>
<dd>

Creating a service instance of the SAP Private Link service sets up a private endpoint that is associated with this service instance.



</dd><dt><b>

Binding

</b></dt>
<dd>

Binding the service instance of the SAP Private Link service to the application gives the Cloud Foundry space access to the private endpoint. Binding the user-provided service to the application shares the service credentials with the application.



</dd><dt><b>

Credentials

</b></dt>
<dd>

Creating a user-provided service, for example, enables you to share the credentials of the bound service instance in the IaaS provider account with the application in your SAP BTP account.



</dd>
</dl>



> ### Note:  
> Depending on the IaaS provider, you might need to perform additional steps. For more information, see [Using SAP Private Link Service](using-sap-private-link-service/using-sap-private-link-service-3672119.md).

