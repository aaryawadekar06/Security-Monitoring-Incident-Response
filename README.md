# 🔐 Broken Anti-Automation – OWASP Juice Shop
## 🛡 Security Monitoring & Incident Response Project

---

## 📌 Project Overview

This project analyzes the **Broken Anti-Automation vulnerability** in OWASP Juice Shop.

Broken Anti-Automation occurs when a web application fails to properly prevent automated attacks such as:

- Brute force login attempts  
- Credential stuffing  
- Automated password reset abuse  
- Bot-based account creation  
- High-speed API abuse  

OWASP Juice Shop intentionally contains weak anti-automation protections for learning purposes.

---

## 🎯 Objectives

- Understand automated attack techniques
- Identify weak anti-automation controls
- Analyze logs to detect bot activity
- Implement detection logic
- Design incident response workflow

---

## 🧃 About OWASP Juice Shop

OWASP Juice Shop is an intentionally vulnerable web application used for cybersecurity training.  
It simulates a real e-commerce application and contains multiple security flaws including weak rate limiting and improper bot protection.

---

# 📊 1️⃣ Activity & Log Analysis

To detect Broken Anti-Automation, the following logs must be monitored:

### 🔍 Authentication Logs
- Multiple failed login attempts
- Rapid login attempts within seconds
- Same username attacked repeatedly
- Multiple usernames tested from same IP

### 🔍 API Logs
- High-frequency requests to `/rest/user/login`
- Repeated POST requests
- Automated request patterns

### 🔍 Network Logs
- Traffic spikes
- Same IP making hundreds of requests
- Suspicious user-agent headers

Indicators of automation:
- Requests every few milliseconds
- Sequential password testing
- No human-like delay between requests

---

# 🚨 2️⃣ Suspicious Behavior Detection Logic

## 📌 Rule-Based Detection

- IF failed login attempts > 5 within 1 minute → Trigger alert  
- IF login requests > 30 per minute from same IP → Flag as bot  
- IF multiple accounts targeted from same IP → Possible credential stuffing  

## 📌 Behavior-Based Detection

- Impossible human interaction speed  
- Identical repeated request payloads  
- No mouse or session variation  

---

# 🛡 3️⃣ Incident Classification & Response

| Severity | Scenario | Response |
|----------|----------|----------|
| Low | Minor login abuse | Monitor |
| Medium | Brute force attempt | Rate limit & warn |
| High | Credential stuffing | Block IP & lock accounts |
| Critical | Distributed bot attack | Activate WAF & escalate |

### 🔧 Response Actions

- Block malicious IP addresses  
- Enable account lockout mechanism  
- Enforce CAPTCHA validation  
- Apply rate limiting  
- Force password reset for affected users  

---

# 🔔 4️⃣ Alert & Response Workflow

1. Monitoring system detects abnormal login behavior  
2. Alert generated in SIEM  
3. Security analyst reviews logs  
4. Confirm automation attack  
5. Contain by blocking source  
6. Fix anti-automation gap  
7. Document incident  

---

# 🧯 Prevention & Mitigation

To prevent Broken Anti-Automation:

- Implement CAPTCHA on login & password reset  
- Enforce rate limiting  
- Apply account lockout policy  
- Enable Multi-Factor Authentication (MFA)  
- Secure backend APIs independently  
- Use Web Application Firewall (WAF)  
- Monitor behavioral patterns  

---

# ⚠ Security Risks

Broken Anti-Automation can lead to:

- Account takeover  
- Data breaches  
- Financial fraud  
- Denial of Service  
- Reputational damage  

---

# ✅ Conclusion

Broken Anti-Automation allows attackers to exploit application functionality using automated tools.  
OWASP Juice Shop demonstrates how weak rate limiting and missing bot protection mechanisms can lead to brute force and credential stuffing attacks.

Proper logging, detection logic, and layered security controls are essential to prevent automated abuse.

---

## 👩‍💻 Author

*Aarya Wadekar*

Cybersecurity Project
