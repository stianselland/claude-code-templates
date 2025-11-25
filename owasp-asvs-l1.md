# OWASP ASVS L1 Checklist

This checklist is referenced by the `/security-review` command. Maintain your specific requirements here.

---

## V1: Architecture & Design
- [ ] V1.1.1 - Security controls are centralized
- [ ] V1.1.2 - Components use least privilege

## V2: Authentication
- [ ] V2.1.1 - Passwords are not logged or exposed
- [ ] V2.2.1 - Authentication failures don't reveal valid usernames
- [ ] V2.3.1 - Session tokens invalidated on logout
- [ ] V2.5.1 - No default credentials

## V3: Session Management
- [ ] V3.1.1 - Session tokens generated with sufficient entropy
- [ ] V3.2.1 - Sessions expire after inactivity
- [ ] V3.3.1 - Session tokens not exposed in URLs

## V4: Access Control
- [ ] V4.1.1 - Access control checks performed server-side
- [ ] V4.2.1 - Directory listing disabled
- [ ] V4.3.1 - Access denied by default (allowlist)
- [ ] V4.4.1 - CORS properly configured

## V5: Validation & Encoding
- [ ] V5.1.1 - All input validated (type, length, range)
- [ ] V5.2.1 - Output encoded for context (HTML, JS, SQL)
- [ ] V5.3.1 - Parameterized queries used
- [ ] V5.4.1 - File uploads validated and restricted

## V6: Cryptography
- [ ] V6.1.1 - No hardcoded secrets or keys
- [ ] V6.2.1 - Strong algorithms used (no MD5, SHA1 for security)
- [ ] V6.3.1 - Random values use CSPRNG

## V7: Error Handling & Logging
- [ ] V7.1.1 - Errors don't expose sensitive information
- [ ] V7.2.1 - Sensitive data not logged
- [ ] V7.3.1 - Stack traces not shown to users

## V8: Data Protection
- [ ] V8.1.1 - Sensitive data not cached
- [ ] V8.2.1 - PII handled according to requirements
- [ ] V8.3.1 - Autocomplete disabled for sensitive fields

## V9: Communication
- [ ] V9.1.1 - TLS enforced for sensitive data
- [ ] V9.2.1 - Certificate validation not disabled

## V10: Malicious Code
- [ ] V10.1.1 - No backdoors or undocumented features
- [ ] V10.2.1 - Dependencies from trusted sources

---

**Note:** Update this checklist with your specific ASVS L1 requirements. The `/security-review` command will reference this file when reviewing code changes.
