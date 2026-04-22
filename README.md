# 🛡️ SIEM Project – Log Analysis & Threat Detection (Splunk)

## 📌 Overview

I implemented a SIEM (Security Information and Event Management) solution using Splunk to collect, analyze, and monitor Linux authentication logs.

The project simulates a real SOC (Security Operations Center) environment where logs are ingested, analyzed, and used to detect potential security threats such as brute-force attacks.

---

## 🎯 Objectives

* Ingest Linux authentication logs into Splunk
* Analyze system activity using search queries
* Detect suspicious login attempts
* Build dashboards for monitoring
* Simulate SOC-level investigation

---

## 🛠️ Technologies Used

* Splunk Enterprise
* Ubuntu Server (log source)
* SSH logs (/var/log/auth.log)

---

## 📥 Log Ingestion

Authentication logs from the Linux server were imported into Splunk for centralized monitoring.

### Source:

* `/var/log/auth.log`

### Purpose:

* Monitor login attempts
* Detect unauthorized access
* Analyze authentication events

---

## 🔍 Log Analysis

### Key Queries Used:

#### 🔹 All Events

```
index=*
```

#### 🔹 Failed Login Attempts

```
"Failed password"
```

#### 🔹 Successful Logins

```
"Accepted password"
```

#### 🔹 SSH Activity

```
sshd
```

---

## 🚨 Detection Logic

### Brute-Force Detection

```
"Failed password" | stats count by src_ip
```

### Explanation:

This query identifies IP addresses with multiple failed login attempts, which may indicate brute-force attacks.

---

## 📊 Dashboard

A monitoring dashboard was created to visualize:

* Failed login attempts
* Successful logins
* SSH activity

This provides real-time visibility into system security.

---

## 🧪 Testing & Validation

* Generated SSH login attempts
* Simulated failed logins
* Verified detection of suspicious IPs
* Confirmed log ingestion and query results

---

## 🚧 Challenges & Solutions

### Issue:

Logs initially not structured properly for IP extraction

### Solution:

Used keyword-based searches and filtering to identify patterns

---

## 📈 Key Takeaways

* Hands-on experience with SIEM tools
* Log analysis and threat detection
* Understanding of authentication events
* Practical SOC investigation workflow

---

## 🧠 Conclusion

The system is functioning normally but shows multiple failed login attempts, indicating potential brute-force activity. Continuous monitoring and automated response mechanisms are recommended.

---
