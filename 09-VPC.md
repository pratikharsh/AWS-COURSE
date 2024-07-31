# VPC (Virtual Private Cloud) Overview

- **Definition**: 
  - A VPC is a virtual network in the cloud, providing a private, secure, and isolated area for applications and data.

- **Purpose**: 
  - Offers a private section of the internet, akin to having your own network within a larger network.
 
    ![image](https://github.com/user-attachments/assets/56bbfc5f-8d6d-4084-9488-afa4971d3be0)

## VPC Components

### 1. Virtual Private Clouds (VPC) 🌐
   - Resembles a traditional network.
   - Allows adding subnets.

### 2. Subnets 🌍
   - Range of IP addresses in a VPC.
   - Resides in a single Availability Zone.
   - Hosts AWS resources.

### 3. IP Addressing 🆔
   - Supports IPv4 and IPv6.
   - Allows bringing public IP addresses to AWS for use in VPC resources.

### 4. Network Access Control List (NACL) 🛡️
   - Stateless firewall controlling traffic at the subnet level.
   - Operates at the IP address level.
   - Allows or denies traffic based on rules.

### 5. Security Group 🔒
   - Acts as a virtual firewall for instances.
   - Controls traffic at the instance level.
   - Defines rules for protocols, ports, and IP addresses.

### 6. Routing 🛣️
   - Uses route tables to direct network traffic.

### 7. Gateways and Endpoints 🚪
   - Internet Gateway: Connects VPC to the internet.
   - VPC Endpoint: Connects to AWS services privately.

### 8. Peering Connections 🔗
   - Routes traffic between two VPCs.

### 9. Traffic Mirroring 📡
   - Copies network traffic for deep packet inspection.

### 10. Transit Gateways 🛤️
    - Acts as a central hub for routing traffic between VPCs, VPNs, and AWS Direct Connect.

### 11. VPC Flow Logs 📊
    - Captures information about IP traffic.

### 12. VPN Connections 🔌
    - Connects VPCs to on-premises networks.

## Additional Information

- **Default VPC**: 
  - Created by AWS for initial use.
  - Recommended to create custom VPCs for specific applications or projects.

## Resources

- **Example Setup**: 
  - VPC with servers in private subnets and NAT.
  - [AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-example-private-subnets-nat.html)

![image](https://github.com/user-attachments/assets/90c8aa3d-e29a-4a19-b467-a5f85c79bef9)

