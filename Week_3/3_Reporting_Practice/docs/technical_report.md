# Technical Report

## Target
192.168.31.199 (Metasploitable2 - DVWA)

---

## Vulnerability 1: SQL Injection

### Description
The application is vulnerable to SQL injection through the "id" parameter in the DVWA module. User input is not properly sanitized, allowing attackers to manipulate SQL queries.

### Evidence
Payload:
1' OR '1'='1

Tool Used:
sqlmap

Result:
- Database: dvwa
- Tables: users, guestbook
- Extracted Credentials:
  - admin : password
  - gordonb : abc123

### Impact
- Unauthorized database access
- Exposure of sensitive data
- Account compromise

### Remediation
- Use parameterized queries
- Validate and sanitize inputs

---

## Vulnerability 2: Cross-Site Scripting (XSS)

### Description
Reflected XSS was identified in the web application, allowing execution of malicious scripts.

### Evidence
Payload:
<script>alert(1)</script>

### Impact
- Session hijacking
- Cookie theft
- User impersonation

### Remediation
- Input validation
- Output encoding
- Use secure headers
