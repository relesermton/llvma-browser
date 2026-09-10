# Security Policy

The LLVMA team takes the security of our open-source search engine, indexing pipeline, and AI integration seriously. We appreciate your efforts to responsibly disclose vulnerabilities to us.

---

## Supported Versions

Only the latest stable minor release and active release candidates receive security patches:

| Version | Supported          |
| ------- | ------------------ |
| `0.2.x` | :white_check_mark: |
| `0.1.x` | :x:                |
| `< 0.1` | :x:                |

---

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.**

### How to Report

To report a vulnerability privately, use one of the following methods:

1. **GitHub Private Advisory (Preferred)**:
   Go to the **Security** tab of the LLVMA repository, click **Advisories**, and select **Report a vulnerability**.

2. **Email**:
   Send your report to **security@llvma.dev** (or the repository maintainer's primary contact).

### What to Include

Please include as much detail as possible to help us triage and reproduce the issue quickly:

- Type of issue (e.g., SSRF in web crawler, prompt injection leading to RCE, unauthorized index access, memory leak).
- Clear, step-by-step instructions or a minimal Proof of Concept (PoC).
- The version, commit hash, or environment where the vulnerability was found.
- Any suggested patches or mitigations, if known.

---

## Response Process

When you submit a report, here is what you can expect:

1. **Acknowledgment**: We will acknowledge receipt of your report within **48 hours**.
2. **Assessment**: We will investigate and confirm whether the issue is valid, assigning it an initial severity score (CVSS).
3. **Fix & Verification**: A patch will be developed in a private security fork. We may ask you to review or test the fix.
4. **Coordinated Disclosure**: Once the fix is published in a new release, we will credit your report in the release notes and advisory (unless you prefer to remain anonymous).

We request that you maintain confidentiality until an official fix is released.

---

## Security Scope & Threat Model

Special considerations for LLVMA search engine deployments:

- **Web Crawlers**: Protections against Server-Side Request Forgery (SSRF) to prevent local network scanning.
- **RAG & LLM Security**: Defenses against prompt injection and cross-document data leakage between multi-tenant indexes.
- **Data Privacy**: Preventing leaks of indexing tokens, local vector store contents, or API credentials via endpoints or logs.
