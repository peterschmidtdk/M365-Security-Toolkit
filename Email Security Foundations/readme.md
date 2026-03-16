# Email Security Foundations

PowerShell scripts for the [Email Security Foundations](https://www.msdigest.net) series on MSDigest.net.

This series covers the full email authentication stack — SPF, DKIM, DMARC, DANE, MTA-STS and BIMI — with configuration walkthroughs for Exchange Online and Microsoft 365. The scripts in this folder are the practical companion to each post.

---

## Scripts

| Script | Blog post | Description |
|---|---|---|
| `Get-DomainEmailSecurityStatus.ps1` | [#01](https://www.msdigest.net) | Quick DNS lookup — shows SPF, DKIM, DMARC, MTA-STS and BIMI status for any domain |


---

## Quick start

The fastest way to see where a domain stands across all email security standards:

```powershell
.\Invoke-EmailSecurityHealthCheck.ps1 -Domain yourdomain.com
```

Example output:

```
========================================
 Email Security Health Check: yourdomain.com
========================================

SPF
  [PASS] SPF record found
         v=spf1 include:spf.protection.outlook.com -all
  [PASS] Hard fail (-all) configured
  [PASS] Exchange Online include present

DKIM
  [PASS] selector1 found: selector1-yourdomain-com._domainkey.yourdomain.onmicrosoft.com
  [PASS] selector2 found: selector2-yourdomain-com._domainkey.yourdomain.onmicrosoft.com

DMARC
  [PASS] DMARC record found
         v=DMARC1; p=reject; rua=mailto:dmarc@yourdomain.com
  [PASS] Policy: reject
  [PASS] Reporting address configured

MTA-STS
  [PASS] MTA-STS DNS record found
  [PASS] MTA-STS policy file accessible
  [PASS] Mode: enforce

BIMI
  [INFO] No BIMI record found

========================================
```

---

## Running against multiple domains

All scripts accept a `-Domain` parameter. To run the health check across multiple domains:

```powershell
$domains = @(
    "yourdomain.com",
    "anotherdomain.com",
    "clientdomain.com"
)

foreach ($domain in $domains) {
    .\Invoke-EmailSecurityHealthCheck.ps1 -Domain $domain
}
```

---

## Exchange Online scripts

Scripts that connect to Exchange Online — `Get-DKIMStatus.ps1` and `Invoke-DKIMKeyRotation.ps1` — require the ExchangeOnlineManagement module and an active connection:

```powershell
Install-Module -Name ExchangeOnlineManagement -Scope CurrentUser
Connect-ExchangeOnline
```

All other scripts in this folder use only `Resolve-DnsName` and `Invoke-RestMethod` — no Exchange Online connection required.

---

## Blog series overview

| Post | Title |
|---|---|
| #01 | [Why email is still the most dangerous attack surface](https://www.msdigest.net) |
| #02 | [The full picture: SPF, DKIM, DMARC, DANE, MTA-STS and BIMI explained](https://www.msdigest.net) |
More Post planned...

---

*Part of the [m365-security-toolkit](https://github.com) repository — scripts for the MSDigest.net blog series by Peter Schmidt.*
