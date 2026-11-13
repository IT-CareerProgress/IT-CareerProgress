Homelab 09 — Network Traffic Analysis with Wireshark

Objective

Learn how to capture, filter, and analyze network traffic using Wireshark. Examine DNS resolution, ICMPv6 communication, TCP connection establishment, and common network protocol layers.

Environment

Operating System: Windows

Network Interface: Wi-Fi

Packet Analysis Tool: Wireshark

Additional Tools: PowerShell

Lab 1 — Packet Capture

Selected the active Wi-Fi network interface in Wireshark and captured network traffic while generating DNS and ICMP traffic using PowerShell.

Commands used:

nslookup example.com
ping example.com

Observed Ethernet II, IPv6, TCP, and TLS protocol layers in captured packets.

Lab 2 — IPv6 Analysis

Inspected IPv6 packet headers and identified:

Source IPv6 address

Destination IPv6 address

Hop Limit

Observed a Hop Limit of 53.

Confirmed that the destination IPv6 address matched the computer's temporary IPv6 address.

Key concept: IPv6 Hop Limit is decremented by routers as a packet travels through a network. It serves the same general purpose as IPv4 TTL.

Lab 3 — DNS Analysis

Applied the Wireshark display filter:

dns && !mdns

Generated DNS traffic using:

nslookup example.com

Observations

Captured a DNS query for example.com.

Identified an A record query.

Located the corresponding DNS response.

Observed two returned IPv4 A records.

Confirmed the response was non-authoritative.

Observed recursion available.

Observed a TTL of approximately 3 minutes and 47 seconds.

Key concepts:

A records resolve domain names to IPv4 addresses.

AAAA records resolve domain names to IPv6 addresses.

DNS TTL determines how long a DNS record may remain cached.

Recursive DNS resolvers retrieve DNS information on behalf of clients.

Lab 4 — ICMPv6 Analysis

Applied the display filter:

icmp || icmpv6

Identified ICMPv6 Echo Request and Echo Reply packets.

Observations

Packet

Type

Code

Echo Request

128

0

Echo Reply

129

0

Key concept: ICMPv6 is used for network diagnostics and IPv6 control functions. Echo requests and replies are commonly used by ping to test reachability.

Lab 5 — TCP Analysis

Applied the display filter:

tcp

Inspected TCP headers and flags, including SYN, ACK, FIN, RST, and PSH.

Identified packets representing the TCP three-way handshake:

Stage

TCP Flags

Purpose

1

SYN

Client initiates connection

2

SYN, ACK

Server acknowledges request

3

ACK

Client acknowledges server response

Verified the corresponding source and destination port reversal between the SYN-ACK and final ACK packets.

Also observed an RST + ACK packet during the initial capture. Its cause was not conclusively determined.

Key concept: TCP uses a three-way handshake to establish connections before normal data exchange.

Key Skills Demonstrated

Capturing network traffic with Wireshark.

Applying display filters.

Identifying Ethernet II, IPv6, TCP, TLS, DNS, and ICMPv6.

Analyzing DNS queries and responses.

Understanding DNS records and TTL caching.

Inspecting IPv6 headers and Hop Limits.

Identifying ICMPv6 Echo Requests and Replies.

Analyzing TCP flags and connection establishment.

Interpreting packet source and destination ports.

Conclusion

Successfully completed a practical introduction to network traffic analysis using Wireshark. Captured and examined DNS, ICMPv6, and TCP traffic while developing an understanding of how network protocols communicate across different layers.

No network configuration or firewall settings were modified during this lab.
