# 🔐 API Security Risk Analysis Report
### Future Interns — Cyber Security Task 3 (2026)

![Security](https://img.shields.io/badge/Type-API%20Security%20Audit-blue)
![Framework](https://img.shields.io/badge/Framework-OWASP%20API%20Top%2010%20(2023)-red)
![Scope](https://img.shields.io/badge/Scope-Read--Only%20%7C%20Ethical-green)
![Findings](https://img.shields.io/badge/Findings-7%20Vulnerabilities-orange)

---

## 📋 Overview

This repository contains a complete **API Security Risk Analysis** performed as part of the Future Interns Cyber Security Internship (Task 3, 2026). The assessment simulates the type of structured security audit delivered by professional AppSec consultants and SaaS security teams.

The audit identifies real-world API security vulnerabilities using only **ethical, read-only methods** on public test APIs — no exploitation, no data modification, no denial-of-service testing.

---

## 🎯 Objective

- Analyze public/demo APIs for security vulnerabilities
- Identify and classify risks using the OWASP API Security Top 10 (2023)
- Explain risks in clear business language
- Provide actionable remediation recommendations

---

## 🔍 APIs Tested

| API | URL | Purpose |
|-----|-----|---------|
| **JSONPlaceholder** | https://jsonplaceholder.typicode.com | Simulated social/blog API |
| **ReqRes** | https://reqres.in | User management & auth simulation |

Both APIs are public, free-to-use platforms specifically designed for testing and learning.

---

## 🛠 Tools Used

| Tool | Purpose |
|------|---------|
| **Postman** | API request testing, response inspection, collection management |
| **Browser DevTools** | HTTP header analysis (Network tab) |
| **OWASP API Top 10 (2023)** | Risk classification framework |
| **API Security Checklist (shieldfy)** | Supplemental security control reference |

---

## 📐 Methodology

The assessment followed a 5-phase structured approach:

1. **Reconnaissance** — Reviewed public API documentation and endpoint inventory
2. **Endpoint Mapping** — Identified all accessible endpoints via GET requests
3. **Authentication Analysis** — Tested whether endpoints require authentication
4. **Header & Response Inspection** — Analyzed HTTP response headers and payloads
5. **Risk Classification** — Mapped findings to OWASP API Top 10 and assigned severity

---

## ⚖️ Scope & Ethics

**Allowed:**
- ✅ Read-only GET/POST requests
- ✅ Response and header inspection
- ✅ Documentation-based analysis
- ✅ Public/demo APIs designed for testing

**Not Allowed:**
- ❌ Exploitation or bypass attempts
- ❌ DoS/flooding testing
- ❌ Accessing private or production systems
- ❌ Modifying or deleting any data

---

## 📊 Findings Summary

| ID | Finding | Severity | OWASP Reference |
|----|---------|----------|-----------------|
| F1 | Unauthenticated Access to User Data | 🔴 HIGH | API2:2023 |
| F2 | Broken Object Level Authorization (BOLA) | 🔴 HIGH | API1:2023 |
| F3 | Unauthenticated Data Creation (POST) | 🔴 HIGH | API2:2023 |
| F4 | Missing Rate Limiting | 🟠 MEDIUM | API4:2023 |
| F5 | Excessive Data Exposure | 🟠 MEDIUM | API3:2023 |
| F6 | Authentication Token Not Enforced | 🟠 MEDIUM | API2:2023 |
| F7 | Missing HTTP Security Headers | 🟡 LOW | API8:2023 |

**Total: 7 findings — 3 High | 3 Medium | 1 Low**

---

## 📁 Repository Structure

```
api-security-audit/
│
├── README.md                          ← You are here
│
├── report/
│   └── API_Security_Risk_Analysis_Report.docx   ← Full professional report
│
├── postman-collection/
│   └── API_Security_Audit.postman_collection.json  ← Import into Postman
│
└── screenshots/
    ├── 01_F1_unauthenticated_users_list.png
    ├── 02_F2_bola_user_enumeration.png
    ├── 03_F3_unauthenticated_post_create.png
    ├── 04_F4_rate_limit_missing.png
    ├── 05_F5_excessive_data_exposure.png
    ├── 06_F6_token_not_enforced.png
    └── 07_F7_missing_security_headers.png
```

---

## 🚀 How to Reproduce This Audit

### Step 1: Import the Postman Collection
1. Open Postman
2. Click **Import** → Upload `postman-collection/API_Security_Audit.postman_collection.json`
3. The collection loads with all 10 pre-configured test requests

### Step 2: Run the Tests
Execute each request in order. Each request description explains:
- What finding it tests
- What response to expect
- What the actual (insecure) response is

### Step 3: Capture Screenshots
For each test, screenshot:
- The request URL and method
- The response body (showing data exposure)
- The response headers tab (showing missing headers)

---

## 📖 Key Security Concepts Demonstrated

**BOLA (Broken Object Level Authorization)**
The most critical API vulnerability. Occurs when an API doesn't verify that the requesting user has permission to access a specific resource. Tested by changing the `{id}` parameter in `/users/{id}`.

**Broken Authentication**
When authentication is absent (F1, F3) or exists but isn't enforced (F6). The login mechanism issues tokens but protected endpoints don't validate them.

**Excessive Data Exposure**
APIs returning more fields than necessary. `/users/{id}` returns 15+ fields including geo-coordinates when most use cases require 2-3 fields.

**Missing Rate Limiting**
No throttling on any endpoint means unlimited requests — enabling brute-force, enumeration, and DoS attacks.

**Security Misconfiguration**
Both APIs lack standard HTTP security headers (X-Content-Type-Options, Strict-Transport-Security, Content-Security-Policy, etc.).

---

## 📚 References

- [OWASP API Security Top 10 (2023)](https://owasp.org/www-project-api-security/)
- [API Security Checklist by shieldfy](https://github.com/shieldfy/API-Security-Checklist)
- [JSONPlaceholder](https://jsonplaceholder.typicode.com)
- [ReqRes](https://reqres.in)

---

## ⚠️ Disclaimer

This assessment was conducted **for educational purposes only** on public APIs specifically designed for testing. No real user data was accessed or compromised. All testing was performed using ethical, read-only methods in accordance with responsible disclosure principles.

---

*Future Interns Cyber Security Internship — Task 3 | February 2026*
