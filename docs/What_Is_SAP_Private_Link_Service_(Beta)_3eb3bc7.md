<!-- loio3eb3bc7aa5db4b5da9dcdbf8ee478e52 -->

# What Is SAP Private Link Service \(Beta\)?

 Provide private connectivity to selected services. 

> ### Note:  
> This is a beta service available on SAP BTP for subaccounts in enterprise accounts. For more information, see [Important Disclaimers and Legal Information](https://help.sap.com/viewer/disclaimer).

SAP Private Link service establishes a private connection between selected SAP BTP services and selected services in your own IaaS provider accounts. By reusing the private link functionality of our partner IaaS providers, it lets you access your services through private network connections to avoid data transfer via the public Internet.



## Environment

This service is available in the Cloud Foundry environment.



## Features

  Access services privately 
 :   Enable access to private service endpoints and avoid public endpoints when connecting to selected service instances across account boundaries.

   Transfer data privately 
 :   Transfer data over private networks and avoid data transfer over the public Internet when connecting to selected service instances across account boundaries.

 

## Overview

To privately access a service in your IaaS Provider account, SAP Private Link service creates a private endpoint and reuses the private link functionality of the IaaS provider:

 ![Establish a private connection using SAP Private Link service.](images/Private_Account_Overview_56b73fb.png) 

For more information, see [Concepts](Concepts_6c7c8a9.md).



## Supported Scenarios

SAP Private Link service supports the following scenarios:

-    [Consume Azure Native Services in SAP BTP](Consume_Azure_Native_Services_in_SAP_BTP_e9cc677.md)

    > ### Restriction:  
    > For the beta release, you can connect to Microsoft Azure Private Link Service running behind the Azure Standard Load Balancer.




## Tools

-   **SAP BTP cockpit**: Use the SAP BTP cockpit to create service instances and application bindings.

-   **Cloud Foundry command line interface**: Use the Cloud Foundry command line interface to create service instances and application bindings. For more information, see [Working with the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2f1d4abd0f9f4760a301f43513d2efa6.html)

-   **IaaS provider tools**


