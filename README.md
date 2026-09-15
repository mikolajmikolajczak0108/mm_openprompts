# mm_openprompts

A public collection of prompts, AI workflows and practical instructions I actually use or adapt in real projects.

This repository is not meant to be a list of one-line "magic prompts". Most of the files are deliberately specific: they define the role, scope, constraints, expected output and stopping points so the model has enough context to do useful work.

## Prompts

| File | Use case |
| --- | --- |
| [01 - Immersive 3D product website](prompts/01-immersive-3d-product-site.md) | Build a cinematic Three.js / React Three Fiber product site around a real GLB model. This is the prompt used for the Loki Bone demo. |
| [02 - Secure code review](prompts/02-secure-code-review.md) | Risk-based application security review with evidence, exploitability, severity and concrete fixes. |
| [03 - DevSecOps pipeline design](prompts/03-devsecops-pipeline-design.md) | Design a CI/CD security pipeline with sensible gates, SAST, SCA, secrets, IaC, container scanning, DAST, SBOM and supply-chain controls. |
| [04 - UI/UX redesign](prompts/04-ui-ux-redesign.md) | Redesign an existing interface without turning it into generic AI UI, while preserving product intent and accessibility. |
| [05 - SEO audit with human approval](prompts/05-seo-audit-hitl.md) | Two-stage SEO workflow: analysis first, then a human decision point before any implementation plan. |
| [06 - Threat model](prompts/06-threat-model.md) | Architecture-led threat modeling with trust boundaries, data flows, STRIDE-style analysis and prioritized mitigations. |

## 3D skill used in the Loki demo

The Loki prompt works well together with the `immersive-3d-web` Claude Code skill:

https://github.com/gabremoku/immersive-3d-web

For the 3D asset itself, you can model it manually in Blender, use a hosted image-to-3D service such as Tripo3D, or run a local image-to-3D workflow in ComfyUI. Local generation is much more hardware-sensitive: VRAM is the GPU memory used by the model and intermediate tensors, while system RAM is used by the rest of the workflow and any CPU/offload path. If VRAM is exhausted, generation may fail with an out-of-memory error or become significantly slower when work is moved off the GPU.

## Notes

These prompts are starting points, not universal templates. Replace assumptions, stack choices and acceptance criteria with the ones that fit the actual project. For security work in particular, the model should distinguish verified findings from hypotheses and should not invent missing architecture, controls or vulnerabilities.

The security and web prompts here are informed by public guidance such as NIST SSDF, OWASP, W3C WCAG/WAI, Google Search Central and SLSA. Links are included inside the relevant files.
