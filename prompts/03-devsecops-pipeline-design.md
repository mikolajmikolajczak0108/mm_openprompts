# DevSecOps pipeline design

Use this to design a security pipeline around an actual repository and delivery model, not around a generic diagram.

## Prompt

You are acting as a senior DevSecOps architect.

Design a practical security pipeline for this repository and its deployment model. The result must be implementable by a normal engineering team and must separate useful controls from security theatre.

First inspect the repository and establish:

- application type and languages
- package managers and dependency manifests
- build system
- test framework
- container usage
- infrastructure as code
- deployment target
- CI/CD platform
- artifact/package registries
- cloud provider and runtime where visible
- branch/release strategy
- environments
- secrets model
- current security tooling

Do not choose tools before you understand the project.

Then design the pipeline as a sequence of stages. At minimum consider:

1. Developer workstation / pre-commit
2. Pull request
3. Build
4. Package / artifact creation
5. Pre-production deployment
6. Security validation in a running environment
7. Release / production promotion
8. Post-release monitoring and vulnerability response

For each stage decide whether the following controls are relevant:

- formatting/linting where it prevents risky mistakes
- unit and integration tests
- SAST
- SCA / dependency vulnerability scanning
- dependency policy and version pinning
- secret scanning
- IaC scanning
- container image scanning
- Dockerfile / image hardening checks
- DAST
- API security testing where relevant
- fuzzing where proportionate
- license policy checks
- SBOM generation
- artifact signing
- build provenance / attestations
- integrity verification before deployment
- malware scanning for uploaded or distributed artifacts where relevant
- environment-specific smoke tests
- admission/deployment policy
- runtime vulnerability monitoring

Do not blindly include every control. Explain why each selected control belongs in a particular stage and why omitted controls are not currently worth the cost.

For every control provide:

- purpose
- trigger
- input
- output/evidence
- blocking vs non-blocking behavior
- failure threshold
- false-positive handling
- owner
- where findings are tracked
- expected developer action

Define security gates explicitly.

A gate must have a decision rule, for example:

- block newly introduced Critical/High vulnerabilities with a credible exploit path
- block confirmed hardcoded secrets
- block deployment if required tests fail
- block release when an artifact has no expected provenance or signature
- warn rather than block on low-confidence or low-severity findings

Avoid "zero vulnerabilities allowed" unless the project has a real policy that requires it.

Supply-chain security must be considered. Include, where appropriate:

- protected branches and reviewed changes
- least-privilege CI permissions
- pinned or trusted CI actions/plugins
- isolated and preferably ephemeral build environments
- trusted artifact registries
- SBOM
- signed artifacts
- verifiable build provenance
- dependency update process
- patch and vulnerability response process

Map the proposed design at a high level to NIST SSDF practices. Use SLSA concepts for provenance and build integrity where they make sense, but do not claim a SLSA level unless the required conditions are actually met.

Output structure:

## Current-state summary
What exists today and the most important gaps.

## Proposed pipeline
A stage-by-stage flow. Use a compact table first, then explain the important stages.

## Security gates
List exact blocking criteria and exceptions.

## Tooling options
For each capability suggest 1-3 sensible tools that fit the stack. Prefer existing platform-native capabilities when they are sufficient. Distinguish open-source, platform-native and commercial options.

## CI/CD implementation
If the CI platform is known, provide a concrete pipeline skeleton in its native format. Keep it modular and do not invent credentials, account IDs or environment names.

## Findings workflow
Explain who receives findings, how duplicates are handled, how risk is accepted, and how remediation SLAs could be applied.

## Rollout plan
Split implementation into:
- minimum viable security pipeline
- next maturity step
- advanced supply-chain hardening

## Cost and friction
Call out controls likely to slow builds, create noise or require paid infrastructure.

Important rules:

- Do not design a pipeline that takes 45 minutes for every pull request unless the risk justifies it.
- Put fast, deterministic checks early and expensive dynamic checks later.
- Separate PR feedback from release gates.
- Do not duplicate the same scanner in three products without a reason.
- Prefer incremental scanning and changed-code feedback where possible.
- Treat findings as evidence to triage, not automatically as vulnerabilities.
- Security gates should be risk-based and understandable to developers.

Reference baseline:

- NIST SSDF SP 800-218: https://csrc.nist.gov/pubs/sp/800/218/final
- SLSA specification: https://slsa.dev/spec/v1.2/
- SLSA build provenance: https://slsa.dev/spec/v1.2/build-provenance
- GitHub code scanning concepts: https://docs.github.com/en/code-security/concepts/code-scanning/code-scanning
- GitHub secret scanning concepts: https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning
- OpenSSF Scorecard: https://openssf.org/scorecard/
