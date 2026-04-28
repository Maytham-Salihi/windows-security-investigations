# Event ID 7045 – New Service Installed (Attempted Investigation)

## Summary
Event ID **7045** is generated when a new service is installed on a Windows system. This event is important for detecting persistence mechanisms, unauthorized software installation, and attacker activity. During this investigation, I filtered the System Log for Event 7045. The filter returned **no matching events**, which is expected if no new services have been installed recently.

## Screenshot
![Event 7045 Screenshot](screenshots/event-7045.png)

## Interpretation of the Event
Event 7045 logs the installation of a new Windows service. If no entries appear, it means:
- No new services were installed by the user
- No software installations added new services
- No system processes created services
- No malicious activity attempted to establish persistence through services

This is normal for a stable WORKGROUP system where services are rarely added or modified.

## Why No Event Appears on This System
This machine is a **WORKGROUP** device with a stable configuration. New services are typically created only when:
- Software is installed that requires a background service
- Administrative tools add a service
- Scripts or automation create a service
- Malware installs a persistence service

Since none of these actions occurred recently, Event 7045 does not appear.

## Investigation Steps Performed
1. Opened **Event Viewer**
2. Navigated to **Windows Logs → System**
3. Applied filter for **Event ID: 7045**
4. Verified that **no events matched the filter**
5. Captured screenshot of the empty results
6. Documented findings and confirmed expected system behaviour

## SOC Analyst Interpretation
Event 7045 is critical for detecting:
- Unauthorized service installation
- Persistence mechanisms used by attackers
- Suspicious software deployment
- Privilege escalation attempts

In this case, the absence of Event 7045 indicates:
- No new services were installed
- No suspicious persistence mechanisms were created
- The system shows no signs of unauthorized service activity

## Conclusion
The investigation into Event ID 7045 was completed successfully. No service installation events were found, which is expected for a WORKGROUP system with no recent software or service changes. The empty result confirms that no unauthorized or unexpected services were installed.

**Status:** Lab Completed – No Service Installation Events Present  
**Action Required:** None  
**Recommendation:** Continue monitoring for unexpected service creation activity.

