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

In conclusison, NSGs was configured and attached to some subnets for effective traffic control.



