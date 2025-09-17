<!-- loio67cda52831c54a738705e3e9f1708435 -->

# Troubleshooting Guide for SAP Private Link Service



## SAP Private Link Service

-   Introduction to SAP Private Link Service



## Introduction to SAP Private Link Service

-   What is SAP Private Link Service?
-   Is this a private connection? And which protocol is used?
-   Is this connectivity a site-to-site type or site \(SAP BTP\)-to-point \(particular service on Azure/ AWS\) type?
-   Is there a limit of bandwidth or data transfer per SAP BTP global account, subaccount or space?
-   Where can I find more information about the SAP Private Link Service?
-   Does SAP Private Link service connect different hyperscalers?



## What is SAP Private Link Service?

The new SAP Private Link service on SAP BTP will enable customers and partners to access **selected** services hosted in their own hyperscaler accounts from **selected** SAP BTP services on hyperscaler accounts using private network connections, without exposing the traffic and data to public internet. For this, the service will reuse established hyperscaler functionality like [Microsoft Azure Private Link](https://azure.microsoft.com/en-us/services/private-link/) and [AWS PrivateLink](https://aws.amazon.com/privatelink/).

Since we rely on functionality from the hyperscaler providers, the service will not support cross-hyperscaler connections. For example, if the customer's BTP subaccount is on MS Azure, they will only be able to connect to services in their MS Azure account.

For more information, please check our[SAP Private Link Service SharePoint page](https://sap.sharepoint.com/sites/204642/SitePages/Overview-and-Motivation.aspx).



<a name="loio67cda52831c54a738705e3e9f1708435__section_hxm_tls_4dc"/>

## Is this a private connection? And which protocol is used?

The connection is private insofar as the transferred data will not leave the data center of the hyperscaler but will be **transported directly to the connected service**. No additional encryption is added from our side.



## Is this connectivity a site-to-site type or site \(SAP BTP\)-to-point \(particular service on Azure/ AWS\) type?

This is a **site to point** connectivity option. It allows network connectivity between all of your CF applications that run in the same CF space which holds the private link service instance and an Azure service located within your Azure account.



## Is there a limit of bandwidth or data transfer per SAP BTP global account, subaccount or space?

Currently, no such limitations are planned.



## Where can I find more information about the SAP Private Link Service?

The official documentation is available on the Help Portal: [What Is SAP Private Link Service](https://help.sap.com/viewer/product/PRIVATE_LINK/CLOUD/en-US).

An overview over the [published blog posts](https://community.sap.com/t5/forums/searchpage/tab/message?q=%22sap%20private%20link%20service%22&noSynonym=false&collapse_discussion=true%22%20scope%3D%22external)regarding our service can be found on SAP Community.

We have also published some tutorials:

-   Azure
    -   [Set Up SAP Private Link Service](https://developers.sap.com/tutorials/private-link-onboarding.html)

    -   [Connect SAP Private Link Service to Microsoft Azure Private Link Service](https://developers.sap.com/tutorials/private-link-microsoft-azure.html)​​​​​​​​​​​​​​


-   AWS

    -   [Set Up SAP Private Link Service on Amazon Web Services \(Beta\)](https://developers.sap.com/tutorials/private-link-service-onboarding-aws.html)
    -   [Connect SAP Private Link Service to AWS PrivateLink Service](https://developers.sap.com/tutorials/private-link-aws.html)


Microsoft has also published a general [FAQ for the Azure Private Link service](https://docs.microsoft.com/en-us/azure/private-link/private-link-faq), which is used as technical basis for offering our service on BTP regions on Azure.

Amazon has published a general [FAQ for the AWS Private Link service](https://aws.amazon.com/privatelink/faqs/?nc1=h_ls), which is used as technical basis for offering our service on SAP BTP regions on AWS.



## Does SAP Private Link service connect different hyperscalers?

Private Link is a hyperscaler-dependent service. We don't support between hyperscalers.

