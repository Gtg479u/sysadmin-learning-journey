# DC01 Domain Controller Setup (Active Directory Lab)

## Goal

I wanted to understand how Active Directory actually works from the ground up instead of just knowing the terminology.

At work, I see things like account issues, access problems, and domain-related errors, but I didn’t fully understand what was happening behind the scenes. I wanted to recreate those same types of situations in a lab so I could see how everything is connected and how to troubleshoot it myself.

The goal wasn’t just to follow steps it was to build the environment, break things, fix them, and understand why they worked once they were fixed.

I’m aiming to build a strong foundation so I can grow into a system administrator role and be confident handling real-world issues.

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

- Add additional client machines to simulate a larger environment  
- Configure user home directories  
- Expand Group Policy configurations (account lockout, auditing, etc.)  
