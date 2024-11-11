<!-- loio67e4c7377a0f4154a3cf0e7034d71b5a -->

# Supported Services for Amazon Web Services in SAP BTP

The following AWS services can be consumed from SAP BTP via SAP Private Link Service.

The Creation Request Configuration Parameters column describes AWS service-specific configuration parameters for a SAP Private Link service instance creation.

The Binding Credentials Attributes column describes AWS service-specific binding credentials.



**Regions for Enterprise Accounts**


<table>
<tr>
<th valign="top">

Service

</th>
<th valign="top">

Creation Request Configuration Parameters

</th>
<th valign="top">

Binding Credentials Attributes

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

VPC Endpoint Service

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.vpce.us-east-1.vpce-svc-018072c5ac6df60dd",
>   "desiredAZs": 2
> }
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>   ...
>   "privatelink": [
>     {
>       ...
>       "credentials": {
>         "hostname": "vpce-00000000000000000-00000000.vpce-svc-00000000000000000.us-east-1.vpce.amazonaws.com"
>       }
>     }
>   ]
> }
> ```



</td>
<td valign="top">

-   [Transport Layer Security Amazon Web Services](transport-layer-security-amazon-web-services-9f07803.md)
-   [Share your services through AWS PrivateLink](https://docs.aws.amazon.com/vpc/latest/privatelink/privatelink-share-your-services.html)



</td>
</tr>
<tr>
<td valign="top">

Amazon Simple Storage Service \(S3\)

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> 
> {
>   "serviceName": "com.amazonaws.us-east-1.s3",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Principal": "*",
>         "Action": [
>           "s3:Get*",
>           "s3:List*"
>         ],
>         "Effect": "Allow",
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>   ...
>   "privatelink": [
>     {
>       ...
>       "credentials": {
>         "hostname": "*.vpce-068c84244a1b70734-r9rznuj8.s3.us-east-1.vpce.amazonaws.com"
>       }
>     }
>   ]
> }
> ```



</td>
<td valign="top">

-   [Amazon Simple Storage Service \(S3\) PrivateLink Sample App](https://github.com/SAP-samples/private-link-aws-services/tree/main/s3)
-   [AWS PrivateLink for Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/privatelink-interface-endpoints.html)



</td>
</tr>
<tr>
<td valign="top">

Amazon Simple Email Service \(SES\)

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.email-smtp",
>   "desiredAZs": 2
> }
> 
> 
> 
> 
> 
> 
> 
> 
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>   ...
>   "privatelink": [
>     {
>       ...
>       "credentials": {
>         "hostname": "vpce-00000000000000000-00000000.email-smtp.us-east-1.vpce.amazonaws.com"
>       }
>     }
>   ]
> }
> ```



</td>
<td valign="top">

-   [AWS SES PrivateLink Sample App](https://github.com/SAP-samples/private-link-aws-services/tree/main/ses)

-   [Setting up VPC endpoints with Amazon SES](https://docs.aws.amazon.com/ses/latest/dg/send-email-set-up-vpc-endpoints.html)



</td>
</tr>
<tr>
<td valign="top">

Amazon Simple Queue Service \(SQS\)

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.sqs",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": {
>                   "AWS": "arn:aws:iam:123456789012:user/MyUser"
>               },
>               "Action": [
>                   "sqs:SendMessage"
>               ],
>               "Effect": "Allow",
>               "Resource": "arn:aws:sqs:us-east-2:123456789012:MyQueue"
>           }]
>     }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.sqs.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS SQS PrivateLink Sample App](https://github.com/SAP-samples/private-link-aws-services/tree/main/sqs)

-   [https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-internetwork-traffic-privacy.html\#sqs-vpc-endpoints](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-internetwork-traffic-privacy.html#sqs-vpc-endpoints)



</td>
</tr>
<tr>
<td valign="top">

Amazon Simple Notification Service \(SNS\)

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> 
> {
>     "serviceName": "com.amazonaws.us-east-1.sns",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": {
>                   "AWS": "arn:aws:iam:123456789012:user/MyUser"
>               },
>               "Action": [
>                   "sns:Publish"
>               ],
>               "Effect": "Allow",
>               "Resource": "arn:aws:sns:us-east-2:123456789012:MyTopic"
>           }]
>     }
> }Creating an Amazon VPC
> 											endpoint policy for Amazon SQS
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> Creating an Amazon VPC{
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.sns.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS SNS PrivateLink Sample App](https://github.com/SAP-samples/private-link-aws-services/tree/main/sns)

-   [Internetwork traffic privacy](https://docs.aws.amazon.com/sns/latest/dg/sns-internetwork-traffic-privacy.html)



</td>
</tr>
<tr>
<td valign="top">

Amazon Relational Database Service \(RDS\) - Aurora Data API

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.rds-data",
>     "policyDocument": {
>           "Statement": [{
>               "Principal": "*",
>               "Action": [
>                   "rds-data:BatchExecuteStatement",
>                   "rds-data:BeginTransaction",
>                   "rds-data:CommitTransaction",
>                   "rds-data:ExecuteStatement",
>                   "rds-data:RollbackTransaction"
>               ],
>               "Effect": "Allow",
>               "Resource": "*"
>           }]
>     }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.rds-data.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS RDS Data API PrivateLink Sample App](https://github.com/SAP-samples/private-link-aws-services/tree/main/rds-data#aws-rds-data-api-privatelink-sample-app)

-   [Creating an Amazon VPC endpoint for the Data API \(AWS PrivateLink\)](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/data-api.html#data-api.vpc-endpoint)



</td>
</tr>
<tr>
<td valign="top">

AWS Lambda

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.lambda",
>     "policyDocument": {
>         "Statement": [
>             {
>                 "Principal": "*",
>                 "Action": [
>                     "lambda:InvokeFunction"
>                 ],
>                 "Effect": "Allow",
>                 "Resource": "arn:aws:lambda:us-east-1:123456789012:function:myFunction"
>             }
>         ]
>     }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.lambda.us-east-1.vpce.amazonaws.com"
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS Lambda PrivateLink Sample App](https://github.com/SAP-samples/private-link-aws-services/tree/main/lambda#aws-lambda-privatelink-sample-app)

-   [Connecting inbound interface VPC endpoints for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc-endpoints.html)



</td>
</tr>
<tr>
<td valign="top">

AWS Key Management Service

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.kms",
>     "policyDocument": {
>         "Statement": [
>             {
>                 "Principal": "*",
>                 "Action": [
>                     "kms:Decrypt",
>                     "kms:DescribeKey", 
>                     "kms:ListAliases",
>                     "kms:ListKeys"
>                 ],
>                 "Effect": "Allow",
>                 "Resource": "*"
>             }
>         ]
>     }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>      ...
>      "privatelink": [
>          {
>              ...
>              "credentials": {
>                  "hostname": "vpce-00000000000000000-00000000.kms.us-east-1.vpce.amazonaws.com"
>              }
>          }
>      ]
>  }
> ```



</td>
<td valign="top">

-   [Connecting to AWS KMS through a VPC endpoint](https://docs.aws.amazon.com/kms/latest/developerguide/kms-vpc-endpoint.html)




</td>
</tr>
<tr>
<td valign="top">

AWS IoT Core

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> ```
> {
>     "serviceName": "com.amazonaws.us-east-1.iot.data",
>     "desiredAZs": 2
> }
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

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



</td>
<td valign="top">

[Using AWS IoT Core with interface VPC endpoints](https://docs.aws.amazon.com/iot/latest/developerguide/IoTCore-VPC.html)

</td>
</tr>
<tr>
<td valign="top">

AWS Elastic Beanstalk

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.elasticbeanstalk",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Action": "*",
>         "Effect": "Allow",
>         "Resource": "*",
>         "Principal": "*"
>       },
>       {
>         "Action": "elasticbeanstalk:TerminateEnvironment",
>         "Effect": "Deny",
>         "Resource": "*",
>         "Principal": "*"
>       }
>     ]
>   }
> }
> ```

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.elasticbeanstalk-health",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Action": "*",
>         "Effect": "Allow",
>         "Resource": "*",
>         "Principal": "*"
>       },
>       {
>         "Action": "elasticbeanstalk:TerminateEnvironment",
>         "Effect": "Deny",
>         "Resource": "*",
>         "Principal": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.elasticbeanstalk.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.elasticbeanstalk-health.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Using Elastic Beanstalk with VPC endpoints](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/vpc-vpce.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon ElastiCache

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> 
> {
>   "serviceName": "com.amazonaws.us-east-1.elasticache",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Principal": "*",
>         "Effect": "Allow",
>         "Action": [
>           "elasticache:CreateCacheCluster",
>           "elasticache:ModifyCacheCluster",
>           "elasticache:CreateSnapshot"
>         ],
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.elasticache.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Amazon ElastiCache API and interface VPC endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/elasticache-privatelink.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon Cloud Directory

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.clouddirectory",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Sid": "ReadOnly",
>         "Principal": "*",
>         "Action": [
>           "clouddirectory:ListDirectories"
>         ],
>         "Effect": "Allow",
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.clouddirectory.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Using Cloud Directory Interface VPC Endpoints](https://docs.aws.amazon.com/clouddirectory/latest/developerguide/getting_started_using_vpc_endpoints.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon Inspector

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.inspector2",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Effect": "Allow",
>         "Action": [
>           "inspector2:CreateFilter",
>           "inspector2:GetMember"
>         ],
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.inspector2.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Amazon Aurora

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.rds",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Principal": "*",
>         "Effect": "Allow",
>         "Action": [
>           "rds:CreateDBInstance",
>           "rds:ModifyDBInstance",
>           "rds:CreateDBSnapshot"
>         ],
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.rds.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Amazon RDS API and interface VPC endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/vpc-interface-endpoints.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon CloudWatch

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> Example 1
> 
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.evidently",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Sid": "PutOnly",
>         "Principal": "*",
>         "Action": [
>           "cloudwatch:PutMetricData"
>         ],
>         "Effect": "Allow",
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```

> ### Sample Code:  
> Example 2
> 
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.evidently-dataplane",
>   "desiredAZs": 2
> }
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```

> ### Sample Code:  
> Example 3
> 
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.rum",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Sid": "PutOnly",
>         "Principal": "*",
>         "Action": [
>           "cloudwatch:PutMetricData"
>         ],
>         "Effect": "Allow",
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```

> ### Sample Code:  
> Example 4
> 
> ```
> 
> {
>   "serviceName": "com.amazonaws.us-east-1.rum-dataplane",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Sid": "PutOnly",
>         "Principal": "*",
>         "Action": [
>           "cloudwatch:PutMetricData"
>         ],
>         "Effect": "Allow",
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```

> ### Sample Code:  
> Example 5
> 
> ```
>         "Action": [
>           "cloudwatch:PutMetricData"
>         ],
>         "Effect": "Allow",
>         "Resource": "*"
>       }
>     ]
>   }
> }
> 									
> 									
> 									
> ```

> ### Sample Code:  
> Example 6
> 
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.synthetics",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Action": [
>           "synthetics:DescribeCanaries",
>           "synthetics:GetCanaryRuns"
>         ],
>         "Effect": "Allow",
>         "Resource": "*",
>         "Principal": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> Example 1
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.evidently.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 2
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.evidently-dataplane.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 3
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.rum.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 4
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.rum-dataplane.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 5
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.monitoring.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 6
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.synthetics.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Using CloudWatch and CloudWatch Synthetics with interface VPC endpoints](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-and-interface-VPC.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon CloudWatch Events

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> ```
>  {
>     "serviceName": "com.amazonaws.us-east-1.events",
>     "desiredAZs": 2
> }
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.events.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Using Amazon EventBridge with Interface VPC Endpoints](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-related-service-vpc.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon CloudWatch Logs

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> ```
> 
>   {
>     "serviceName": "com.amazonaws.us-east-1.logs",
>     "desiredAZs": 2
> }
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.logs.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Using CloudWatch Logs with interface VPC endpoints](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/cloudwatch-logs-and-interface-VPC.html)




</td>
</tr>
<tr>
<td valign="top">

AWS App Mesh

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> Example 1
> 
> ```
>   {
>     "serviceName": "com.amazonaws.us-east-1.appmesh",
>     "desiredAZs": 2
> }
> 
> 
> 
> 
> 
> 									
> 									
> 									
> 									
> 									
> ```

> ### Sample Code:  
> Example 2
> 
> ```
>   {
>     "serviceName": "com.amazonaws.us-east-1.appmesh-envoy-management",
>     "desiredAZs": 2
> }
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> Example 1
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.appmesh.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 2
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.appmesh-envoy-management.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [App Mesh Interface VPC Endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/app-mesh/latest/userguide/vpc-endpoints.html)




</td>
</tr>
<tr>
<td valign="top">

AWS CloudHSM

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.cloudhsmv2",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Principal": "*",
>         "Effect": "Allow",
>         "Action": [
>           "cloudhsm:DescribeBackups",
>           "cloudhsm:DescribeClusters",
>           "cloudhsm:ListTags"
>         ],
>         "Resource": "*"
>       }
>     ]
>   }
> }
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.cloudhsmv2.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS CloudHSM and VPC endpoints](https://docs.aws.amazon.com/cloudhsm/latest/userguide/cloudhsm-vpc-endpoint.html)




</td>
</tr>
<tr>
<td valign="top">

AWS IoT SiteWise

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> Example 1
> 
> ```
> 
>  {
>   "serviceName": "com.amazonaws.us-east-1.iotsitewise.api",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Action": [
>           "iotsitewise:CreateAsset",
>           "iotsitewise:ListGateways",
>           "iotsitewise:ListTagsForResource"
>         ],
>         "Effect": "Allow",
>         "Resource": "arn:aws:iotsitewise:us-west-2:123456789012:asset/a1b2c3d4-5678-90ab-cdef-33333EXAMPLE",
>         "Principal": {
>           "AWS": [
>             "123456789012:user/iotsitewiseadmin"
>           ]
>         }
>       }
>     ]
>   }
> } 
> ```

> ### Sample Code:  
> Example 2
> 
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.iotsitewise.data",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Action": [
>           "iotsitewise:CreateAsset",
>           "iotsitewise:ListGateways",
>           "iotsitewise:ListTagsForResource"
>         ],
>         "Effect": "Allow",
>         "Resource": "arn:aws:iotsitewise:us-west-2:123456789012:asset/a1b2c3d4-5678-90ab-cdef-33333EXAMPLE",
>         "Principal": {
>           "AWS": [
>             "123456789012:user/iotsitewiseadmin"
>           ]
>         }
>       }
>     ]
>   }
> } 
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> Example 1
> 
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.iotsitewise.api.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 2
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.iotsitewise.api.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS IoT SiteWise and interface VPC endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/iot-sitewise/latest/userguide/vpc-interface-endpoints.html)




</td>
</tr>
<tr>
<td valign="top">

AWS IoT Greengrass

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.greengrass",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Principal": "*",
>         "Effect": "Allow",
>         "Action": [
>           "greengrass:CreateDeployment",
>           "greengrass:ListEffectiveDeployments"
>         ],
>         "Resource": "*"
>       }
>     ]
>   }
> }  
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.greengrass.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [AWS IoT Greengrass and interface VPC endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/greengrass/v2/developerguide/vpc-interface-endpoints.html)




</td>
</tr>
<tr>
<td valign="top">

AWS IoT Core for LoRaWAN

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> Example 1
> 
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.iotwireless.api",
>   "desiredAZs": 2
> } 
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```

> ### Sample Code:  
> Example 2
> 
> ```
>  {
>   "serviceName": "com.amazonaws.us-east-1.lorawan.cups",
>   "desiredAZs": 2
> } 
> 									
> 									
> 									
> 									
> 									
> 									
> 									
> ```

> ### Sample Code:  
> Example 3
> 
> ```
>  {
>   "serviceName": "com.amazonaws.us-east-1.lorawan.lns",
>   "desiredAZs": 2
> } 
> 
> 
> 
> 
> 
> 
> 
> 									
> 									
> 									
> 									
> 									
> 									
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> Example 1
> 
> ```
> 
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.iotwireless.api.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 2
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.lorawan.cups.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```

> ### Sample Code:  
> Example 3
> 
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.lorawan.lns.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Connecting to AWS IoT Core for LoRaWAN through a VPC interface endpoint](https://docs.aws.amazon.com/iot/latest/developerguide/connect-iot-lorawan-interface-vpc-endpoint.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon Bedrock

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName) \(required\)
-   [policyDocument](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_policyDocument) \(optional\)

> ### Sample Code:  
> ```
> {
>   "serviceName": "com.amazonaws.us-east-1.bedrock-runtime",
>   "policyDocument": {
>     "Statement": [
>       {
>         "Principal": "*",
>         "Effect": "Allow",
>         "Action": [
>           "bedrock:InvokeModel",
>           "bedrock:InvokeModelWithResponseStream"
>         ],
>         "Resource": "*"
>       }
>     ]
>   }
> } 
> ```



</td>
<td valign="top">

-   [hostname](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_hostname)

> ### Sample Code:  
> ```
> {
>     ...
>     "privatelink": [
>         {
>             ...
>             "credentials": {
>                 "hostname": "vpce-00000000000000000-00000000.bedrock-runtime.us-east-1.vpce.amazonaws.com",
>             }
>         }
>     ]
> }
> ```



</td>
<td valign="top">

-   [Use interface VPC endpoints \(AWS PrivateLink\)](https://docs.aws.amazon.com/bedrock/latest/userguide/vpc-interface-endpoints.html)




</td>
</tr>
<tr>
<td valign="top">

Amazon MSK

</td>
<td valign="top">

-   [serviceName](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_serviceName)

    \(required\)

-   [clusterARN](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_clusterARN)\(required\)
-   [authentication](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_authentication) \(required\)
-   [desiredAZs](supported-services-for-amazon-web-services-in-sap-btp-67e4c73.md#loio67e4c7377a0f4154a3cf0e7034d71b5a__section_desiredAZs) \(optional\)

> ### Sample Code:  
> ```
> 
> {
>     "serviceName": "com.amazonaws.us-east-1.msk",
>     "clusterARN": "arn:aws:kafka:us-east-1:666666666:cluster/demo/d5a31672-0b23-4tb5-va36-f4c38665af7c-1",
>     "authentication": "SASL_SCRAM",
>     "desiredAZs": 3
> }
> ```

**Prerequisite is to allowlist your MSK cluster**:

-   [Best Practices for Secure Endpoint Approval on AWS](../best-practices-for-secure-endpoint-approval-on-aws-e045588.md)




</td>
<td valign="top">

> ### Sample Code:  
> ```
> 
> {
>    ...
>    "privatelink": [
>       {
>          ...
>          "credentials": {
>             "hostname": "b-1.auth.name.abcabc.c1.kafka.region.amazonaws.com:14001,b-2.auth.name.abcabc.c1.kafka.region.amazonaws.com:14002,b-3.auth.name.abcabc.c1.kafka.region.amazonaws.com:14003"   
>          }
>       }
>    ]
> }
> ```



</td>
<td valign="top">

-   Supported in Kyma environment.

-   Amazon MSK multi-VPC private connectivity in a single Region



</td>
</tr>
</table>



<a name="loio67e4c7377a0f4154a3cf0e7034d71b5a__section_gtz_bgc_dzb"/>

## Known Limitations

Only AWS services in the same region as the SAP BTP Cloud Foundry environment are supported. If you want to consume workloads in a different region via Private Link, you can create a dedicated Endpoint Service \(and Network Load Balancer\) in the local region which accesses the workload in the other region via VPC peering. See [Inter-Region Endpoint Services](https://docs.aws.amazon.com/whitepapers/latest/aws-privatelink/use-case-examples.html#inter-region-endpoint-services)



<a name="loio67e4c7377a0f4154a3cf0e7034d71b5a__section_vwx_pvz_gdc"/>

## Known Limitations for Amazon MSK

-   Multi-VPC private connectivity is supported only on Apache Kafka 2.7.1 or higher. Make sure that any clients that you use with the MSK cluster are running Apache Kafka versions that are compatible with the cluster.

-   Multi-VPC private connectivity supports auth types TLS and SASL/SCRAM. Unauthenticated clusters can't use multi-VPC private connectivity.
-   If you are using the SASL/SCRAM or mTLS access-control methods, you must set Apache Kafka ACLs for your cluster. First, set the Apache Kafka ACLs for your cluster. Then, update the cluster's configuration to have the property**allow.everyone.if.no.acl.found** set to **false** for the cluster. For information about how to update the configuration of a cluster, see [Amazon MSK configuration operations](https://docs.aws.amazon.com/msk/latest/developerguide/msk-configuration-operations.html). For more information about Apache Kafka ACLs, see [Apache Kafka ACLs](https://docs.aws.amazon.com/msk/latest/developerguide/msk-acls.html).
-   Multi-VPC private connectivity doesn’t support the **t3.small** instance type.
-   Multi-VPC private connectivity isn’t supported across AWS Regions, only on AWS accounts within the same Region.
-   Amazon MSK doesn't support multi-VPC private connectivity to Zookeeper nodes.



<a name="loio67e4c7377a0f4154a3cf0e7034d71b5a__section_nbm_3gc_dzb"/>

## Binding Credential Attributes

****


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`hostname`

</td>
<td valign="top">

Regional DNS hostname to connect to the AWS interface endpoint.

</td>
</tr>
</table>



<a name="loio67e4c7377a0f4154a3cf0e7034d71b5a__section_rsf_dgc_dzb"/>

## Creation Request Configuration Parameters

****


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`serviceName` \(required\)

</td>
<td valign="top">

The service name on AWS side that uniquely identifies the AWS endpoint service to connect to.

</td>
</tr>
<tr>
<td valign="top">

`desiredAZs`

</td>
<td valign="top">

SAP BTP Cloud Foundry environment runs in three AWS availability zones. By default, SAP Private Link service expects the customer's endpoint service to also run in three availability zones.

This ensures that the connection runs in the highest available fashion possible. If the SAP Private Link service detects that the endpoint service on customer side runs in fewer zones than three,the connection will be rejected unless desiredAZs is set to the number of present availability zones. This is a precautionary measure to ensure that the connection cannot accidentally run with fewer than three zones.

</td>
</tr>
<tr>
<td valign="top">

`policyDocument`

</td>
<td valign="top">

A JSON document specifying a VPC endpoint policy.

</td>
</tr>
<tr>
<td valign="top">

`clusterARN`

</td>
<td valign="top">

Specifies the AWS MSK cluster ARN for which the VPC Connection will be created.

</td>
</tr>
<tr>
<td valign="top">

`authentication`

</td>
<td valign="top">

Specifies the AWS MSK authentication type with which the VPC Connection will be created. Supported types are: "SASL\_SCRAM" and "TLS".

</td>
</tr>
</table>

