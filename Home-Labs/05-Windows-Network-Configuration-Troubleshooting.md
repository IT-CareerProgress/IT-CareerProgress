Objective
Learn how to troubleshoot Windows network connectivity by examining IP configuration,
testing local connectivity, testing the default gateway, testing external connectivity,
and verifying DNS resolution.

Environment
- Windows 11 Virtual Machine
- Command Prompt
- IPv4
- DHCP
- DNS


Simulated Help-Desk Ticket

A user reports that their computer is unable to access websites. The technician needs to determine whether 
the problem is with the computer's network configuration, local network, Internet connectivity, or DNS.


initial troubleshooting process

Running ipconfig in command prompt to gather network configuration settings such as 
ipv4
default gateway
subnet
dns 


for the first step of the process I pinged the computers ipv4 address in order to 
verify the computer is atleast functioning and can broadcast a signal/communicate

from this point i pinged the default gateway in order to make sure the computer can communicate with
the device sending traffic/data from the computers on the network to the internet.

once i confirmed the ipv4 and default gateway were receiving response times i pinged 
an external ip address outside of the local network to make sure the computer can communicate with external devices
or IPs (8.8.8.8)

after confirming these steps i decided to test the dns server and verify the computer can translate domains into ip addresses
in order to the internet.
This was done using the "nslookup" command 


Overall the conclusion is that

All network connectivity tests succeeded. The VM was able to communicate with its own network interface,
reach the default gateway, reach an external IP address, resolve a domain name through DNS, 
and successfully communicate with the resolved hostname. No network connectivity problem was reproduced during testing.


What I learned 

I learned how IPv4 addresses, subnet masks, default gateways, DHCP, and DNS work together to provide network connectivity.
I also learned how to isolate a network problem by testing connectivity in stages rather than immediately 
changing network settings.


Key findings 

ipconfig provides important network configuration information.
The default gateway provides a path to other networks.
ping can be used to test connectivity at different points in the network path.
nslookup can test DNS resolution.
Successful IP connectivity does not necessarily mean DNS is working.
Testing a hostname combines DNS resolution with network connectivity.
Troubleshooting should proceed systematically from local connectivity toward external services.


IPv4
Subnet Masks
DHCP
DNS
Default Gateway
TCP/IP Troubleshooting
Ping
NSLookup
IP Configuration
Network Troubleshooting
Help Desk Troubleshooting Methodology
