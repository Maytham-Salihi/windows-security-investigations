# Event ID 4625 — Failed Logon Attempt Investigation

![event4625](screenshots/event4625.png)

## Summary
Event ID **4625** indicates a **failed logon attempt** on the system. This event is generated when authentication fails due to an incorrect username, incorrect password, or an attempt to log in using invalid credentials. In this case, the failed logon originated from the local workstation and was triggered by an incorrect username or password.

## Evidence

| Field | Value |
|-------|--------|
| **Event ID** | 4625 |
| **Failure Reason** | Unknown user name or bad password |
| **Status** | 0xC000006D |
| **Sub Status** | 0xC000006A |
| **Logon Type** | 2 / 3 (based on screenshot) |
| **Account Attempted** | `msalihi` |
| **Account Domain** | `MAYTHAMSALIHI` |
| **Subject Security ID** | SYSTEM |
| **Caller Process Name** | `C:\Windows\System32\lsass.exe` |
| **Source Network Address** | 127.0.0.1 or ::1 |
| **Source Port** | 0 / 62731 |
| **Workstation Name** | (blur before posting) |

## Analysis
The failed logon attempt was caused by an incorrect username or password. The **Status** and **Sub Status** codes confirm this:

- **0xC000006D** → Bad username or password  
- **0xC000006A** → Incorrect password  

The **Caller Process Name** (`lsass.exe`) and **Logon Process** (`User32` or `NtLmSsp`) indicate that Windows handled the authentication attempt normally. The **Source Network Address** being `127.0.0.1` or `::1` confirms the attempt originated **locally**, not from a remote attacker.

This behaviour is consistent with:
- A user mistyping their password  
- A non‑existent username being entered  
- A local script or service attempting authentication  
- A deliberate test to generate Event ID 4625  

There is **no indication of malicious activity** in this specific event.

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|-----------|----|-------------|
| **Brute Force** | T1110 | Adversaries may attempt to gain access by guessing passwords |
| **Valid Accounts** | T1078 | Failed attempts may precede successful credential use |
| **Credential Access** | TA0006 | Failed logons often appear during credential‑guessing activity |

## Detection Logic (KQL for Microsoft Sentinel)

```kql
SecurityEvent
| where EventID == 4625
| extend FailureReason = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="FailureReason")]."#text")
| extend AccountName = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="TargetUserName")]."#text")
| extend LogonType = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="LogonType")]."#text")
| extend SourceIP = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="IpAddress")]."#text")
| project TimeGenerated, AccountName, LogonType, FailureReason, SourceIP, Computer
```

## Interpretation
This event represents a **single failed logon attempt** with no signs of brute‑force or password‑spray behaviour.

Indicators that would suggest malicious activity (not present here):
- Multiple 4625 events in a short time  
- Sequential username attempts  
- Attempts from external IP addresses  
- Logon Type 10 (remote) or 3 (network) from unknown sources  

Your event appears to be **normal system behaviour** consistent with your testing.

## Conclusion
This Event ID 4625 log entry shows a **local failed authentication attempt** caused by an incorrect username or password. There is **no evidence of malicious intent** in this specific event. However, monitoring for repeated 4625 events is essential, as they can indicate:

- Brute‑force attacks  
- Password spraying  
- Lateral movement attempts  
- Credential harvesting  

This investigation demonstrates your ability to analyse authentication failures, interpret Windows security logs, and map findings to MITRE ATT&CK — all key skills for UK SOC analyst roles.

## Files Included
- `screenshots/event4625.png`  
- `report.md`
