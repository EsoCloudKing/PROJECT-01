# PROJECT NAME
 
 **Implementing a Secure Hub-and-Spoke Virtual Network Architecture Design for Cloud and On-Premises Environment**.
 
 ## Objective
  To demonstrate and examine how a hub-and-spoke Network topology can be used to secure communications between multiple cloud (Azure) workloads and hybrid environment. The primary focus of this project was to Design a highly secure, scalable Hub and Spoke Virtual network and effect cost effective Network security using key principles like network segmentation and isolation, VPN, inter-cloud traffic encryption, firewall, NSGs, VPN-Gateways.

  ## Skills Learned
  - Advanced understanding of Virtual Network Security concepts and their practical application.
  - Proficiency in provisioning and securing Virtual Network using variety of cyber and cloud security concepts and principles.
  - Enhanced knowledge for provision and using Azure Network resources (Nsg, Azure firewall, Azure Bastion, VPN-Gateway, Application Gateway, and DDOS Protection).
  - Improved understanding of network protocols and security vulnerabilities.
  - Development of critical thinking and problem-solving skills in cyber security.

  ### Tools Used For this Project
- Microsoft Visio for diagram mapping.
- Azure CLI Command for provisioning of  Virtual network resources.
- Azure Virtual Network Manager for creating Vnet groups and hub and spoke topology.
- ARM Templates for provisioning of some resources.

 ## Steps
- **Step 1** : Gathering of vital Information and requirements

Before starting this project it was very important to answer some important questions and requirements. This will enable proper management of subletting, IP planning and cost optimization.

Some questions that needed to be asked were as follows; how many devices will go into the network present and future? Will there be an expansion in the future? How many subnets will the digital estate need? Will all subnets be the same size? Depending on the services running on the infrastructure, which devices need to be isolated?
Finding solid answers to the above these questions, paved way for **step 2 below**.

- **Step 2** : Mapping a diagram

*Ref Diagram 1: Hub & Spoke Network Diagram*
   ![Vnet hub and spoke](https://github.com/user-attachments/assets/a1906da8-0ecf-46c2-a355-2c7d0db02591)

- **Step 3** : Virtual Network manager was provisioned. This will be used later, to manage VNets and create a hub and spoke topology.

- **Step 4** : With Azure CLI, all Virtual networks were created with single subnets with proper IP addressing and allocation as shown in diagram 2 below.  Other needed subnets were later added to the Vnets via the azure portal respectively :

*Ref Diagram 2: Hub & Spoke Network Diagram*
![CLI Vnets Creation](https://github.com/user-attachments/assets/61f117c0-2663-49c6-a576-5b5905a353a0)

- **Step 5** : Virtual network manager was used to group Vnets, create a Hub and spoke topology structure, as depicted in diagram 1 above.
 Effective **Network security groups (NSG)** were created and placed on appropriate subnets for more granular control of traffic flow, in and out of respective subnets and appliances.

*Ref Diagram 3: SPOKES PEERED WITH HUB*
![NETWORK MANAGER](https://github.com/user-attachments/assets/9601d983-b1cd-47e3-8861-f30e63b7922f)

 Effective Network security groups (NSG) were created and placed on appropriate subnets for more granular control of traffic flow in and out of respective subnets and appliances.

To round up this project, here are some key highlight about the secured hub and spoke virtual network topology below;

*Ref Diagram 3: Hub and Spoke architecture*
![Vnet hub and spoke](https://github.com/user-attachments/assets/1f3dc0d9-d86f-4664-8b84-b2aabd784f61)

**-Hub-Vnet (10.0.0.0/16):** This is the Vnet hosting the spoke networks with bi-directional peering.  Azure Bastion have its subnet for secure RDP/SSH connection to Virtual machines. For load balancing and WAF, Application Gateway was provisioned to balance load for the App-Vnet with a scale set, hosting some important App services. VPN gateway will be deployed to its own subnet to enable cross premises connection. For any “work from home staff”, point-to-site VPN can be configured. 

**-Admin-Vnet (10.1.0.0/16):** The requirement for this Vnet was simple because it will host work Virtual machines. It’s a spoke to the hub with two-way connection to the hub and the Marketing/sales-Vnet. Which means the resources in this Vnet can be assessed by the Hub-Vnet, Spoke2 Vnet and vice-versa.
For traffic inspection, Next hop Network Virtual Appliance (NVA) will be provisioned on a subnet in this Vnet, with a Route table configured (UDR) to direct traffic through the appliance before reaching the work Vms .

**-Marketing/Sales-Vnet (10.4.0.0/16)**: This Vnet has two subnets which will host some Vms and a sales app. The app will assess some resources from the general services-Vnet , so this vnet is peered directy with the admin and Gen-services Vnet to communicate in both ways. 

**-App-Vnet (10.2.0.0/16):** with a single subnet of 255 IPs (10.4.0.0/24), it has Virtual machine scale set hosting some critical apps. It is a spoke to the hub and only peered to communicate with the Gen-services Vnet one way to assess resources from the vnet.
An application Gateway on the hub will distribute load to this scale sets back pool in this network.

**-General services-Vnet (10.3.0.0/16):** This network will be used as service endpoints for some vital services like Azure Key vault, SQL databases, storage services which will need to be assessed securely by some other Vnet Spokes. Each service points use a separate subnet with constricted Ip range to assess these services.

In addition to all the above, **Network Security Group (NSGs)** was configured to deny or allow traffic to and from some subnets, according the requirement of each departments.

The **Azure monitor** will collect diagnostics, from diagnostics enabled Azure bastion, Azure firewall and App-Gateway to monitor health and performance of this resources.

