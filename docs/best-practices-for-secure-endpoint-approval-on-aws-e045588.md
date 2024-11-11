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

**Only allow requests from SAP BTP Cloud Foundry and Kyma environment's AWS accounts**

You can configure AWS Endpoint Service and AWS MSK cluster so that only consumers from allowlisted AWS accounts can even create requests.

We strongly recommend to set this setting by executing the following steps. Steps are separated in sub-steps for AWS Endpoint Service and AWS MSK cluster:

1.  In the AWS Console,
    -   navigate to your AWS Endpoint Service then navigate to**Allowed Principals** and click on *Allowed Principals*.

    -   navigate to your AWS MSK cluster then navigate to**Actions** and click on *Edit cluster policy*.

2.  Find the SAP BTP AWS Account IDs for the landscape where your AWS Endpoint Service or AWS MSK cluster should be consumed from:
    -   For Cloud Foundry: A current list of AWS account IDs can be found in [SAP for Me Systems & Provisioning](https://me.sap.com/systemsprovisioning/connectivity).

    -   For Kyma environment: Create PLS service instance and error log will show up with AWS account ID information in it.

3.  **Only for AWS Endpoint Service**: For each AWS Account ID, click *Add Principal* and enter the ARN in form of "arn:aws:iam::<SAP BTP AWS account ID from step 2\>:root". Click *Allow principals*.
4.  **Only for AWS MSK cluster**: Modify your cluster policy with provided json below:
    -   For each AWS account ID, enter the ARN in form of *arn:aws:iam::<SAP BTP AWS account ID from step 2\>:root*

    -   For AWS MSK cluster ARN, enter at Resource property.
    -   Provided actions under **Action** property are minimum to be created PLS service instance.
    -   Click *Save Changes*.


> ### Sample Code:  
> ```
> {
>     "Version": "2012-10-17",
>     "Statement": [
>         {
>             "Effect": "Allow",
>             "Principal": {
>                 "AWS": [
>                     "arn:aws:iam::1111122222:root",
>                     "arn:aws:iam::3333344444:root"
>                 ]
>             },
>             "Action": [
>                 "kafka:DescribeCluster",
>                 "kafka:DescribeClusterV2",
>                 "kafka:CreateVpcConnection",
>                 "kafka:GetBootstrapBrokers"
>             ],
>             "Resource": "arn:aws:kafka:us-east-1:66666666:cluster/demo/d5a31672-0b23-4tb5-va36-f4c38665af7c-1"
>         }
>     ]
> }
> ```

Find the SAP BTP AWS Account IDs for the landscape where your Endpoint Service should be consumed from. A current list of account IDs can be found in [SAP for Me Systems & Provisioning](https://me.sap.com/systemsprovisioning/connectivity).

With this protection in place, only the approved SAP BTP cockpit accounts can create approval requests to your AWS Endpoint Service in the first place.

You still need to make sure you follow the steps below to only approve benign requests from within SAP BTP cockpit:



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

