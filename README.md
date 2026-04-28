# Windows Security Investigations

This repository contains a collection of Windows Security Event Log investigations performed as part of my cybersecurity training and SOC analyst development.  
All investigations are based on **real evidence collected directly from Windows Event Viewer** on a live Windows system.

## What Each Investigation Includes
- Event details and context  
- MITRE ATT&CK mapping (where applicable)  
- Detection logic (KQL-style examples)  
- Threat hunting questions  
- Screenshots  
- Final conclusion and risk rating  

---

# 🔍 Completed Investigations

### ✅ Event 4624 – Successful Logon  
[View Investigation](event-4624-successful-logon/report.md)

### ✅ Event 4625 – Failed Logon Attempt  
[View Investigation](event-4625-failed-logon/report.md)

### ✅ Event 4672 – Special Privileges Assigned  
[View Investigation](event-4672-special-privileges-assigned/report.md)

### ✅ Event 4720 – User Account Created  
(Attempted — No account creation events found)  
[View Investigation](event-4720-user-account-created/report.md)

### ✅ Event 4726 – User Account Deleted  
(Attempted — No account deletion events found)  
[View Investigation](event-4726-user-account-deleted/report.md)

### ✅ Event 4769 – Kerberos Service Ticket Request  
(Attempted — No Kerberos events due to WORKGROUP system)  
[View Investigation](event-4769-kerberos-service-ticket-request/report.md)

### ✅ Event 4771 – Kerberos Pre‑Authentication Failure  
(Attempted — No Kerberos events due to WORKGROUP system)  
[View Investigation](event-4771-kerberos-pre-auth-failure/report.md)

### ✅ Event 4776 – NTLM Authentication  
[View Investigation](event-4776-ntlm-authentication/report.md)

### ✅ Event 7045 – New Service Installed  
(Attempted — No service installation events found)  
[View Investigation](event-7045-new-service-installed/report.md)

---

# 🛠️ Tools Used
- **Windows Event Viewer** (primary and only tool used)

---

# 📌 Purpose of This Repository
This project demonstrates:
- Real-world SOC investigation workflow  
- Ability to analyze Windows Security Events  
- Professional documentation skills  
- Understanding of authentication, account management, and system activity logs  
- Ability to present findings clearly for recruiters and hiring managers  

---

# 📈 Future Improvements
As the lab environment expands, I plan to add:
- Sysmon-based investigations  
- SIEM-based detection logic (Splunk / ELK)  
- Additional Windows security events  

---

# 📬 Contact
For collaboration or feedback, feel free to connect.
