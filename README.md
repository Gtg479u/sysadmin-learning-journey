# System Administration Learning Journey

This repo shows how I built out an Active Directory environment step by step, starting from a basic domain setup and expanding it into a more realistic enterprise-style lab.

The lab started with basic domain setup and was later expanded into a more complete environment with users, policies, and access control.

## What you'll find here

- Windows Server & Active Directory hands-on labs  
- Domain-joined endpoint testing  
- Troubleshooting notes (what broke, why, and how I fixed it)  
- Networking fundamentals in practice  


## Active Directory Lab Journey

This repo shows how I built out an Active Directory environment step by step, starting from a basic domain setup and expanding it into a more realistic enterprise-style lab.

---

### Phase 1: Foundations

- Set up a Windows Server domain controller (DC01)  
- Created the domain: yellowjackets.local  
- Joined a Windows 11 client (GT01) to the domain  
- Ran into DNS and domain join issues and worked through them  

Files:
- dc01-domain-controller-setup.md  
- gt01-domain-join-and-troubleshooting.md  

---

### Phase 2: Build-Out

After getting the domain working, I expanded the environment to make it more realistic:

- Created an OU structure for IT, HR, and Finance  
- Used PowerShell to create around 50 users  
- Created security groups and assigned users by department  
- Created shared folders and controlled access using group permissions  
- Applied Group Policy to enforce different restrictions by department  
- Configured automatic drive mapping using GPO  
- Configured a domain password policy  

File:
- active-directory-enterprise-lab.md  

---

### What this lab demonstrates

- Active Directory setup and structure  
- Basic DNS troubleshooting  
- Group Policy in practice  
- PowerShell for admin tasks  
- How access control actually works in a domain  

