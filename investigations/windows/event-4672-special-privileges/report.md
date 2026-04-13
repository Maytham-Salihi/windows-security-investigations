## Event ID 4672 — Special Privileges Assigned to New Logon

### Screenshot
(Insert your screenshot here)
Example:
![event4672](screenshots/event4672.png)

---

### Summary
Event ID 4672 is generated when an account logs on and is automatically assigned administrative‑level privileges. In this case, the SYSTEM account (NT AUTHORITY\SYSTEM) received a set of powerful privileges used for core operating system functions. This behavior is normal and expected during system operations.

---

### Evidence
- **Security ID:** SYSTEM  
- **Account Name:** SYSTEM  
- **Account Domain:** NT AUTHORITY  
- **Logon ID:** 0x3E7  

**Privileges Assigned:**  
- SeAssignPrimaryTokenPrivilege  
- SeTcbPrivilege  
- SeSecurityPrivilege  
- SeTakeOwnershipPrivilege  
- SeLoadDriverPrivilege  
- SeBackupPrivilege  
- SeRestorePrivilege  
- SeDebugPrivilege  
- SeAuditPrivilege  
- SeSystemEnvironmentPrivilege  
- SeImpersonatePrivilege  
- SeDelegateSessionUserImpersonatePrivilege  

---

### Analysis
This event indicates that a new logon session was granted high‑level privileges. The SYSTEM account is the highest‑privileged built‑in identity on Windows and routinely receives these privileges for normal OS operations. These privileges allow actions such as loading drivers, debugging processes, taking ownership of files, and impersonating other accounts.

No signs of privilege escalation or unauthorized activity are present. If these privileges were assigned to a non‑SYSTEM or non‑administrator account, it would indicate a critical security incident.

---

### Conclusion
Normal system activity.  
No further investigation required.

---

### Files Included
- event4672.png
