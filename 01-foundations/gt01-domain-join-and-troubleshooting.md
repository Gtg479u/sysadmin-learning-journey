# GT01 Domain Join & Client Troubleshooting (Windows 11)

## Goal
The goal with GT01 was to understand what actually happens on the client side when a machine joins a domain and a user tries to log in. I wanted to see how DNS, credentials, and domain communication affect whether a client can even “see” the domain, instead of just assuming the join process works when everything is configured correctly.

## Environment
- Hypervisor: VirtualBox
- Domain: yellowjackets.local

### Virtual Machine

**GT01**
- OS: Windows 11 Pro
- Role: Domain-joined client
- IP Address: 10.0.3.15 (static)
- Gateway: 10.0.3.2
- DNS: Initially incorrect, later corrected to point to DC01 (192.168.56.10)

**Domain Controller**
- DC01 (Windows Server 2022)
- IP Address: 192.168.56.10

## What I Did
- Built GT01 as a Windows 11 Pro VM
- Configured a static IP address
- Attempted to join GT01 to the yellowjackets.local domain
- Logged in using domain credentials once the join was successful
- Tested connectivity to DC01 using File Explorer and command-line tools

## Issues I Ran Into
- GT01 could not locate the domain controller during the domain join process
- DNS was initially pointing to the default gateway instead of the domain controller
- Errors appeared to be credential-related when the real issue was name resolution
- Confusion caused by GT01 and DC01 being on different subnets

## How I Fixed It
- Updated GT01’s DNS settings to point directly to DC01
- Verified connectivity by accessing `\\DC01`
- Confirmed SYSVOL and NETLOGON access from GT01
- Retried the domain join after correcting DNS
- Successfully logged in using a domain user account

## What I Learned
- A client cannot join a domain if it cannot resolve the domain controller through DNS
- Domain join errors are often misleading and don’t clearly point to DNS issues
- Even when machines are on different subnets, communication can still work depending on the virtual network setup
- Verifying access to SYSVOL and NETLOGON is a simple but powerful way to confirm domain connectivity
- Client-side issues are just as important to understand as server-side configuration

## What I plan to test next

- Add additional client machines to compare behavior  
- Intentionally break DNS to better understand login failures  
- Expand Group Policy testing across different users  
- Review Event Viewer logs to understand authentication and login behavior  

