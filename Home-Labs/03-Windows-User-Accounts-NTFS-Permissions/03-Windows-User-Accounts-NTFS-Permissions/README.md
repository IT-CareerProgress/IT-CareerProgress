# Lab 03 — Windows User Accounts & NTFS Permissions

## Objective

Learn how Windows local user accounts, groups, and NTFS permissions control access to files and folders.

The goal of this lab was to simulate a common help desk situation where a standard user encounters restricted access to a file or folder.

---

## Environment

- Windows 10/11 Virtual Machine
- Local Administrator account
- Standard local user account: `TestUser`
- NTFS file system
- Windows File Explorer
- Command Prompt

---

## Scenario

A user reports that they are unable to access or modify files inside an IT project folder.

As the technician, the objective is to:

1. Verify the user's account type.
2. Check the user's group membership.
3. Inspect the folder's NTFS permissions.
4. Determine why access is being restricted.
5. Understand the difference between administrator and standard-user access.
6. Apply appropriate permissions without unnecessarily making the user an administrator.

---

## Lab Setup

Created the following folder structure:

C:/Workshare
C:/Workshare/TestInvoice
C:/workshare/testinvoice/testnotepad


Verification of the users account

used " net test user " to verify what user group the local account was in 
and confirmed it was part of the users group

the commmand "whoami /groups " was also used to verify the permissions of the currently logged in account
which was an administrator


NTFS PERMISSIONS

Permissions were tested using combinations of:
- - Read
- - Write
- - Modify
- - List Contents
- - Full Control
 
Test and Issue diagnosis

The local user test account was attempting to access
a restricted file which they did not have permissions to
modify or write on.


Results demonstrated how windows enforced the assigned user 
permissions to the account 

This demonstrated that the test user was able to view the files
see the listed contents as well as read them, but could not save
nor make changes to the existing file

Troubleshooting

The following command " net user " and "whoami /groups" 
were used to determine which account was currently logged in,
as well as which accounts had what permissions and were apart of 
what groups.

Using these commands, I was able to determine the local test user 
was not given the ability to save or adjust the file, as a result
i went into the properties section and the security tab of said file,
selecting the test user and adjusting their individual permissions.

What I Learned
This lab provided hands-on experience with:
- Local Windows user accounts
- Standard users vs. administrators
- Windows security groups
- NTFS permissions
- Read, Write, Modify, and Full Control
- Access Denied troubleshooting
- net user whoami /groups
- - Basic Windows access control
- The principle of least privilege

Skills Demonstrated
- Windows User Administration
- NTFS Permissions
- Access Control
- Windows Troubleshooting
- Command Prompt
- Basic Windows Security
- Least-Privilege Concepts
     
