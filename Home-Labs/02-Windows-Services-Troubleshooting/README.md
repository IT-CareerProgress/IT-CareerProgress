# Lab 02 — Windows Services Troubleshooting

## Objective

Learn how Windows services provide background functionality for the operating system and how service configuration can affect
Windows features.

The goal of this lab was to troubleshoot a Windows Search problem by investigating the Windows Search service.

---

## Environment

- Windows 10/11 Virtual Machine
- Windows Services
- Windows Search
- File Explorer
- Notepad
- Command Prompt

---

## Scenario

A user reports that Windows Search is not finding a newly created file.

The objective is to investigate the problem, identify whether a Windows service is involved, test a configuration change, and verify the results.

---

## Initial Problem

A new test file was created inside the Windows virtual machine.

Windows Search was used to locate the file, but the newly created file was not appearing in the search results as expected.

---

## Troubleshooting

The Windows Services management console was opened using:
services.msc

The Windows Search service was investigated.
The service startup configuration was temporarily changed to determine whether the service 
was affecting Windows Search functionality.

The same search test was then performed again.


Troubleshooting Process
1. Reproduced the Windows Search problem.
2. Investigated Windows services.
3. Identified Windows Search as a relevant service.
4. Changed the service configuration for testing.
5. Repeated the search test.
6. Compared the results.
7. Restored the original service configuration.
8. Created another test file.
9. Verified that Windows Search was functioning again.


Key Findings
The testing demonstrated that the Windows Search service configuration affected Windows Search's ability to locate newly created files.
Restoring the service configuration returned the search behavior to normal.


What I Learned
- Windows services provide background functionality for Windows.
- Services can affect other operating system features.
- The Services management console can be used to inspect and configure services.
- Changing a service configuration can help troubleshoot system problems.
- Troubleshooting should begin by reproducing the reported problem.
- Changes should be tested and verified.
- Service configurations should be restored after temporary troubleshooting changes.

Skills Demonstrated
- Windows Services
- Windows Search Troubleshooting
- Service Configuration
- Windows Troubleshooting
- Problem Reproduction
- Verification Testing
- Basic Windows Administration
