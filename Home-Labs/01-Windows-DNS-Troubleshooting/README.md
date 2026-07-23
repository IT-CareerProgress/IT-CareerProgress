Environment
Host OS: Windows 10
Virtualization Software: VirtualBox VM
Guest OS: Windows 10
VM Name: VboxUser



hostname: homelab
logged-in user(whoami) : /homelab/vboxuser
ipv4: 10.X.X.XX
subnet mask 255.XXX.XXX.XXX
default gateway:feXX::X%X


Ping from ipv4: Successful
ping from default gateway:Successful
ping from external ip:Successful

-----------------
Virtual machine connectivity is active and working properly^

  Problem
[User was unable to access websites on their computer} 

  Initial Hypothesis
[Computer appeared to have a functioning network connection because
it could communicate with external IPs]

  Symptoms
[- Computer could successfully ping its own IP
 - Computer could ping external IPs
 - Computer could ping default gateway
 - Computer failed to ping domain names (google.com etc
 - Computer timed out while running NSlookup]

 Tools Used
- Command Prompt
- PowerShell
- ipconfig
- ping
- nslookup
- tracert
- Network Settings

 Troubleshooting Steps
1.Checked IP configuration using ipconfig cmd
2.Pinged External IPs such as 8.8.8.8
3.Tested domain name connectivity with nslookup google.com
4.Determined external Ip connectivity was working
5.Inspected networks IPv4 DNS configurations
6. Identified an invalid DNS config
7. Restored DNS config to automatic
8. Flushed DNS cache using ipconfig /flushdns
9. Retested DNS Resolution


  Root Cause
[The Computer was configured to use an invalid DNS server]

  Resolution
[Invalid DNS server was removed and was restored to automatic DNS config and the DNS Cache was flushed afterwards]

  Verification
[reran nslookup google.com and returned valid response
 ping google.com successfully returned replies]

  Lessons Learned
[Computer can still communicate with IPs even if it cannot directly access websites/domain names
Testing external IPs and Default gateway as well as device IP helps
Identify where the issue in the process is coming from]




