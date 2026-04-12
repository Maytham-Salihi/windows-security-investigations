<img width="1927" height="1067" alt="eventviewer" src="https://github.com/user-attachments/assets/afdbece8-df0c-42b1-8ce6-9aafec1bfab1" />
# Successful System Logon – Event ID 4624

**System:** Windows Security Log  
**Severity:** Informational / Expected Behaviour  

---

## 📸 Screenshot: Event Viewer (Security Log)
> Replace `eventviewer.png` with your actual screenshot filename.

![Event Viewer Screenshot](eventviewer.png)

---

## 📸 Screenshot: Event ID 4624 Details
> Replace `4624-details.png` with your actual screenshot filename.

![4624 Event Details](4624-details.png)

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
