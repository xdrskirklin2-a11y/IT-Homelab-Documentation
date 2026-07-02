# Active Directory Home Lab

## Overview
Built a fully functional Active Directory environment from scratch using Proxmox 
virtualization on a physical machine. Deployed Windows Server 2022 as a domain 
controller and configured a Windows 10 Pro client workstation, simulating a 
real-world enterprise IT environment.

## Environment
| Component | Details |
|-----------|---------|
| Hypervisor | Proxmox VE (physical machine) |
| Domain Controller | Windows Server 2022 |
| Client Machine | Windows 10 Pro |
| Domain Name | homelab.local |
| Server IP | 10.0.x.x (static) |
| Client IP | 10.0.x.x (static) |

## What I Built

### 1. Proxmox Virtualization Environment
- Configured Proxmox VE on physical hardware
- Created and managed virtual machines for server and client
- Configured virtual network bridge (vmbr0) for VM communication
- Took snapshots at each major milestone for rollback capability

### 2. Windows Server 2022 Domain Controller
- Installed Windows Server 2022 from ISO
- Configured static IP addressing
- Installed Active Directory Domain Services (AD DS) role
- Promoted server to domain controller for homelab.local
- Verified domain health using Get-ADDomain and dcdiag

### 3. Active Directory Configuration
- Created Organizational Unit structure:
  - Employees OU — standard user accounts
  - IT Department OU — administrative accounts
  - Workstations OU — computer accounts
- Created and managed user accounts (jsmith, jdoe)
- Created IT admin account (helpdesk) with Domain Admin privileges
- Performed password resets simulating real Tier 1 help desk workflows
- Managed group membership including Domain Admins group

### 4. DNS Configuration
- Configured DNS server role alongside Active Directory
- Created Forward Lookup Zone for homelab.local
- Created Reverse Lookup Zone for 10.0.x.x subnet
- Generated PTR records using ipconfig /registerdns
- Configured DNS forwarders to 8.8.8.8 for internet resolution
- Verified DNS resolution using nslookup and ping

### 5. Client VM Domain Join
- Installed Windows 10 Pro from ISO
- Configured static IP with domain controller as DNS server
- Disabled IPv6 to prevent DNS resolution conflicts
- Successfully joined Windows 10 Pro client to homelab.local
- Verified domain authentication using whoami (homelab\jsmith)
- Moved computer account to Workstations OU

## Skills Demonstrated
- Active Directory Domain Services
- Windows Server 2022 Administration
- DNS Configuration (Forward/Reverse Lookup Zones)
- Proxmox Virtualization
- Domain Controller Deployment
- User Account Management
- Organizational Unit Design
- Group Management
- TCP/IP Networking
- Help Desk Tier 1 Workflows
- Troubleshooting Methodology

## Troubleshooting Experience
During this lab I encountered and resolved several real-world issues:
- Reconfigured static IP after physical network change
- Resolved DNS resolution conflicts caused by IPv6 priority
- Diagnosed and fixed time synchronization issues affecting Kerberos authentication
- Troubleshot domain controller netlogon registration
- Resolved VM network bridge configuration issues

## Screenshots
See screenshots folder for visual documentation of each step.

## Tools Used
- Proxmox VE
- Windows Server 2022
- Windows 10 Pro
- Active Directory Users and Computers
- DNS Manager
- PowerShell
- Command Prompt (ipconfig, ping, nslookup, nltest)
