## Objective

Learn how Windows local user accounts, security groups, and NTFS permissions work together.


The goal was to create a new employee account, place the employee into an appropriate security group,
assign permissions to the group, and verify that the employee received the intended access without 
receiving unnecessary administrative privileges.

## Environment
Windows 11 Virtual machine 
File explorer
Command prompt 


## Simulated Scenario 

A new employee has joined the company.

The technician needs to:

1. Create the employee's local account.
2. Place the employee into the appropriate security group.
3. Assign the group access to a company folder.
4. Verify that the employee receives the intended access.
5. Verify that the employee does not have administrative privileges.


Initial Process

Created the local employee account using the command
"net user LabEmployee /add"

this local account was initially a member of the standard users group. With 
basic permissions adjusted by the administrator account

Created a local group for the simulated IT department using
"net localgroup ITSupport /add"

after the local group was added I then also in command prompt added the local employee account
to the group using the command

"net localgroup IT-Support LabEmployee /add"

Verified the local accounts membership in the group via
"net user LabEmployee"

Also verified membership from the groups side
net localgroup IT-Support


NTFS Permissions
Created a test folder containing another folder and a text document.
Permissions were assigned to the following accounts/groups:
- Administrator account (vboxuser) — Full Control
- IT-Support — List folder contents, Read & Execute, and Write
Permissions were assigned to the IT-Support group rather than directly to LabEmployee.


Access Testing
Logged into LabEmployee and tested access to the protected folder.
LabEmployee was able to access the folder because the account was a member of IT-Support.
A separate standard local user that was not a member of IT-Support was unable to access the folder.


This demonstrated that access was being granted through group membership rather than
by directly assigning permissions to the individual employee account.

Administrative Privilege Verification

Verified that LabEmployee was not a member of the local Administrators group.
The account therefore remained a standard user while receiving the additional access provided through IT-Support.

Troubleshooting / Verification Process
The lab followed this process:
1. Create employee account
2. Verify standard user status
3. Create IT-Support group
4. Add employee to IT-Support
5. Verify group membership
6. Assign NTFS permissions to IT-Support
7. Test access with LabEmployee
8. Test access with a standard user outside the group
9. Verify LabEmployee was not an administrator

Key Findings
- Windows local users can be organized into security groups.
- NTFS permissions can be assigned to groups instead of individual users.
- A user can receive access through group membership without being an administrator.
- Users outside the authorized group can be denied access to protected resources.
- Group-based permissions make access management easier to maintain in larger environments.

What I Learned
This lab demonstrated the relationship between:
User → Group → Permission
Instead of assigning folder permissions directly to individual users, permissions can be assigned to a security 
group and users can receive those permissions through group membership. I also learned the importance of least privilege
by keeping LabEmployee as a standard user instead of adding the account to the Administrators group.


Skills Demonstrated
- Windows Local User Administration
- Windows Local Group Administration
- NTFS Permissions
- Group-Based Access Control
- Access Testing
- Least Privilege
- Command-Line Administration
- Windows Troubleshooting
- User and Group Verification
