# Homelab 08: Windows Firewall & Network Security

## Objective
Explore Windows Defender Firewall configuration using PowerShell. Inspect firewall profiles, inbound and outbound rules, 
default traffic actions, firewall logging settings, and the Windows Defender Firewall service.

## Environment
- **Operating system:** Windows
- **Tools:** Windows PowerShell, Windows Defender Firewall
- **Permissions:** Administrator PowerShell used for firewall rule inspection
- **Scope:** Firewall profiles, rule inspection, default actions, logging configuration, and service status
- **Safety:** Read-only inspection commands were used. No firewall settings or rules were modified.

## Step 1: Inspect Firewall Profiles

**Command:**
```powershell
Get-NetFirewallProfile |
    Select-Object Name, Enabled, DefaultInboundAction, DefaultOutboundAction
```

**Result:**
- Domain, Private, and Public firewall profiles were enabled.
- The initial profile output showed `NotConfigured` for default inbound and outbound actions.

**Purpose:** Identify the available firewall profiles and inspect their configuration.

## Step 2: Identify the Active Network Profile

**Command:**
```powershell
Get-NetConnectionProfile |
    Select-Object InterfaceAlias, NetworkCategory, IPv4Connectivity, IPv6Connectivity
```

**Result:**
- Network category: `Public`
- IPv4 connectivity: `Internet`
- IPv6 connectivity: `LocalNetwork`

**Purpose:** Determine how Windows classifies the active network and review its reported IPv4 and IPv6 connectivity.

## Step 3: Inspect Inbound Firewall Rules

**Command:**
```powershell
Get-NetFirewallRule -PolicyStore ActiveStore -Direction Inbound |
    Select-Object -First 15 DisplayName, Enabled, Profile, Action
```

**Result:**
- The command initially returned an access-denied error in the original PowerShell session.
- The command was rerun successfully in an elevated Administrator PowerShell session.
- The inspected rules included `Allow` actions.
- Four of the displayed rules were not enabled.

**Purpose:** Review a sample of inbound rules and understand their enabled state, applicable profiles, and actions.

**Note:** Only the first 15 matching rules were inspected. This result does not describe every inbound rule or establish the
security impact of any individual rule.

## Step 4: Inspect Outbound Firewall Rules

**Command:**
```powershell
Get-NetFirewallRule -PolicyStore ActiveStore -Direction Outbound |
    Select-Object -First 15 DisplayName, Enabled, Profile, Action
```

**Result:** The inspected outbound rules showed `Allow` actions.

**Purpose:** Compare outbound rules with inbound rules and other rules that may block traffic


Step 5: Verify Effective Firewall Defaults

Command:

Get-NetFirewallProfile -PolicyStore ActiveStore |
    Select-Object Name, Enabled, DefaultInboundAction, DefaultOutboundAction

Result:

All three profiles were enabled.

Default inbound action: Block

Default outbound action: Allow

Purpose: Inspect the effective profile policy and identify the default handling of incoming and outgoing traffic.

Step 6: Inspect Firewall Logging

Command:

Get-NetFirewallProfile -PolicyStore ActiveStore |
    Select-Object Name, LogBlocked, LogAllowed, LogFileName, LogMaxSizeKilobytes

Result:

LogBlocked: False for all three profiles

LogAllowed: False for all three profiles

Purpose: Determine whether Windows Firewall's own logging of allowed and blocked connections is enabled.

Observation: Connection logging was disabled for all three profiles at the time of inspection. This does not mean the firewall
itself was disabled.

Step 7: Verify the Windows Defender Firewall Service

Command:

Get-Service -Name mpssvc

Result: Status was Running.

Purpose: Confirm that the Windows Defender Firewall service was running.

Step 8: Final Configuration Snapshot

Command:

Get-NetFirewallProfile -PolicyStore ActiveStore |
    Format-Table Name, Enabled, DefaultInboundAction, DefaultOutboundAction, LogBlocked, LogAllowed -AutoSize

Result: The final snapshot confirmed:

Domain, Private, and Public profiles enabled

Default inbound action set to Block

Default outbound action set to Allow

LogBlocked and LogAllowed set to False for all three profiles

Results Summary

Area inspected

Finding

Firewall profiles

All three enabled

Active network category

Public

IPv4 connectivity

Internet

IPv6 connectivity

LocalNetwork

Sample inbound rules

Included Allow actions; four displayed rules disabled

Sample outbound rules

Displayed rules showed Allow actions

Effective default inbound action

Block

Effective default outbound action

Allow

Firewall connection logging

Allowed and blocked traffic logging disabled

Windows Defender Firewall service

Running

Security Observations

Blocking inbound traffic by default is a common defensive configuration for Windows Firewall.

Allowing outbound traffic by default is common, but outbound rules can still restrict specific traffic.

A rule with an Allow action does not necessarily apply to every connection; its enabled state, profile, and other conditions matter.

Firewall connection logging was disabled during this inspection. Enabling logging may help with future troubleshooting,
but it should be an intentional configuration decision based on monitoring needs and available storage.

A Public network profile is generally appropriate for untrusted networks. A trusted home network may warrant a different profile,
depending on the environment.

Conclusion

This lab used PowerShell to inspect Windows Defender Firewall configuration without changing security settings. 
All three firewall profiles were enabled, effective default inbound traffic was blocked,
and default outbound traffic was allowed. The inspected inbound and outbound rules illustrated how individual 
rules have their own actions and enabled states.

The Windows Defender Firewall service was running. Logging of allowed and blocked connections was disabled for all three 
profiles. The results provide a baseline of the computer's firewall configuration at the time of testing; they do not, 
by themselves, establish that every rule or security setting is optimal.

Skills Practiced

Inspecting Windows Defender Firewall profiles

Understanding inbound and outbound firewall rules

Reviewing effective firewall policy settings

Inspecting firewall connection logging

Checking Windows services with PowerShell

Running elevated PowerShell commands

Troubleshooting an access-denied error

Documenting security configuration without exposing private information
