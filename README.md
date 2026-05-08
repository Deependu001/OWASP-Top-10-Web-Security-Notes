# OWASP-Top-10-Web-Security-Notes
Comprehensive beginner-to-advanced OWASP Top 10 notes covering web application vulnerabilities, exploitation techniques, prevention methods, security testing tools, and practical cybersecurity concepts for ethical hacking and penetration testing.


# 🛡️ OWASP Top 10 — Complete Beginner to Advanced Notes for Cybersecurity

> A practical documentation repository covering the **OWASP Top 10 Web Application Security Risks**, attack techniques, vulnerabilities, testing methods, prevention strategies, and security best practices.

---

# 📌 What is OWASP?

**OWASP (Open Worldwide Application Security Project)** is a non-profit organization focused on improving software security.

The **OWASP Top 10** is one of the most important awareness documents for web application security.  
It represents the **10 most critical web security risks** developers, security engineers, and ethical hackers should know.

---

# 🎯 Why OWASP Top 10 Matters

- Helps identify common web vulnerabilities
- Used by penetration testers & bug bounty hunters
- Improves secure coding practices
- Important for web application assessments
- Frequently used in real-world cyber attacks

---

# 🔥 OWASP Top 10 (2021)

| Rank | Vulnerability |
|---|---|
| A01 | Broken Access Control |
| A02 | Cryptographic Failures |
| A03 | Injection |
| A04 | Insecure Design |
| A05 | Security Misconfiguration |
| A06 | Vulnerable & Outdated Components |
| A07 | Identification & Authentication Failures |
| A08 | Software & Data Integrity Failures |
| A09 | Security Logging & Monitoring Failures |
| A10 | Server-Side Request Forgery (SSRF) |

---

# A01 — Broken Access Control

## 📖 Description
Occurs when users can access resources or perform actions outside their intended permissions.

## ⚠️ Examples
- Accessing admin pages without authorization
- IDOR vulnerabilities
- Privilege escalation
- Bypassing access restrictions

## 💥 Example
```bash
https://example.com/user?id=1001
```

Changing:
```bash
id=1002
```

May allow access to another user's account.

## 🔍 Testing Techniques
- Parameter tampering
- Forced browsing
- Horizontal privilege escalation
- Vertical privilege escalation

## 🛡️ Prevention
- Implement role-based access control (RBAC)
- Deny access by default
- Validate permissions server-side
- Use least privilege principle

---

# A02 — Cryptographic Failures

## 📖 Description
Failures related to weak encryption, sensitive data exposure, or insecure transmission.

## ⚠️ Examples
- Weak password hashing
- HTTP instead of HTTPS
- Storing plaintext passwords
- Weak SSL/TLS configurations

## 🔍 Testing Techniques
- Check HTTPS enforcement
- Analyze cookies
- Identify weak hashes
- Inspect data transmission

## 🛠️ Common Weak Algorithms
- MD5
- SHA1
- DES

## ✅ Secure Alternatives
- bcrypt
- Argon2
- AES-256
- TLS 1.2+

## 🛡️ Prevention
- Encrypt sensitive data
- Use strong cryptographic standards
- Implement secure key management
- Disable outdated protocols

---

# A03 — Injection

## 📖 Description
Injection flaws occur when untrusted input is interpreted as commands or queries.

## ⚠️ Types of Injection
- SQL Injection (SQLi)
- Command Injection
- LDAP Injection
- NoSQL Injection
- Cross-Site Scripting (XSS)

---

## 💥 SQL Injection Example

```sql
' OR 1=1 --
```

### Vulnerable Query
```sql
SELECT * FROM users WHERE username='$user';
```

---

## 🔍 SQLMap Basic Usage

```bash
sqlmap -u "http://target.com?id=1"
```

### Database Enumeration
```bash
sqlmap -u "URL" --dbs
```

### Dump Tables
```bash
sqlmap -u "URL" -D database --tables
```

---

## 🛡️ Prevention
- Parameterized queries
- Input validation
- Prepared statements
- ORM frameworks
- Least privilege database accounts

---

# A04 — Insecure Design

## 📖 Description
Security weaknesses caused by poor application architecture or insecure business logic.

## ⚠️ Examples
- No rate limiting
- Weak password reset flows
- Missing threat modeling
- Lack of security controls

## 🛡️ Prevention
- Secure development lifecycle (SDLC)
- Threat modeling
- Security-by-design principles
- Abuse case testing

---

# A05 — Security Misconfiguration

## 📖 Description
Improperly configured systems, frameworks, cloud services, or applications.

## ⚠️ Examples
- Default credentials
- Open cloud storage buckets
- Directory listing enabled
- Verbose error messages

## 🔍 Enumeration Techniques

### Nikto Scan
```bash
nikto -h http://target.com
```

### Nmap Service Detection
```bash
nmap -sV target.com
```

---

## 🛡️ Prevention
- Remove unused services
- Disable directory listing
- Change default credentials
- Secure HTTP headers
- Patch systems regularly

---

# A06 — Vulnerable & Outdated Components

## 📖 Description
Using libraries, frameworks, or software with known vulnerabilities.

## ⚠️ Examples
- Outdated WordPress plugins
- Old Apache versions
- Vulnerable npm packages

## 🔍 Detection Tools
- Nmap NSE scripts
- WPScan
- Dependency Check
- Snyk

---

## 🛠️ Example Commands

### WPScan
```bash
wpscan --url http://target.com
```

### Nmap Vulnerability Scan
```bash
nmap --script vuln target.com
```

---

## 🛡️ Prevention
- Regular patch management
- Remove unused dependencies
- Use dependency scanners
- Monitor CVEs

---

# A07 — Identification & Authentication Failures

## 📖 Description
Weak authentication mechanisms allowing account compromise.

## ⚠️ Examples
- Weak passwords
- Credential stuffing
- Session fixation
- Broken session management

---

## 🔍 Testing Techniques
- Brute force attacks
- Password spraying
- Session token analysis

---

## 🛠️ Hydra Example

```bash
hydra -l admin -P passwords.txt ssh://10.10.10.10
```

---

## 🛡️ Prevention
- Multi-factor authentication (MFA)
- Strong password policies
- Account lockout mechanisms
- Secure session handling

---

# A08 — Software & Data Integrity Failures

## 📖 Description
Failures related to code integrity, software updates, CI/CD pipelines, and insecure deserialization.

## ⚠️ Examples
- Malicious software updates
- Insecure deserialization
- Supply chain attacks

## 💥 Real-World Example
- SolarWinds supply chain attack

## 🛡️ Prevention
- Verify software signatures
- Secure CI/CD pipelines
- Integrity checks
- Trusted dependencies only

---

# A09 — Security Logging & Monitoring Failures

## 📖 Description
Insufficient logging, monitoring, or alerting that prevents detection of attacks.

## ⚠️ Examples
- No failed login logging
- No SIEM monitoring
- Missing audit trails

## 🛡️ Prevention
- Centralized logging
- Real-time alerting
- SIEM implementation
- Log retention policies

---

# A10 — Server-Side Request Forgery (SSRF)

## 📖 Description
Occurs when a server fetches remote resources without validating user-supplied URLs.

## ⚠️ Examples
- Accessing internal services
- Cloud metadata access
- Internal network scanning

---

## 💥 SSRF Payload Example

```bash
http://127.0.0.1/admin
```

### Cloud Metadata Example
```bash
http://169.254.169.254/latest/meta-data/
```

---

## 🛡️ Prevention
- Allowlist URLs/domains
- Disable unnecessary URL schemas
- Network segmentation
- Validate user input

---

# 🧪 Common Tools Used in OWASP Testing

| Tool | Purpose |
|---|---|
| Burp Suite | Web App Testing |
| OWASP ZAP | Vulnerability Scanning |
| SQLMap | SQL Injection |
| Nikto | Web Server Scanning |
| Nmap | Enumeration |
| Hydra | Brute Force Testing |
| Gobuster | Directory Bruteforcing |
| ffuf | Fuzzing |
| WPScan | WordPress Scanning |

---

# 🔥 Useful Commands Cheatsheet

## Gobuster
```bash
gobuster dir -u http://target.com -w wordlist.txt
```

## ffuf
```bash
ffuf -u http://target.com/FUZZ -w wordlist.txt
```

## Nmap
```bash
nmap -sC -sV target.com
```

## Burp Suite Proxy
```bash
127.0.0.1:8080
```

---

# 📚 Important Security Concepts

## 🔹 CIA Triad
- Confidentiality
- Integrity
- Availability

## 🔹 Principle of Least Privilege
Users should only have minimum required permissions.

## 🔹 Defense in Depth
Multiple layers of security controls.

## 🔹 Input Validation
Never trust user input.

---

# 🛠️ Secure Coding Best Practices

- Validate all inputs
- Sanitize outputs
- Use parameterized queries
- Implement proper authentication
- Secure session management
- Use HTTPS everywhere
- Avoid hardcoded secrets
- Implement logging & monitoring

---

# 🔍 OWASP Testing Methodology

1. Reconnaissance
2. Enumeration
3. Vulnerability Identification
4. Exploitation
5. Privilege Escalation
6. Post-Exploitation
7. Reporting

---

# 📖 Recommended Labs & Practice Platforms

## 🧪 Practice Labs
- TryHackMe
- Hack The Box
- PortSwigger Web Security Academy
- DVWA
- OWASP Juice Shop
- Metasploitable

---

# 🚀 Learning Roadmap After OWASP Top 10

- Burp Suite Advanced
- API Security
- JWT Attacks
- Authentication Bypass
- Advanced SQL Injection
- WebSockets Security
- SSRF Exploitation
- Race Conditions
- Bug Bounty Hunting
- Secure Coding

---

# 🏆 Key Takeaways

- OWASP Top 10 forms the foundation of web security
- Most real-world web attacks map to these vulnerabilities
- Understanding both exploitation & mitigation is important
- Hands-on labs are essential for mastery

---

# 📌 Repository Structure Suggestion

```bash
OWASP-Top-10/
│
├── Broken-Access-Control/
├── Cryptographic-Failures/
├── Injection/
├── Insecure-Design/
├── Security-Misconfiguration/
├── Vulnerable-Components/
├── Authentication-Failures/
├── Integrity-Failures/
├── Logging-Monitoring/
├── SSRF/
└── README.md
```

---

# ⭐ Useful Resources

## Official OWASP
https://owasp.org/www-project-top-ten/

## Web Security Labs
https://portswigger.net/web-security

## Practice Labs
https://tryhackme.com

https://www.hackthebox.com

---

# 👨‍💻 Author

Documented as part of my cybersecurity learning journey covering:
- Web Application Security
- Penetration Testing
- Ethical Hacking
- Secure Development Practices

---

# 🚀 Future Updates

> 📌 This repository will continue to grow with:
- Advanced payloads
- Burp Suite labs
- Real-world case studies
- Bug bounty techniques
- Authentication bypass methods
- API security testing
- Advanced exploitation notes

---

# ⭐ If You Found This Useful

Consider starring the repository and following my cybersecurity journey.