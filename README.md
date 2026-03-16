# m365-security-toolkit

A collection of PowerShell scripts for Microsoft 365 security, compliance and administration — built alongside the blog series on [MSDigest.net](https://www.msdigest.net) by [Peter Schmidt](https://www.msdigest.net/about).

Every script in this repository has a corresponding blog post that explains the concept, walks through the configuration and provides context for when and why to use it. The scripts are designed to be practical, readable and safe to run in production environments — with output that makes sense to both engineers and the people they report to.

---

## Repository structure

```
m365-security-toolkit/
├── email-security-foundations/   # SPF, DKIM, DMARC, DANE, MTA-STS, BIMI
├── defender-for-office-365/      # MDO policies, quarantine, attack simulation
├── m365-security-posture/        # Secure Score, tenant health, posture reporting
├── purview/                      # Sensitivity labels, DLP, retention, eDiscovery
├── copilot-agent-security/       # Copilot readiness, agent identity, audit
└── tenant-to-tenant-migrations/  # Identity, mail, Teams, SharePoint migration
```

---

## Blog series

| Series | Posts | Repository folder |
|---|---|---|
| [Email Security Foundations](https://www.msdigest.net) | 12 posts | `email-security-foundations/` |
| [Defender for Office 365](https://www.msdigest.net) | 16 posts | `defender-for-office-365/` |
| [Microsoft 365 Security Posture](https://www.msdigest.net) | 13 posts | `m365-security-posture/` |
| [Microsoft Purview](https://www.msdigest.net) | 20 posts | `purview/` |
| [Copilot and Agent Security](https://www.msdigest.net) | 12 posts | `copilot-agent-security/` |
| [Tenant-to-Tenant Migrations](https://www.msdigest.net) | 14 posts | `tenant-to-tenant-migrations/` |

---

## Prerequisites

Most scripts in this repository require one or more of the following PowerShell modules. Install them before running:

```powershell
# Exchange Online Management
Install-Module -Name ExchangeOnlineManagement -Scope CurrentUser

# Microsoft Graph (for Entra and broader M365 queries)
Install-Module -Name Microsoft.Graph -Scope CurrentUser

# Azure AD / Entra ID
Install-Module -Name AzureAD -Scope CurrentUser
```

Individual script folders note any additional module requirements in their own README.

---

## Usage

Each script is self-contained and includes a parameter block at the top. Most accept at minimum a `-Domain` or `-TenantId` parameter. Run scripts with the `-?` flag to see available parameters:

```powershell
.\EmailSecurityHealthCheck.ps1 -?
```

Scripts that connect to Exchange Online or Microsoft Graph will prompt for authentication unless you pass credentials or use an existing session.

---

## Contributing

Found a bug, have an improvement or want to add a script that fits the series? Pull requests are welcome. Please keep scripts consistent with the existing style — parameter blocks at the top, `Write-Host` output with `-ForegroundColor` for readability, and a comment block at the top linking to the relevant blog post.

---

## Disclaimer

These scripts are provided as-is for educational and administrative use. Always test in a non-production environment before running against a live tenant. The author takes no responsibility for unintended changes to your environment.

---

## Author

**Peter Schmidt** — Microsoft 365 consultant, security architect and writer.

- Blog: [msdigest.net](https://www.msdigest.net)
- LinkedIn: [linkedin.com/in/pschmidt](https://www.linkedin.com/in/petsch)

---

*Scripts are added as blog posts are published. Star the repository to follow along.*
