# Event ID 4776 — NTLM Authentication Attempt Investigation

## Summary
Event ID **4776** is generated when a computer attempts to validate user credentials using the **NTLM authentication protocol**. This event appears on standalone Windows machines (WORKGROUP) and domain‑joined systems. It is the NTLM equivalent of Kerberos authentication events (4768/4769).

This event is important for detecting:
- Password guessing attempts  
- Credential stuffing  
- Legacy authentication usage  
- Lateral movement attempts  
- Misconfigured services repeatedly authenticating  

Your captured event shows a **successful NTLM authentication**.

---

## Evidence

### Screenshot
![NTLM Authentication Screenshot](screenshots/Event ID 4776.png)

### Event Data

| Field | Value |
|-------|--------|
| **Authentication Package** | MICROSOFT_AUTHENTICATION_PACKAGE_V1_0 |
| **Logon Account** | msalihi |
| **Source Workstation** | MAYTHAMSALIHI |
| **Error Code** | 0x0 (Success) |

---

## Interpretation

### 🔐 What happened
Your computer attempted to validate the credentials for the account **msalihi** using NTLM.  
The **Error Code 0x0** indicates the authentication was **successful**.

### 🧠 Why this matters
NTLM authentication events are critical for SOC analysts because:

- NTLM is still widely used in legacy systems  
- Attackers often target NTLM for **brute force** and **credential replay**  
- NTLM authentication can reveal early signs of lateral movement  
- NTLM is weaker than Kerberos and easier to abuse  

Even on a standalone machine, this event demonstrates your ability to analyse authentication flows.

---

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|-----------|----|-------------|
| **Brute Force** | T1110 | Attackers may attempt repeated NTLM logons |
| **Valid Accounts** | T1078 | Successful NTLM authentication may indicate compromised credentials |
| **Credential Access** | TA0006 | NTLM is commonly targeted for credential harvesting |

---

## Detection Logic (KQL for Microsoft Sentinel)

```kql
SecurityEvent
| where EventID == 4776
| extend AuthPackage = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="PackageName")]."#text")
| extend TargetUser = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="TargetUserName")]."#text")
| extend Workstation = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="Workstation")]."#text")
| extend Status = tostring(parse_xml(EventData).EventData.Data[?(@.Name=="Status")]."#text")
| project TimeGenerated, TargetUser, Workstation, AuthPackage, Status, Computer
```

---

## Indicators of Malicious Activity (Not Present Here)

This event is **normal**, but SOC analysts watch for:

- Multiple 4776 failures in a short time  
- Authentication attempts from unusual workstations  
- NTLM usage where Kerberos is expected  
- Repeated attempts against disabled or non‑existent accounts  
- Status codes other than `0x0` (success)  

Your event shows **none** of these — it is a clean, successful NTLM authentication.

---

## Conclusion
This Event ID 4776 log entry represents a **successful NTLM authentication attempt** for the account **msalihi** from the workstation **MAYTHAMSALIHI**.  
It demonstrates your ability to analyse NTLM authentication behaviour, understand legacy protocols, and interpret Windows Security Logs — all essential skills for SOC analysts.

---

## Files Included
- `screenshots/Event ID 4776.png`  
- `report.md`
