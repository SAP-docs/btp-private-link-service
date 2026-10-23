<!-- loio7eeeb76de95b4c9eab577d1cb6fef7da -->

# Best Practices for Secure Endpoint Approval on Google Cloud Platform

Learn about recommended secure approval processes when you establish a connection through Private Link service.



## Context

To establish a connection from SAP BTP to a Google Cloud service running in your Google Cloud project, the service owner must approve each connection request in the Google Cloud console.



## Secure Approval

Consider the following recommendations for secure approvals.



### Allow requests from SAP BTP Cloud Foundry and Kyma environment accounts only

You can configure Google Private Service Connect so that only consumers from allowlisted Google Cloud projects can create requests.

We strongly recommend that you configure this setting:

1.  In the Google Cloud console, navigate to your *Private Service Connect*.
2.  Navigate to *Published services* and select your service.
3.  At *Edit service details*, under *Connection preference*, select *Accept connections for selected projects*.
4.  Click *Add accepted project* and add the Google Cloud project IDs of the SAP BTP accounts for the landscape where your Private Link service should be consumed from. A current list of project IDs can be found in [3811111 - Best Practices for Secure Endpoint Approval](https://me.sap.com/notes/3811111).
5.  Click *Save*.

With this protection in place, only the approved SAP BTP accounts can create approval requests to your Google Cloud Private Service Connect.

