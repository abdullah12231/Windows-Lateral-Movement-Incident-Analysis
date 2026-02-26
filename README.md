# PsExec Lateral Movement Incident Analysis

# Scenario
- This lab simulates a lateral movement attack using PsExec between two Windows machines (WIN-ATTACK → WIN-VICTIM).
The objective was to detect and analyze the activity using Windows Event Logs and Sysmon.

# Attack Timeline 
1. Successful Network Logon (Event ID 4624 - Logon Type 3)
2. Service Installation (Event ID 7045 - PSEXESVC)
3. Remote Command Execution (Sysmon Event ID 1)

# MITRE ATT&CK Mapping 
- T1021.002 – SMB/Windows Admin Shares
- T1569.002 – Service Execution
- T1059.003 – Windows Command Shell

# Detection Strategy
Detection can be achieved by monitoring:
- Event ID 4624 (Type 3 logons)
- Event ID 7045 (Service creation)
- Sysmon Event ID 1 (Parent process = PSEXESVC.exe)

# Key Takeaways
- Importance of monitoring service creation events
- Correlating 4624 + 7045 + Sysmon Event ID 1
- Detecting administrative lateral movement activity


## Event ID 4624 – Network Logon
![4624 Logon](screenshots/4624_EVENTID.png)

## Event ID 7045 – Service Creation
![7045 Service](screenshots/7045_EVENTID.png)

## Sysmon Event ID 1 – Process Execution
![Sysmon Event 1](screenshots/SYSMON_EVENTID_1.png)

## PsExec Remote Terminal
![PsExec Terminal](screenshots/PSEXEC_TERMINAL.png)
