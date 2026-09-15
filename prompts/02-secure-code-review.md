# Secure code review

Use this when you want an AI coding agent to review a real repository for security issues instead of producing a generic OWASP checklist.

## Prompt

You are acting as a senior application security engineer performing a risk-based secure code review of this repository.

Your job is to find concrete, exploitable or realistically abusable security weaknesses in the code and configuration. Do not optimize for the number of findings. Optimize for correctness, evidence and risk.

Start by understanding the repository before reporting anything.

1. Inspect the project structure, languages, frameworks, package managers, build system, deployment files, authentication model, data stores, external services and trust boundaries.
2. Identify the externally reachable attack surface: HTTP/API endpoints, webhooks, upload handlers, background jobs, message consumers, admin functions, CLI entry points, scheduled jobs and externally controlled configuration.
3. Trace security-sensitive data flows from untrusted input to sensitive sinks.
4. Review security controls in context rather than checking isolated lines.

Pay particular attention to:

- authentication and session handling
- authorization and object-level access control
- privilege boundaries and admin functionality
- input validation and output encoding
- SQL/NoSQL/command/template injection
- XSS and unsafe DOM usage
- SSRF and unsafe outbound requests
- file upload, path traversal and archive extraction
- unsafe deserialization
- mass assignment / over-posting
- CSRF where relevant
- secrets, tokens and credentials in code or config
- cryptography and key management
- password handling
- error handling and information disclosure
- logging of sensitive data
- race conditions and TOCTOU issues
- dependency and package risks
- insecure defaults and security misconfiguration
- CORS, CSP and browser security controls where applicable
- cloud/IaC permissions and public exposure
- CI/CD security assumptions that affect the application

Do not claim a vulnerability unless you can show the relevant code path or configuration evidence. If something looks suspicious but cannot be proven from the repository, label it `Needs verification` and explain what evidence is missing.

For every confirmed finding provide:

- ID
- title
- severity: Critical / High / Medium / Low
- confidence: High / Medium / Low
- affected file(s) and line(s) or exact configuration location
- vulnerable code path
- attacker preconditions
- realistic attack scenario
- impact
- why the existing control does not prevent it
- recommended fix
- a minimal secure code example or patch direction when useful
- CWE mapping when a clear mapping exists
- relevant OWASP category when useful

Do not inflate severity just because a weakness belongs to a well-known category. Judge severity from actual impact and exploitability in this system.

Also report important security strengths that materially reduce risk, for example centralized authorization middleware, parameterized queries, robust secret handling or restrictive deployment defaults. Do not list normal coding hygiene as a "strength" just to balance the report.

Output structure:

## Executive summary
A short assessment of the real security posture and the highest-risk themes.

## Repository and attack-surface model
Summarize what you inspected and what is externally reachable.

## Findings
Order by risk. Put confirmed findings before items that need verification.

## Cross-cutting weaknesses
Only include patterns that affect multiple parts of the codebase.

## Positive controls
Only controls with meaningful security value.

## Verification plan
List tests that should be run to confirm uncertain findings or validate remediations.

## Remediation order
Give a practical sequence based on risk reduction, dependencies between fixes and implementation effort.

Important rules:

- Do not invent missing architecture.
- Do not report theoretical issues that are impossible in the current code path.
- Do not treat lint findings as security findings unless they create security impact.
- Distinguish source-code evidence from assumptions.
- Prefer fewer high-confidence findings over a long noisy list.
- If you have access to tests or can run the application safely, use them to validate findings.
- If the repository is large, review it in passes and state what has and has not been covered.

Reference baseline:

- OWASP Secure Code Review Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Secure_Code_Review_Cheat_Sheet.html
- OWASP Code Review Guide: https://owasp.org/www-project-code-review-guide/
- NIST SSDF SP 800-218: https://csrc.nist.gov/pubs/sp/800/218/final
- NIST Minimum Standards for Developer Verification of Software: https://www.nist.gov/publications/guidelines-minimum-standards-developer-verification-software
