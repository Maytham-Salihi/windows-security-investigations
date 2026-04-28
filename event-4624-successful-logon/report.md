# Event ID 4624 – Successful Logon (Service Logon)

## Summary

Event ID **4624** indicates a **successful authentication** on the system.  
This instance shows a **Logon Type 5**, which corresponds to a **service logon** performed by the operating system.  
This behaviour is normal when Windows services start and authenticate locally.

## Evidence (From System Logs)

### Subject (Process Requesting the Logon)
- **Security ID:** SYSTEM  
- **Account Name:** [MachineAccount]$  
- **Account Domain:** WORKGROUP  
- **Logon ID:** 0x3E7  

### Logon Information
- **Logon Type:** 5 (Service Logon)  
- **Elevated Token:** Yes  
- **Virtual Account:** No  

### New Logon (Account That Logged On)
- **Security ID:** SYSTEM  
- **Account Name:** SYSTEM  
- **Account Domain:** NT AUTHORITY  
- **Logon ID:** 0x3E7  

### Process Information
- **Process ID:** 0x578  
- **Process Name:** C:\Windows\System32\services.exe  

### Network Information
- **Source Network Address:** —  
- **Source Port:** —  

### Authentication Details
- **Logon Process:** Advapi  
- **Authentication Package:** Negotiate  
- **Key Length:** 0  

*(Screenshot stored in `screenshots/`.)*

## Analysis

- Logon Type **5** indicates a **service** is logging on, not a human user.  
- The **SYSTEM** account with Logon ID **0x3E7** is a standard local system session.  
- The process responsible is **services.exe**, which is expected for service‑related logons.  
- No remote IP or port is present, confirming this is not a network logon.  
- No indicators of compromise are present in this event.

This event represents **normal Windows behaviour**.

## MITRE ATT&CK Context

While this specific event is benign, attackers may abuse service logons for persistence:

- **Technique:** T1543 – Create or Modify System Process  
- **Tactic:** Persistence / Privilege Escalation  

## Detection Logic (KQL Example)

```kusto
SecurityEvent
| where EventID == 4624
| where LogonType == 5
| project TimeGenerated, Account, LogonType, LogonProcess, AuthenticationPackage, Computer

