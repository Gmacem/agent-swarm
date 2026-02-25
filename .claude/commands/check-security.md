# Check Security

Perform a security-focused review of code or a pull request.

## Arguments

- `$ARGUMENTS` — PR number, file path, or directory to review

## Instructions

1. Review the target code for security vulnerabilities:
   - **Injection:** SQL injection, command injection, XSS, template injection.
   - **Authentication/Authorization:** Missing auth checks, privilege escalation.
   - **Data exposure:** Sensitive data in logs, responses, or error messages.
   - **Secrets:** Hard-coded credentials, API keys, tokens.
   - **Dependencies:** Known vulnerable packages.
   - **Input validation:** Missing or inadequate validation at system boundaries.
   - **Cryptography:** Weak algorithms, improper key management.
2. Rate each finding by severity: critical, high, medium, low.
3. Provide specific remediation steps for each finding.
4. Report results and update the task.
