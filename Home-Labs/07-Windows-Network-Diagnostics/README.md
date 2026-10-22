# Homelab 07: Windows Network Diagnostics

## Objective
Practice troubleshooting basic Windows network connectivity using built-in command-line tools, PowerShell, and Windows Event Viewer. Establish a healthy baseline and identify whether any network-related issues are observable.

## Environment
- **Operating system:** Windows
- **Tools:** Command Prompt, PowerShell, Windows Event Viewer
- **Scope:** Local network configuration, connectivity, routing, DNS resolution, TCP connectivity, and system logs
- **Safety:** Read-only diagnostic commands were used. Private network addresses and identifying details have been omitted.

## Diagnostic Procedure

### 1. Inspect network configuration
**Command:** `ipconfig /all`

**Result:** The active network adapter had an IPv4 address, a default gateway, and a DNS server configured. DHCP was enabled.

**Purpose:** Verify that Windows has the basic network configuration needed to communicate.

### 2. Test the local TCP/IP stack
**Command:** `ping 127.0.0.1`

**Result:** Successful replies; 0% packet loss.

**Purpose:** Verify that the local loopback address responds.

### 3. Test the default gateway
**Command:** `ping <default-gateway>`

**Result:** Successful replies; 0% packet loss.

**Purpose:** Confirm that the configured local gateway responds to ICMP requests.



### 4. Test external IP connectivity
**Command:** `ping 1.1.1.1`

**Result:** Successful replies; 0% packet loss.

**Purpose:** Test external IP connectivity without relying on hostname resolution.

### 5. Inspect the network route
**Command:** `tracert -d 1.1.1.1`

**Result:** The trace reached its destination.

**Purpose:** Observe the route taken toward an external IP address. The `-d` option prevents hostname lookups for intermediate hops.

### 6. Test DNS resolution
**Command:** `nslookup example.com`

**Result:** DNS resolution returned IP addresses successfully.

**Purpose:** Verify that a hostname can be resolved through the configured DNS service.

**Additional test:** A deliberately invalid hostname was queried. The output did not clearly establish whether an answer address was returned, so this test was recorded as inconclusive rather than treated as evidence of DNS redirection or another fault.

### 7. Test TCP connectivity
**PowerShell command:** `Test-NetConnection example.com -Port 443`

**Result:** `TcpTestSucceeded : True`

**Purpose:** Verify that a TCP connection to the destination on port 443 could be established.

### 8. Inspect the DNS Client service and Windows logs
**PowerShell command:** `Get-Service -Name Dnscache`

**Result:** The DNS Client service was running.

**Event Viewer:** Opened Windows Logs → System and reviewed relevant recent Critical, Error, and Warning events.

**Result:** No relevant network or DNS warnings or errors were identified.

## Results Summary

| Area tested | Result |
|---|---|
| Network configuration | Configuration present |
| Local loopback | Passed |
| Default gateway | Passed |
| External IP connectivity | Passed |
| Route tracing | Destination reached |
| Valid DNS lookup | Passed |
| Invalid-hostname lookup | Inconclusive |
| TCP port 443 | Passed |
| DNS Client service | Running |
| Relevant System log errors | None identified |

## Conclusion

The diagnostic tests indicated that basic network connectivity was functioning during the lab. The local TCP/IP loopback, default gateway, external IP connectivity, route tracing, valid DNS lookup, and TCP connectivity on port 443 all completed successfully. The DNS Client service was running, and no relevant network errors were identified in the reviewed Windows System logs.

The invalid-hostname test was inconclusive because the output did not clearly establish whether an answer address was returned. No specific network fault was reproduced, and no corrective changes were required based on the evidence collected.

## Skills Practiced
- Windows network configuration inspection
- ICMP connectivity testing with `ping`
- Route analysis with `tracert`
- DNS troubleshooting with `nslookup`
- TCP connectivity testing with PowerShell
- Windows service inspection
- Reviewing Windows System event logs
- Recording test evidence and drawing evidence-based conclusions



