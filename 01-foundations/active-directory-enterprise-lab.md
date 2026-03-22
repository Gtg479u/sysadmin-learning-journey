## Active Directory Enterprise Lab

### Overview
In this lab, I built a full Active Directory environment to simulate a real-world enterprise network. This expanded on my foundational work by adding user management, group-based access control, file shares, and Group Policy enforcement.

---

### Environment

- **DC01** – Windows Server 2022 (Domain Controller + DNS)
- **GT01** – Windows 11 (Domain-joined client)

---

### Domain
yellowjackets.local

---

### Organizational Structure

Corp  
├── IT  
├── HR  
└── Finance  

---

### User & Group Management

- Created **50 users using PowerShell**
- Organized users into departmental OUs
- Created security groups:
  - IT-Group
  - HR-Group
  - Finance-Group

---

### Group Policy Implementation

- IT:
  - Control Panel disabled

- Finance:
  - Command Prompt disabled

- HR:
  - No restrictions (used as baseline for comparison)

---

### File Shares & Permissions

Created shared folders on the domain controller:

C:\Shares\IT  
C:\Shares\HR  
C:\Shares\Finance  

Access was controlled using security groups:
- IT users → IT share only
- HR users → HR share only
- Finance users → Finance share only

---

### Drive Mapping (GPO)

Mapped network drives automatically using Group Policy:

- IT → Z:\IT
- HR → Z:\HR
- Finance → Z:\Finance

---

### Password Policy

Configured domain password policy:
- Minimum length: 8
- Complexity enabled
- Max age: 30 days

---

### Testing & Validation

- Logged in as multiple domain users
- Verified group membership using:
  whoami /groups
- Tested access to file shares
- Confirmed GPO restrictions
- Validated password policy enforcement

---

### What I Learned

- How Active Directory structures (OUs, groups, users) work together
- Difference between GPO Policies vs Preferences
- How to automate user creation with PowerShell
- How to troubleshoot DNS and domain join issues
- How permissions and access control are applied in real environments
