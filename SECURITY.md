# Security Policy

KDBL Consulting Limited takes the security of the KDBL Knowledge Layer seriously.
This policy covers how to report a vulnerability and how we secure what we ship.

## Reporting a vulnerability

**Please report suspected vulnerabilities privately to [security@kdbl.co.uk](mailto:security@kdbl.co.uk).**
Do **not** open a public GitHub issue for security matters.

When reporting, please include:

- the affected image(s) and version/tag,
- a description of the issue and its impact, and
- steps to reproduce or a proof of concept, where possible.

We aim to acknowledge legitimate reports within **2 business days** and to keep
you informed as we investigate and remediate. We ask that you give us a
reasonable opportunity to remediate before any public disclosure, and that you
do not access, modify, or exfiltrate data that is not yours while testing. We
practise coordinated disclosure and are glad to credit reporters who wish it.

## What we do to secure what we ship

- **Daily vulnerability scanning.** Every published image is scanned daily with
  [Trivy](https://github.com/aquasecurity/trivy) for known OS and dependency
  vulnerabilities. A rolling summary is published in
  [`SECURITY-REPORT.md`](SECURITY-REPORT.md), with dated history under
  [`security/`](security/) and detailed reports retained as workflow artifacts.
- **Software Bill of Materials (SBOM).** Each image is built with an SBOM and a
  build provenance attestation, so you can inventory exactly what it contains.
- **Minimal, current base images** and a least-privilege runtime posture
  (non-root where possible; capabilities granted only where a backend requires
  them).
- **Image signing** with [cosign](https://github.com/sigstore/cosign). Releases
  are signed with our key — the public key is published here as
  [`cosign.pub`](cosign.pub). Verify an image before you run it:

  ```bash
  cosign verify --key cosign.pub ghcr.io/kdbl-consulting/kdbl-worker:<version>
  ```

> Detailed, per-CVE breakdowns are available to licensed and evaluation
> customers on request. We publish summaries publicly rather than a full
> exploitable-CVE inventory, to avoid handing attackers a roadmap.

## Supported versions

Security fixes are provided for the **latest released minor version**. We
recommend pinning deployments to a released version tag (for example `:0.1`)
rather than `:latest`, and updating promptly when a new release is published.

| Version | Supported |
| --- | --- |
| Latest released minor | ✅ |
| Older minors | ⚠️ best-effort / on request |

## Scope

This policy covers the KDBL Knowledge Layer container images published to
`ghcr.io/kdbl-consulting/*` and the contents of this repository. Vulnerabilities
in third-party or upstream open-source components should also be reported to us;
we will coordinate with upstream as appropriate.

---

**KDBL Consulting Limited** · [kdbl.co.uk](https://kdbl.co.uk) ·
security@kdbl.co.uk · Company no. 15430964.
