# 🧪 SIEM Investigation Report

## 📌 Overview

I analyzed Linux authentication logs using Splunk to identify normal system behavior and detect potential security threats.

---

## 🔍 Observations

### ✅ Normal Activity

* Successful SSH login attempts detected
* Regular system usage observed

---

### 🚨 Suspicious Activity

* Multiple failed login attempts from specific IP addresses
* Repeated authentication failures indicating possible brute-force attack

---

## 📊 Analysis

### Failed Login Pattern

Several IP addresses attempted multiple logins within a short time frame.

### Indicator:

* High number of "Failed password" events

---

## 🚨 Detection

Query used:

```
"Failed password" | stats count by src_ip
```

### Result:

* Identified IP addresses with repeated login failures
* Flagged potential attackers

---

## 📈 Risk Assessment

| Activity          | Risk Level |
| ----------------- | ---------- |
| Failed Logins     | Medium     |
| Successful Logins | Low        |
| SSH Activity      | Normal     |

---

## 🧠 Conclusion

The system shows signs of repeated failed login attempts, which may indicate brute-force attack attempts. No confirmed compromise was detected.

---

## 🔐 Recommendations

* Continue monitoring logs
* Use Fail2Ban to block attackers
* Implement alerting for repeated failures
* Restrict SSH access where possible

---
