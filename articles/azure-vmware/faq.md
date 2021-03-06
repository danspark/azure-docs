---
title: Frequently asked questions
description: Provides answers to some of the common questions about Azure VMware Solution.
ms.topic: conceptual
ms.date:  12/22/2020
---

# Frequently asked questions about Azure VMware Solution

In this article, we'll answer frequently asked questions about Azure VMware Solution.

## General

#### What is Azure VMware Solution?

As enterprises pursue IT modernization strategies to improve business agility, reduce costs, and accelerate innovation, hybrid cloud platforms have emerged as key enablers of customers' digital transformation. Azure VMware Solution combines VMware's Software-Defined Data Center (SDDC) software with Microsoft's Azure global cloud service ecosystem. Azure VMware Solution is managed to meet performance, availability, security, and compliance requirements.

## Azure VMware Solution Service

#### Where is Azure VMware Solution available today?

The service is continuously being added to new regions, so view the [latest service availability information](https://azure.microsoft.com/global-infrastructure/services/?products=azure-vmware) for more details. 

#### Can workloads running in an Azure VMware Solution instance consume or integrate with Azure services?

All Azure services will be available to Azure VMware Solution customers. Performance and availability limitations for specific services will need to be addressed on a case-by-case basis.

#### Do I use the same tools that I use now to manage private cloud resources?

Yes. The Azure portal is used for deployment and several management operations. vCenter and NSX Manager are used to manage vSphere and NSX-T resources.

#### Can I manage a private cloud with my on-premises vCenter?

At launch, Azure VMware Solution won't support a single management experience across on-premises and private cloud environments. Private cloud clusters will be managed with vCenter and NSX Manager local to a private cloud.

#### Can I use vRealize Suite running on-premises? 

Specific integrations and use cases may be evaluated on a case-by-case basis.

#### Can I migrate vSphere VMs from on-premises environments to Azure VMware Solution private clouds?

Yes. VM migration and vMotion can be used to move VMs to a private cloud if standard cross vCenter [vMotion requirements](https://kb.vmware.com/s/article/2106952?lang=en_US&queryTerm=2106952) are met.

#### Is a specific version of vSphere required in on-premises environments?

All cloud environments come with VMware HCX, vSphere 5.5, or later in on-premises environments for vMotion.

#### What does the change control process look like?

Updates made to the service itself follows Microsoft Azure's standard change management process. Customers are responsible for any workload administration tasks and the associated change management processes.

#### How is this different from Azure VMware Solution by CloudSimple?

With the new Azure VMware Solution, Microsoft and VMware have a direct cloud provider partnership. The new solution is entirely designed, built, and supported by Microsoft, and endorsed by VMware. Architecturally, the solutions are consistent, with the VMware technology stack running on a dedicated Azure infrastructure.

#### Can Azure VMware Solution VMs be managed by VMRC?
Yes. Provided the system it's installed on can access the private cloud vCenter and is using public DNS to resolve ESXi hostnames.

#### Are there special instructions for installing and using VMRC with Azure VMware Solution VMs?
No. To meet the VM prerequisites follow the [instructions provided by VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-89E7E8F0-DB2B-437F-8F70-BA34C505053F.html). 

#### Is VMware HCX supported on VPNs?
No, because of bandwidth and latency requirements.

#### Can Azure Bastion be used for connecting to Azure VMware Solution VMs?
Azure Bastion is the service recommended to connect to the jump box to prevent exposing Azure VMware Solution to the internet. You can't use Azure Bastion to connect to Azure VMware Solution VMs since they aren't Azure IaaS objects.

#### Can Azure Load Balancer internal be used for Azure VMware Solution VMs?
No. Azure Load Balancer internal-only supports Azure IaaS VMs. Azure Load Balancer doesn't support IP-based backend pools; only Azure VMs or virtual machine scale set objects in which Azure VMware Solution VMs aren't Azure objects.

#### Can an existing ExpressRoute Gateway be used to connect to Azure VMware Solution?
Yes. Use an existing ExpressRoute Gateway to connect to Azure VMware Solution as long as it doesn't exceed the limit of four ExpressRoute circuits per virtual network. To access Azure VMware Solution from on-premises through ExpressRoute, you must have ExpressRoute Global Reach since the ExpressRoute Gateway doesn't provide transitive routing between its connected circuits.

## Compute, network, storage, and backup

#### Is there more than one type of host available?

There's only one type of host available.

#### What are the CPU specifications in each type of host?

The servers have dual 18 core 2.3 GHz Intel CPUs.

#### How much memory is in each host?

The servers have 576 GB of RAM.

#### What is the storage capacity of each host?

Each ESXi host has two vSAN diskgroups with a capacity tier of 15.2 TB and a 3.2-TB NVMe cache tier (1.6 TB in each diskgroup).

#### How much network bandwidth is available in each ESXi host?

Each ESXi host in Azure VMware Solution is configured with four 25-Gbps NICs, two NICs provisioned for ESXi system traffic, and two NICs provisioned for workload traffic. 

#### Is data stored on the vSAN datastores encrypted at rest?

Yes, all vSAN data is encrypted by default using keys stored in Azure Key Vault.

####  What independent software vendors (ISVs) backup solutions work with Azure VMware Solution?

Commvault, Veritas, and Veeam have extended their backup solutions to work with Azure VMware Solution.  However, any backup solution that uses VMware VADP with the HotAdd transport mode would work right out of the box on Azure VMware Solution.

#### What about support for ISV backup solutions?

As these backup solutions are installed and managed by customers, they can reach out to the respective ISV for support. 

#### What is the correct storage policy for the dedupe setup?

Use the *thin_provision* storage policy for your VM template.  The default is *thick_provision*.

#### Are the SNMP infrastructure logs shared?

No.

## Hosts, clusters, and private clouds

#### Is the underlying infrastructure shared?

No, private cloud hosts and clusters are dedicated and securely erased before and after use.

#### What are the minimum and maximum number of hosts per cluster?

Clusters can scale between 3 and 16 ESXi hosts. Trial clusters are limited to three hosts.

#### Can I scale my private cloud clusters?

Yes, clusters scale between the minimum and the maximum number of ESXi hosts. Trial clusters are limited to three hosts.

#### What are trial clusters?

Trial clusters are three host clusters used for one-month evaluations of Azure VMware Solution private clouds.

#### Can I use High-end hosts for trial clusters?

No. High-end ESXi hosts are reserved for use in production clusters.

## Azure VMware Solution and VMware software

#### What versions of VMware software is used in private clouds?

Private clouds use vSphere 6.7 U3, vSAN 6.7 U3, VMware HCX, and NSX-T 2.5.  For more information, see [the VMware software version requirements](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-54E5293B-8707-4D29-BFE8-EE63539CC49B.html).

#### Do private clouds use VMware NSX?

Yes, NSX-T 2.5 is used for the software-defined networking in Azure VMware Solution private clouds.

#### Can I use VMware NSX-V in a private cloud?

No. NSX-T is the only supported version of NSX.

#### Is NSX required in on-premises environments or networks that connect to a private cloud?

No, you aren't required to use NSX on-premises.

#### What is the upgrade and update schedule for VMware software in a private cloud?

The private cloud software bundle upgrades keep the software within one version of the most recent software bundle release from VMware. The private cloud software versions may differ from the most recent versions of the individual software components (ESXi, NSX-T, vCenter, vSAN).

#### How often will the private cloud software stack be updated?

The private cloud software is upgraded on a schedule that tracks the software bundle's release from VMware. Your private cloud doesn't require downtime for upgrades.

## Connectivity

#### What network IP address planning is required to incorporate private clouds with on-premises environments?

A private network /22 address space is required to deploy an Azure VMware Solution private cloud. This private address space shouldn't overlap with other virtual networks in a subscription or with on-premises networks.
 
#### How do I connect from on-premises environments to an Azure VMware Solution private cloud?

You can connect to the service in one of two methods: 

- With a VM or application gateway deployed on an Azure virtual network that is peered through ExpressRoute to the private cloud.
- Through ExpressRoute Global Reach from your on-premises data center to an Azure ExpressRoute circuit.

#### How do I connect a workload VM to the internet or an Azure service endpoint?

In the Azure portal, enable internet connectivity for a private cloud. With NSX-T manager, create an NSX-T T1 router and a logical switch. You then use vCenter to deploy a VM on the network segment defined by the logical switch. That VM will have network access to the internet and Azure services.

#### Do I need to restrict access from the internet to VMs on logical networks in a private cloud?

No. Network traffic inbound from the internet directly to private clouds isn't allowed by default.  However, you're able to expose Azure VMware Solution VMs to the internet through the [Public IP](public-ip-usage.md) option in your Azure portal for your Azure VMware Solution private cloud.

#### Do I need to restrict internet access from VMs on logical networks to the internet?

Yes. You'll need to use NSX-T manager to create a firewall to restrict VM access to the internet.


#### Can Azure VMware Solution use Azure Virtual WAN hosted ExpressRoute Gateways?
Yes.

#### Can transit connectivity be established between on-premises and Azure VMware Solution through Azure Virtual WAN over ExpressRoute Global Reach?
Azure Virtual WAN doesn't provide transitive routing between two connected ExpressRoute circuits and non-virtual WAN ExpressRoute Gateway. Using ExpressRoute Global Reach allows connectivity between on-premises and Azure VMware Solution, but goes through Microsoft's global network instead of the Virtual WAN Hub.


## Accounts and privileges

#### What accounts and privileges will I get with my new Azure VMware Solution private cloud?

You're provided credentials for a cloudadmin user in vCenter and admin access on NSX-T Manager. There's also a CloudAdmin group that can be used to incorporate Azure Active Directory. For more information, see [Access and Identity Concepts](concepts-identity.md).

#### Can have administrator access to ESXi hosts?

No, administrator access to ESXi is restricted to meet the security requirements of the solution.

#### What privileges and permissions will I have in vCenter?

You'll have CloudAdmin group privileges. For more information, see [Access and Identity Concepts](concepts-identity.md).

#### What privileges and permissions will I have on the NSX-T manager?

You'll have full administrator privileges on NSX-T and can manage vSphere role-based access control as you would with NSX-T Data Center on-premises. For more information, see [Access and Identity Concepts](concepts-identity.md).

> [!NOTE]
> A T0 router is created and configured as part of a private cloud deployment. Any modification to that logical router or the NSX-T edge node VMs could affect connectivity to your private cloud.

## Billing and Support

#### How will pricing be structured for Azure VMware Solution?

For general questions on pricing, see the Azure VMware Solution [pricing](https://azure.microsoft.com/pricing/details/azure-vmware) page. 

#### Can Azure VMware Solution be purchased through a Microsoft CSP?

Yes, customers can deploy Azure VMware Solution within an Azure subscription managed by a CSP.

#### Who supports Azure VMware Solution?

Microsoft delivers support for Azure VMware Solution. You can submit a [support request](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest). 

For CSP-managed subscriptions, the first level of support provides the Solution Provider in the same fashion as CSP does for other Azure services.

#### What accounts do I need to create an Azure VMware Solution private cloud?

You'll need an Azure account in an Azure subscription.

#### Are Red Hat solutions supported on Azure VMware Solution?

Microsoft and Red Hat share an integrated, colocated support team that provides a unified contact point for Red Hat ecosystems running on the Azure platform.  Like other Azure platform services that work with Red Hat Enterprise Linux, Azure VMware Solution falls under the Cloud Access and integrated support umbrella. Red Hat Enterprise Linux is supported for running on top of Azure VMware Solution within Azure.

#### Is VMware HCX Enterprise available, and if so, how much does it cost?

VMware HCX Enterprise is available with Azure VMware Solution as a *Preview* function/service. While VMware HCX Enterprise for Azure VMware Solution is in Preview, it's a free function/service and subject to Preview service terms and conditions. Once the VMware HCX Enterprise service goes GA, you'll get a 30-day notice that billing will switch over. You can switch it off or opt-out of the service.

#### How do I request a host quota increase for Azure VMware Solution?

For CSP-managed subscriptions, the customer must submit the request to the partner. The partner team then engages with Microsoft to get the quota increased for the subscription. See [How to enable Azure VMware Solution resource article](enable-azure-vmware-solution.md) for the details. 

For EA subscriptions, use the following procedure. First, you'll need:

* An [Azure Enterprise Agreement (EA)](../cost-management-billing/manage/ea-portal-agreements.md) with Microsoft.
* An Azure account in an Azure subscription.

Before you can create your Azure VMware Solution resource, you'll submit a support ticket to have your hosts allocated. It takes up to five business days to confirm and fulfill your request. If you have an existing Azure VMware Solution private cloud and want more hosts allocated, you'll go through the same process.

1. In your Azure portal, under **Help + Support**, create a **[New support request](https://rc.portal.azure.com/#create/Microsoft.Support)** and provide the following information for the ticket:
   - **Issue type:** Technical
   - **Subscription:** Select your subscription
   - **Service:** All services > Azure VMware Solution
   - **Resource:** General question 
   - **Summary:** Need capacity
   - **Problem type:** Capacity Management Issues
   - **Problem subtype:** Customer Request for Additional Host Quota/Capacity

1. In the **Description** of the support ticket, on the **Details** tab, provide:

   - POC or Production 
   - Region Name
   - Number of hosts
   - Any other details

   >[!NOTE]
   >Azure VMware Solution recommends a minimum of three hosts to spin up your private cloud and for redundancy N+1 hosts. 

1. Select **Review + Create** to submit the request.

   It will take up to five business days for a support representative to confirm your request.

   >[!IMPORTANT] 
   >If you already have an existing Azure VMware Solution and request additional hosts, please note that we need five business days to allocate the hosts. 

1. Before you can provision your hosts, make sure that you register the **Microsoft.AVS** resource provider in the Azure portal.  

   ```azurecli-interactive
   az provider register -n Microsoft.AVS --subscription <your subscription ID>
   ```

   For more ways to register the resource provider, see [Azure resource providers and types](../azure-resource-manager/management/resource-providers-and-types.md). 

#### Are Reserved Instances available for purchasing through the Cloud Solution Provider (CSP) program?

Yes. CSP can purchase reserved instances for their customers. For more information, see [Save costs with a reserved instance](reserved-instance.md). 

#### Does Azure VMware Solution offer multi-tenancy for hosting CSP partners?

No. Currently, Azure VMware Solution doesn't offer multi-tenancy.

#### Will traffic between on-premises and Azure VMware Solution over ExpressRoute incur any outbound data transfer charge in the metered data plan?

Traffic in the Azure VMware Solution ExpressRoute circuit isn't metered in any way. Traffic from your ExpressRoute circuit connecting to your on-premises to Azure is charged according to ExpressRoute pricing plans.


## Customer communication

#### How can I receive an alert when Azure sends service health notifications to my Azure subscription?

Service issues, planned maintenance, health advisories, security advisories notifications are published through **Service Health** in the Azure portal.  You can take timely actions when you set up activity log alerts for these notifications. For more information, see [Create service health alerts using the Azure portal](../service-health/alerts-activity-log-service-notifications-portal.md#create-service-health-alert-using-azure-portal).

:::image type="content" source="media/service-health.png" alt-text="Screenshot of Service Health notifications":::



<!-- LINKS - external -->
[kb2106952]: https://kb.vmware.com/s/article/2106952?lang=en_US&queryTerm=21069522

<!-- LINKS - internal -->
[Access and Identity Concepts]: concepts-identity.md
