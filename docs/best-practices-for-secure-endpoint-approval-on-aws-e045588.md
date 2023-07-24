<!-- loioe0455888a6e44eb2bda8b8edb13dc55a -->

# Best Practices for Secure Endpoint Approval on AWS

Learn about recommended secure approval processes when establishing a connection via Private Link service



<a name="loioe0455888a6e44eb2bda8b8edb13dc55a__section_lwk_2hf_yrb"/>

## Context

To establish a connection from SAP BTP to an AWS service running in your AWS account, each connection request has to be approved by the service owner in the AWS console.



<a name="loioe0455888a6e44eb2bda8b8edb13dc55a__section_z43_kb1_wrb"/>

## Secure Approval

Consider the following recommendations for secure approvals.



### 

**Only allow requests from SAP BTP CF's AWS account**

You can configure AWS Endpoint Service so that only consumers from allowlisted AWS accounts can even create requests.

We strongly recommend to set this setting by executing the following steps:

1.  In the AWS console, navigate to your Endpoint Service

2.  Navigate to *Allowed Principals* and click on *Allowed Principals*.

3.  Find the SAP BTP AWS Account IDs for the landscape where your Endpoint Service should be consumed from. A current list of account IDs can be found in <https://me.sap.com/systemsprovisioning/connectivity\>
4.  For each account ID, hit *Add Principal* and enter the ARN in form of `arn:aws:iam::<SAP BTP account ID from step 3>:root`.

5.  Hit *Allow principals*.


With this protection in place, only the approved SAP BTP accounts can create approval requests to your AWS Endpoint Service in the first place.

You still need to make sure you follow the steps below to only approve benign requests from within SAP BTP:



### **Case 1: The user requesting the private link is also the AWS service owner \(approver\)**

If the person creating the request in SAP BTP and the person approving those requests are one and the same person, you must check the trustworthiness by matching the endpoint ID that is displayed after the request creation:

> ### Sample Code:  
> ```
> 
>  
>    cf service privatelink-test
>    Showing status of last operation:
>  
>    status:     create in progress
>    message:    Connection from VPC Endpoint ID 'vpce-047f057f38a2e27e1' not yet approved to service 'com.amazonaws.vpc.us-east-1.vpce-svc-0d727708b69ad6738'. Waiting for approval.
>  
> 
> ```

In this case, the endpoint connection `vpce-047f057f38a2e27e1` can be safely approved. Don't approve any other connection requests as their origin can't be verified and might come from an unknown source.

> ### Tip:  
> To compare the endpoint ID, paste the endpoint ID in the filter function in the Endpoint connections section. It only returns the specific endpoint connection.



### **Case 2: The user requesting the private link isn't the AWS service owner \(approver\)**

If the person creating the request in SAP BTP is **not** identical to the person approving those requests, we recommend sharing the endpoint ID over an established, secure, and private channel. The endpoint ID is the information that is needed to check whether the incoming request can be trusted.

An example process could look as follows:

1.  The requestor creates the SAP BTP Private Link service instance.

2.  The requestor copies the endpoint ID from the output of **cf service <instance\\\>** \(for example \`vpce-047f057f38a2e27e1\`\\\)
3.  The requestor sends a message to the service owner and asks to approve the request with endpoint ID \`vpce-047f057f38a2e27e1\`.

4.  The approver receives the message, browses to the Approval request in the AWS console, and approves \`vpce-047f057f38a2e27e1\`.


> ### Tip:  
> To compare the endpoint ID, paste the endpoint ID in the filter function in the Endpoint connections section. It only returns the specific endpoint connection.

With such processes in place, users can reduce security risks resulting from approving wrong or malicious requests considerably.

