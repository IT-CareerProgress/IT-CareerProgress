#Objective
-Learn the fundamentals of windows event viewer and investigate windows system events and errors
as well as how to capitalize on the information provided by windows event viewer for troubleshooting
purposes

Environment

- Windows 10/11 Virtual Machine
- Windows Event Viewer
- Windows Services
- Windows Search
- Command Prompt


Scenario
A user is experiencing an issue with the Windows Search service. 
The technician needs to investigate Windows system logs to determine 
what occurred.


Used "eventvwr.msc" to open event viewer and began investigating the system logs for 
errors related to windows services

as a result of looking at event viewer I came across

Log: System
Source: Service Control Manager
Event ID: 7009
Level: Error

Upon discovering the actual system error occuring I did research on the actual 
event ID to try and determine what is going wrong


from this I concluded windows error event 7009 occurs whenever there is a timeout or failure
to connect 


Online research suggested modifying the Windows Registry to increase the service timeout. 
This change was not performed because there was insufficient evidence that increasing the timeout would resolve 
the underlying issue. The lab focused on evidence-based troubleshooting rather
than blindly applying an online fix.


Key Findings
- Event Viewer can provide evidence about Windows system problems.
- Event ID 7009 indicates a service connection/startup timeout.
- Service Control Manager records service-related events.
- Event IDs should be investigated in context rather than treated as automatic diagnoses.
- Online fixes should not be applied blindly.

Skills Demonstrated 

Windows Event Viewer
Windows System Logs
Service Control Manager
Event ID Investigation
Log Analysis
Windows Services
Troubleshooting Methodology
Evidence-Based Troubleshooting
Problem Reproduction
