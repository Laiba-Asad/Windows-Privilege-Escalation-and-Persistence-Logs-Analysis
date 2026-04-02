# Windows Privilege Escalation & Persistence – Incident Analysis

This project documents a simulated attack involving **privilege escalation and persistence techniques** on a Windows system, analyzed using Wazuh SIEM logs.

---

## Overview

The lab focuses on identifying post-compromise attacker behavior, including:

- Privilege escalation via group manipulation  
- Persistence through service creation  
- Abuse of legitimate Windows features (WSL, restore points)  
- Privileged logon activity  

---

## Environment

- **Target System:** DESKTOP-5LV1F3O  
- **IP Address:** 192.168.1.105  
- **Platform:** Windows  
- **Monitoring Tool:** Wazuh SIEM  

---

## Attack Timeline

### 🔹 Privilege Escalation (02:16)
- Local group modifications observed  
- User `Dev` added to privileged group (docker-users)  

**MITRE:** T1484 – Privilege Escalation via Group Modification  

---

### 🔹 Preparation Activity
- Windows restore point created  
- Likely used as a fallback mechanism  

---

### 🔹 Persistence via Service Creation (02:17)
- New Windows service created  
- Common technique for maintaining access  

**MITRE:** T1543 – Create or Modify System Process  

---

### 🔹 System Restart (02:20)
- System shutdown and restart  
- Likely applied changes made by attacker  

---

### 🔹 Privileged Logon (02:22)
- Successful logon with special privileges  
- Indicates escalation was successful  

---

### 🔹 WSL Installation (02:28)
- Windows Subsystem for Linux installed  
- Enables execution of Linux-based tools within Windows  

**MITRE:** T1059.004 – Command Execution (WSL)  

---

### 🔹 Continued Persistence (02:28 – 02:29)
- Additional services created  
- Service-based logons observed  
- Multiple privileged sessions recorded  

---

## Key Indicators

- Group membership changes  
- Restore point creation  
- New service installation  
- Privileged logon events  
- WSL installation activity  

---

## Analysis

This attack demonstrates typical post-compromise behavior:

1. Elevate privileges  
2. Establish persistence  
3. Prepare fallback mechanisms  
4. Extend capabilities (WSL)  
5. Maintain long-term access  

Attackers leveraged built-in Windows features to blend in with legitimate activity.

---

## Impact

- Privilege escalation achieved  
- Persistent access established  
- System-level changes performed  

---

##  MITRE ATT&CK Mapping

| Technique | ID |
|----------|----|
| Privilege Escalation (Group Modification) | T1484 |
| Persistence (Service Creation) | T1543 |
| Command Execution (WSL) | T1059.004 |

---

## Key Learnings

- Group changes are critical escalation indicators  
- Service creation is a strong persistence signal  
- WSL can be abused for stealthy execution  
- Privileged logons should always be monitored  

---

## Recommendations

- Monitor Event IDs 4731, 4732, 4735 (group changes)  
- Alert on Event ID 7045 (service creation)  
- Restrict WSL installation  
- Audit privileged logons regularly  
- Implement endpoint hardening  

---

## Conclusion

This lab highlights how attackers escalate privileges and establish persistence using legitimate Windows features. It emphasizes the importance of monitoring system changes and privileged activity in a SOC environment.

---

##  Author

Laiba Asad
CyberSecurity Engineer

## 👤 Author

Laiba Asad
