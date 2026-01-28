# DC01 Domain Controller Setup (Active Directory Lab)

## Goal
I wanted to actually understand what Active Directory is doing behind the scenes instead of just knowing the terminology. I kept running into login and access issues at work and wanted to recreate those problems in a lab where I could see exactly what was happening. I didn’t want to just follow a guide — I wanted to break things, fix them, and understand why they worked once they were fixed.

## Environment
- Hypervisor: VirtualBox (fresh rebuild on a new computer)
- Domain: yellowjackets.local

### Virtual Machine

**DC01**
- OS: Windows Server 2022
- Role: Domain Controller (AD DS + DNS)
- IP Address: 192.168.56.10 (static)
- Gateway: 192.168.56.1
- DNS: 192.168.56.10 (initially misconfigured)

*A Windows 11 client (GT01) was later used to validate domain functionality.*

## What I Did
- Installed Active Directory Domain Services and DNS on DC01
- Promoted DC01 to a domain controller for yellowjackets.local
- Created users and OUs in Active Directory (some initially created with PowerShell, then corrected in ADUC)
- Configured a static IP for DC01
- Verified domain functionality using SYSVOL and NETLOGON shares

## Issues I Ran Into
- DNS SRV record errors during domain validation
- Domain authentication failures caused by DNS misconfiguration
- Confusion caused by DC01 initially pointing DNS to loopback
- Running `dcdiag` with output redirection looked like it wasn’t doing anything

## How I Fixed It
- Corrected DC01’s DNS configuration from loopback (127.0.0.1) to its own static IP
- Used `dcdiag` to verify DNS health and SRV records
- Used `repadmin` to confirm replication and overall domain health
- Verified access to `\\DC01\sysvol` and `\\DC01\netlogon` from a domain-joined client

## What I Learned
- Active Directory is extremely dependent on DNS being configured correctly
- If DNS is wrong, AD might look like it’s working when it really isn’t
- Many authentication issues trace back to name resolution, not credentials
- Tools like `dcdiag` and `repadmin` are essential for validating AD health
- Sometimes commands are running correctly even when they don’t show output right away

## Next Steps
- Create and test Group Policy Objects (GPOs)
- Add additional client VMs
- Configure shared folders and home directories
