Active Directory Home Lab
Phase 1: Building an Active Directory Domain Controller
Project Objective

The objective of this phase was to build a Windows Server 2022 Active Directory environment from scratch to develop hands-on experience with enterprise identity management, Windows Server administration, and PowerShell automation.

Lab Environment
Component	Configuration
Hypervisor	Oracle VirtualBox
Operating System	Windows Server 2022 Standard Evaluation (Desktop Experience)
Server Name	DC01
Domain	theory.lab
Server Roles	Active Directory Domain Services (AD DS), DNS
IP Address	192.168.10.10
Tasks Completed
Installed Windows Server 2022
Configured a static IPv4 address
Configured DNS
Renamed the server to DC01
Installed the Active Directory Domain Services role
Promoted the server to a Domain Controller
Created the theory.lab Active Directory domain
Creating Organizational Units

To organize departmental resources, I created separate Organizational Units (OUs) for:

IT
HR
Finance
Medical
Social Services

Initially, I created one OU manually to understand the process before automating the remaining OUs with PowerShell.

PowerShell Used
Import-Module ActiveDirectory

$OUs = @(
    "HR",
    "Finance",
    "Medical",
    "Social Services"
)

foreach ($OU in $OUs) {
    New-ADOrganizationalUnit -Name $OU -Path "DC=theory,DC=lab"
}
Skills Demonstrated
Windows Server Administration
Active Directory Domain Services
DNS Configuration
Organizational Unit Design
PowerShell Automation
PowerShell Arrays
foreach Loops
Challenges Encountered

During this phase I encountered several common PowerShell issues including:

Typographical errors
Variable naming mistakes
Multi-line PowerShell prompts (>>)
Script execution troubleshooting

Resolving these issues improved my understanding of PowerShell syntax and debugging techniques.

Evidence

📸 Windows Server 2022

📸 Server Manager

📸 Active Directory Users and Computers

📸 PowerShell creating Organizational Units

Reflection

Building an Active Directory domain from scratch helped me understand how Windows Server, DNS, and Active Directory work together. Automating Organizational Unit creation with PowerShell reinforced the value of scripting repetitive administrative tasks and highlighted the importance of testing and troubleshooting during system administration.

Phase 2: User Provisioning and Security Group Administration
Project Objective

The objective of this phase was to simulate an enterprise onboarding process by automating user account creation, organizing users into departmental Organizational Units, and implementing Role-Based Access Control (RBAC) through Active Directory Security Groups.

Tasks Completed
Created an employee CSV file
Imported user data into PowerShell
Simulated user creation using -WhatIf
Created Active Directory users
Verified user creation
Created Global Security Groups
Added users to department security groups
Verified group memberships
Employee CSV

The employee data was stored in a CSV file to simulate a Human Resources onboarding process.

FirstName,LastName,Username,Department
Jamie,Carter,jcarter,IT
Sam,Patel,Spatel,HR
Alex,Cross,Across,Finance
John,Doverman,Jdoverman,Medical
Perry,Gray,Pgray,Social Services
Dave,Smitherman,Dsmitherman,IT
PowerShell User Provisioning

Users were created using:

Import-Csv
foreach loops
New-ADUser
SecureString passwords

The initial execution used PowerShell's -WhatIf parameter to safely validate the automation before creating production objects.

Security Groups Created
Department	Security Group
IT	IT-Security
HR	HR-Security
Finance	Finance-Security
Medical	Medical-Security
Social Services	Social Services-Security
User Memberships
User	Group
Jamie Carter	IT-Security
Dave Smitherman	IT-Security
Sam Patel	HR-Security
Alex Cross	Finance-Security
John Doverman	Medical-Security
Perry Gray	Social Services-Security
PowerShell Commands Used
Import-Csv

New-ADUser

Add-ADGroupMember

Get-ADGroupMember
Skills Demonstrated
Active Directory User Administration
CSV Data Management
PowerShell Automation
Identity and Access Management (IAM)
Role-Based Access Control (RBAC)
Active Directory Security Groups
User Verification
Troubleshooting
Challenges Encountered

During this phase I learned several important administrative concepts:

Using -WhatIf before making production changes
Understanding duplicate account errors
Correcting incorrect usernames during group assignment
Verifying user creation before assigning permissions
Validating group memberships after configuration
Evidence

📸 Employee CSV

📸 PowerShell -WhatIf output

📸 User creation

📸 Active Directory Users and Computers showing users

📸 Security Groups

📸 Add-ADGroupMember commands

📸 Get-ADGroupMember verification

Reflection

This phase demonstrated how enterprise administrators automate user provisioning while implementing Role-Based Access Control through Active Directory Security Groups. Rather than assigning permissions directly to users, security groups provide a scalable and maintainable method for managing access to organizational resources. The project also reinforced the importance of validating automation, verifying configurations, and troubleshooting issues before deploying changes.

Technologies Used
Windows Server 2022
Active Directory Domain Services (AD DS)
DNS
PowerShell
Oracle VirtualBox
CSV
Active Directory Users and Computers (ADUC)
