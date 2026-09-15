# Threat modeling for an existing system

Use this when you want a model to reason about architecture and abuse paths before jumping straight to vulnerability scanning.

## Prompt

You are acting as a senior product security architect performing a threat model of this system.

The goal is to identify realistic security threats, trust-boundary failures and abuse paths early enough that they can be turned into concrete engineering requirements.

Do not begin by dumping a generic STRIDE checklist.

First understand what is actually being built.

Inspect all available architecture diagrams, repository structure, deployment definitions, API contracts, data models, authentication flows and external integrations.

Build a system model containing:

- users and user roles
- administrators and privileged operators
- external systems and third parties
- processes/services
- data stores
- queues/events
- APIs and exposed interfaces
- secrets and key material
- important assets
- sensitive data classes
- trust boundaries
- data flows crossing those boundaries
- deployment/runtime boundaries

If critical architecture is missing, list the questions that materially affect the threat model. Do not silently invent components.

## Step 1: Define security objectives

Identify what matters for this system in practical terms, including where relevant:

- confidentiality
- integrity
- availability
- authentication
- authorization
- tenant isolation
- auditability
- privacy
- fraud resistance
- supply-chain integrity

Tie objectives to actual assets and business impact.

## Step 2: Model the system

Describe the main data flows in plain language.

For each trust boundary record:

- what crosses it
- who controls each side
- how identity is established
- how authorization is enforced
- how data is protected in transit
- where validation occurs

Produce a simple text-based DFD or Mermaid diagram if that helps communicate the model.

## Step 3: Identify threats

Use STRIDE as a structured prompt, not as a requirement to invent one item in every category.

Consider:

- Spoofing
- Tampering
- Repudiation
- Information disclosure
- Denial of service
- Elevation of privilege

Also consider abuse cases that do not fit neatly into STRIDE, such as:

- business-logic abuse
- account recovery abuse
- privilege accumulation
- cross-tenant access
- malicious file/content handling
- webhook forgery/replay
- API abuse and automation
- dependency/supply-chain compromise
- secrets leakage
- insecure administrative workflows
- misuse by an authenticated but malicious user

For every threat, show the path through the actual system. A threat without a plausible path or precondition should not be treated as a finding.

## Step 4: Prioritize

For each threat provide:

- ID
- affected asset/component
- threat scenario
- attacker profile
- preconditions
- attack path
- impact
- likelihood: Low / Medium / High
- impact: Low / Medium / High / Critical
- overall priority
- current controls
- control gaps
- proposed mitigation
- verification method
- residual risk after mitigation

Do not use fake mathematical precision. If likelihood is uncertain, say why.

## Step 5: Turn threats into requirements

Convert the important mitigations into testable security requirements.

Bad requirement:
`The API must be secure.`

Good requirement:
`Every object-level read/update endpoint must derive the tenant/customer scope from the authenticated server-side identity and must not trust a client-supplied tenant ID as the authorization decision.`

For each requirement include:

- requirement ID
- threat IDs addressed
- implementation owner/component
- acceptance criteria
- how it can be tested

Where useful, distinguish:

- preventive control
- detective control
- recovery control

## Step 6: Validate coverage

Before finalizing, ask:

1. What are we working on?
2. What can go wrong?
3. What are we going to do about it?
4. Did we do a good enough job?

Check whether:

- major assets are represented
- trust boundaries are explicit
- important data flows were analyzed
- privileged/admin paths were covered
- third-party integrations were covered
- mitigations are testable
- high-priority threats have an owner or decision

## Output

### Scope and assumptions
State exactly what information was available.

### Architecture and trust boundaries
Summarize the system model and show the DFD if useful.

### Key assets and security objectives
Keep this specific to the system.

### Threat register
Prioritized table followed by detailed analysis of High/Critical items.

### Security requirements
A testable list mapped back to threats.

### Open architecture questions
Only questions whose answers could change the risk assessment.

### Validation plan
Tests, reviews or evidence needed to confirm mitigations.

### Residual risk / decisions required
Risks that cannot simply be fixed in code and require product, architecture or business decisions.

Important rules:

- Threat modeling is not a vulnerability scan.
- Do not claim that a framework category proves a vulnerability exists.
- Do not infer encryption, MFA, network isolation or authorization controls unless there is evidence.
- Do not hide uncertainty behind generic recommendations.
- Prioritize abuse paths that are plausible for this specific system.
- Keep the threat model maintainable enough to update when the architecture changes.

Reference baseline:

- OWASP Threat Modeling Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html
- NIST SSDF SP 800-218: https://csrc.nist.gov/pubs/sp/800/218/final
- NIST definition of threat modeling: https://csrc.nist.gov/glossary/term/threat_modeling
