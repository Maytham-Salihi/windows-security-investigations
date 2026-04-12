# Successful System Logon – Event ID 4624

**System:** Windows Security Log  
**Severity:** Informational / Expected Behaviour  

---

## 📸 Screenshot: Event Viewer (Security Log)
<img width="1920" height="1080" alt="eventviewer" src="https://github.com/user-attachments/assets/a1bb731a-4896-4c6f-9cbe-cda6bcaafd51" />



---

## 📸 Screenshot: Event ID 4624 Details
<img width="1660" height="1080" alt="4624-details" src="https://github.com/user-attachments/assets/a6c3de20-623b-4765-b058-543be910373c" />

---

## 📝 Summary
A successful logon event was recorded for the SYSTEM account.  
The account name ending with “$” indicates a machine account, and the Logon ID `0x3E7` confirms this is a Local System logon session used by Windows services.  
This is normal system activity and not malicious.

---

## 🔍 Evidence
- **Security ID:** SYSTEM  
- **Account Name:** MAYTHAMSALIHI$  
- **Account Domain:** WORKGROUP  
- **Logon ID:** `0x3E7`  

---

## 🧠 Analysis
This event represents an internal authentication performed by the operating system.  
It is commonly generated when Windows services start or when the system performs background tasks.  
No suspicious behaviour detected.

---

## ✅ Conclusion
Normal system activity.  
No action required.

---

## 📁 Files Included
- `eventviewer.png`  
- `4624-details.png`  
- This report (`windows-4624-successful-logon.md`)
