# Security Policy

## Supported Versions

infraHorizon is currently in **Version 0 — Foundation**. No runtime implementation exists yet. The project is in the documentation and architectural planning phase.

| Version | Supported |
|---------|-----------|
| V0 (Foundation) | Documentation / planning only — no runtime |
| V1+ | Not yet released |

---

## Scope

Because V0 contains no deployable runtime, there is currently no attack surface to report against. This policy will expand significantly when V1 (Kubernetes Workload Visualization) is released.

**When runtime code exists, the following will be in scope:**

- Vulnerabilities in the event collection pipeline
- Vulnerabilities in the API layer
- Vulnerabilities in authentication or authorization (when implemented — V0 explicitly excludes auth)
- Any behavior that could allow unauthorized access to Kubernetes cluster data
- Dependency vulnerabilities with known CVEs

**Out of scope:**
- Issues in development tooling only (local dev scripts, test helpers)
- Social engineering attacks
- Issues requiring physical access to infrastructure
- Issues in third-party dependencies without a suggested fix
- Theoretical vulnerabilities without proof-of-concept

---

## Reporting a Vulnerability

If you discover a security vulnerability, **please do not open a public GitHub issue**.

Instead:

1. **Email the maintainers** at the contact listed in the repository's maintainer file.
2. Include:
   - A description of the vulnerability
   - Steps to reproduce (if applicable)
   - Potential impact
   - Any suggested remediation (optional but appreciated)

---

## Response Timeline

| Stage | Target |
|-------|--------|
| Acknowledgement | Within 72 hours |
| Initial assessment | Within 7 days |
| Resolution or workaround | Dependent on severity and complexity |
| Public disclosure | After a fix is available and deployed |

We follow responsible disclosure. We will coordinate with the reporter before any public disclosure and give credit to reporters unless they prefer to remain anonymous.

---

## Security Considerations for Contributors

While V0 contains no runtime code, contributors should keep the following in mind for future contributions:

- **Never commit credentials, tokens, or secrets** — not even in comments or test files.
- **Avoid logging sensitive cluster data** — execution graphs may contain sensitive infrastructure information.
- **Prefer least privilege** — when the platform connects to Kubernetes, request only the permissions actually needed.
- **Treat infrastructure event data as sensitive** — it describes real system behavior and should be handled accordingly.

---

## Disclosure Policy

We are committed to handling security reports responsibly and transparently. Once a fix is available:

- We will publish a security advisory on the repository.
- We will credit the reporter (with their consent).
- We will document the fix in the relevant ADR or changelog.

Thank you for helping keep infraHorizon and its users safe.
