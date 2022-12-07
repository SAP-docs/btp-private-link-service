<!-- loio844bca7a51f04a15be865b9a6c1867b0 -->

# Best Practices for Secure Endpoint Approval on Azure

Learn about recommended secure approval processes when establishing a connection via Private Link service.



<a name="loio844bca7a51f04a15be865b9a6c1867b0__section_lwk_2hf_yrb"/>

## Context

To establish a connection from SAP BTP to an Azure service running in your Azure subscription, each connection request has to be approved by the service owner in the Azure portal.



<a name="loio844bca7a51f04a15be865b9a6c1867b0__section_z43_kb1_wrb"/>

## Secure Approval

Consider the following recommendations for secure approvals.



### **Only allow requests from SAP BTP CF's Azure subscription**

You can configure Azure Private Link Service so that only consumers from allowlisted Azure subscriptions can even create requests.

We strongly recommend to set this setting by executing the following steps:

1.  In the Azure Portal navigate to your Private Link service.

2.  Navigate to *Access security*.

3.  Under *Who can request access to your service?* select *Restricted by subscription*.

4.  Click *Add Subscription* and add the SAP BTP CF's subscription IDs for the landscape where your Private Link service should be consumed from.

    A current list of subscription IDs can be found in <https://me.sap.com/systemsprovisioning/connectivity\>.

5.  Hit *OK* and then *Save*.


With this protection in place, only the approved SAP BTP CF subscriptions can create approval requests to your Azure Private Link service in the first place.

You still need to make sure you follow the steps below to only approve benign requests from within SAP BTP:



### Case 1: The user requesting the private link is also the Azure service owner \(approver\)

If the person creating the request in SAP BTP and the person approving those requests are one and the same person, you must check the trustworthiness by matching the endpoint name that is displayed after the request creation:

> ### Sample Code:  
> ```
> 
> 	cf service privatelink-test
> 	Showing status of last operation from service privatelink-test...
> 
> 	status:    create in progress
> 	message:   Please approve the connection for Private Endpoint sap-privatelink-00000000-0000-0000-0000-000000000001 in your Azure portal
> 
> ```

In this case, the private endpoint connection `sap-privatelink-00000000-0000-0000-0000-000000000001` can be safely approved. Don't approve any other connection requests as their origin can't be verified and might come from an unknown source.

> ### Tip:  
> To compare the endpoint name, paste the endpoint name in the search function in the Private Link services overview. It only returns the specific endpoint.



### Case 2: The user requesting the private link isn't the Azure service owner \(approver\)

If the person creating the request in SAP BTP is **not** identical to the person approving those requests, we recommend sharing the endpoint name over an established, secure, and private channel. The endpoint name is the information that is needed to check whether the incoming request can be trusted.



An example process could look as follows:

1.  The requestor creates the SAP BTP Private Link service instance.
2.  The requestor copies the endpoint name from the output of **cf service <instance\>** \(for example `sap-privatelink-00000000-0000-0000-0000-000000000001`\).
3.  The requestor sends a message to the service owner and asks to approve the request with endpoint name `sap-privatelink-00000000-0000-0000-0000-000000000001`.
4.  The approver receives the message, browses to the Approval request in the Azure portal, and approves `sap-privatelink-00000000-0000-0000-0000-000000000001`.



> ### Tip:  
> To compare the endpoint name, paste the endpoint name in the search function in the Private Link services overview. It only returns the specific endpoint.

If desired, the requestor could include further information in the *requestMessage* field during creation. This information is displayed to the approver in the portal.

With such processes in place, users can reduce security risks resulting from approving wrong or malicious requests considerably.

