<!-- loio3195b1f7174d4ea78e5962c3f2f59131 -->

# Security

Get an overview of the security-relevant information for the SAP Private Link service \(Beta\).

For information on the security features of SAP BTP, see [Security for SAP BTP](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e129aa20c78c4a9fb379b9803b02e5f6.html).



<a name="loio3195b1f7174d4ea78e5962c3f2f59131__section_by1_mnj_1qb"/>

## Security Groups

When a binding between a Cloud Foundry application and a private link service instance is created, SAP Private Link service \(Beta\) creates a space-scoped Cloud Foundry application security group that enables network access to the IP address associated with the private endpoint. For more information, see [App Security Groups](https://docs.cloudfoundry.org/concepts/asg.html).



<a name="loio3195b1f7174d4ea78e5962c3f2f59131__section_nqf_11f_kqb"/>

## Audit and Logging Information

The SAP Private Link service \(Beta\) relies on the audit logging capabilities of the Cloud Foundry environment. For more information, see [Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html).



<a name="loio3195b1f7174d4ea78e5962c3f2f59131__section_izk_l3x_z4b"/>

## Identity and Access Management

The SAP Private Link service \(Beta\) relies on the identity and access management capabilities of the Cloud Foundry environment. To find out how to manage user identities and access in the Cloud Foundry environment, see [SAP Authorization and Trust Management Service in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6373bb7a96114d619bfdfdc6f505d1b9.html).



<a name="loio3195b1f7174d4ea78e5962c3f2f59131__section_v4m_l3x_z4b"/>

## Network and Communication Security

The SAP Private Link service \(Beta\) handles connectivity between SAP BTP customer accounts and customer IaaS services over the backbone network of the partner IaaS provider.



<a name="loio3195b1f7174d4ea78e5962c3f2f59131__section_sy4_l3x_z4b"/>

## Data Protection and Privacy

Governments place legal requirements on industry to protect data and privacy. We provide features and functions to help you meet these requirements.

> ### Note:  
> SAP does not provide legal advice in any form. SAP software supports data protection compliance by providing security features and data protection-relevant functions, such as blocking and deletion of personal data. In many cases, compliance with applicable data protection and privacy laws is not covered by a product feature. Furthermore, this information should not be taken as advice or a recommendation regarding additional features that would be required in specific IT environments. Decisions related to data protection must be made on a case-by-case basis, taking into consideration the given system landscape and the applicable legal requirements. Definitions and other terms used in this documentation are not taken from a specific legal source.

For general information about data protection and privacy on SAP BTP, see the SAP BTP documentation under [Data Protection and Privacy](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/7e513d31704a4a87831191e504ca850a.html).

> ### Caution:  
> The SAP Private Link service \(Beta\) does not provide the technical capabilities to support the collection, processing, and storage of personal data.

