# Hybrid Enterprise Lab

A connected enterprise lab built from bare metal. Each project depends on the previous one working correctly, the same way real enterprise infrastructure does. Nothing here is isolated or self-contained.

Built on Rocky Linux 9.7 with VirtualBox. Five VMs across two isolated subnets, routed through an Ubuntu gateway, with a hybrid identity stack connecting on-premises Active Directory to Azure.

## Projects

### Complete

- [Project 1: Linux Enterprise Gateway](https://github.com/mansour-wade/Linux-Enterprise-Gateway)  
  Ubuntu Server configured as a NAT router and stateful firewall. Handles routing for Rocky Linux and Fedora clients across an isolated internal network.

- [Project 2: Active Directory Domain Controller](https://github.com/mansour-wade/Active-Directory-Domain-Controller)  
  Windows Server 2022 promoted to Domain Controller on an isolated server subnet. DNS, OU structure, privileged account management, and stateful inter-subnet routing controlled by iptables.

### In Progress

- Project 3: User Management and GPOs  
  Active Directory users and OUs across Sales, IT, and HR. Four Group Policy Objects including password policy, desktop lockdown, drive mapping, and endpoint ICMP controls.

- Project 4: Domain Join  
  Rocky Linux, Fedora, and Windows 11 joined to lab.local using SSSD and Realmd. Live tcpdump packet capture during domain join showing Kerberos, LDAP, and DNS traffic.

- Project 5: RDS Web Access Portal  
  Browser-based remote desktop portal tied to Active Directory. Requires domain users from Project 3 and a joined Windows 11 client from Project 4.

- Project 6: Azure Entra Connect and Squid Proxy  
  On-premises AD synced to Azure Entra ID. Subnet-aware Squid proxy with different outbound rules for the server subnet and the client subnet.

## Lab Environment

| VM | Role | IP |
| :--- | :--- | :--- |
| Ubuntu Server | Gateway and Firewall | 10.0.1.1 / 10.0.3.1 |
| Rocky Linux | Lab Client | 10.0.1.2 |
| Fedora | Lab Client | 10.0.1.3 |
| Windows 11 | Domain Client | 10.0.1.4 |
| Windows Server 2022 | Domain Controller | 10.0.3.10 |

## Repos

- [github.com/mansour-wade/Linux-Enterprise-Gateway](https://github.com/mansour-wade/Linux-Enterprise-Gateway)
- [github.com/mansour-wade/Active-Directory-Domain-Controller](https://github.com/mansour-wade/Active-Directory-Domain-Controller)
