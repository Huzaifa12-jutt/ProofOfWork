# Security Policy

**ProofOfWork** takes security and candidate data privacy seriously. This document outlines our vulnerability disclosure policy and core architectural security principles.

---

## 🛡️ Core Security Architecture Rules

Every developer contributing to ProofOfWork must adhere to these golden security standards:

1. **Passwords & Hashing:**
   - Always hash passwords with **Argon2id**.
   - Plaintext passwords must NEVER be saved in the database or logged in application logs.

2. **Authentication & Sessions:**
   - Use secure, `HttpOnly`, `SameSite=Lax/Strict` cookies over HTTPS for JWT tokens.
   - Never trust frontend state for backend authorization. Always verify identity and organization membership on every protected API endpoint.

3. **Protection Against Data Leaks (IDOR):**
   - Every database query must verify that the requesting user's organization owns the requested resource (assessments, candidate submissions, recruiter notes).
   - Candidate API responses must NEVER contain question answer keys or private reviewer notes.

4. **Candidate Code Execution:**
   - Candidate-submitted code must **NEVER** run inside the main API server process. Code sandboxing requires an isolated execution environment.

5. **Secrets & Credentials:**
   - Never commit API keys, database passwords, or `.env` files to Git.
   - Use environment variables exclusively.

---

## 🚨 Reporting a Vulnerability

If you discover a security vulnerability within ProofOfWork:

1. **Do not create a public GitHub issue.**
2. Send an email to the security lead or create a private security advisory on GitHub under the **Security** tab.
3. Include detailed reproduction steps and impact assessment.
4. Allow reasonable time for the engineering team to address the issue before public disclosure.
