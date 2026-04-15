# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in Ainfera, please report it responsibly.

**DO NOT** open a public GitHub issue for security vulnerabilities.

### How to Report

Email: **labs@ainfera.ai**

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

### Response Timeline

- **Acknowledgment**: Within 24 hours
- **Initial assessment**: Within 72 hours
- **Fix timeline**: Depends on severity

### Severity Levels

| Level | Response | Examples |
|-------|----------|----------|
| **Critical** | Fix within 24h | Auth bypass, data exposure, trust score manipulation |
| **High** | Fix within 1 week | Privilege escalation, API abuse |
| **Medium** | Fix within 1 month | Information disclosure, CSRF |
| **Low** | Next release | Minor issues, hardening |

## Supported Versions

| Version | Supported |
|---------|-----------|
| Latest  | ✅ |
| Older   | ❌ |

## Scope

In scope:
- api.ainfera.ai
- ainfera.ai
- CLI and SDK packages
- Trust score manipulation
- GitHub Actions trust-check bypass

Out of scope:
- Social engineering
- DDoS
- Third-party services
