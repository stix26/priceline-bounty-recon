# Priceline Bug Bounty Recon — 2026-07-05

**HackerOne:** Priceline  
**Scope:** priceline.com  
**Methodology:** Full recon pipeline (subfinder → live probing → CORS → exposed files → nuclei → ffuf)

## Summary

| Step | Status | Findings |
|------|--------|----------|
| Subdomain Enumeration | ✅ | 396 subdomains found |
| Live Probing | ✅ | 7 key subdomains checked |
| CORS Testing | ✅ | **HIGH: www.priceline.com reflects origin with credentials** |
| Exposed Files | ✅ | All paths return 403 |
| Nuclei Scan | ✅ | Azure AD tenant info |
| FFUF Fuzzing | ✅ | Common paths scanned |

## CORS Results
- **www.priceline.com** — `access-control-allow-origin: https://evil.com` + `access-control-allow-credentials: true` 🔴
- All others — No CORS headers

## Key Subdomains Live
- www.priceline.com (403)
- api.priceline.com (403)
- booking.priceline.com (301)
- priceline.com (301)

## Nuclei
- **Azure Domain Tenant:** priceline.com → Azure AD (tenant: adbc8019-8aa3-46e1-a416-f2e7473b96f3)

## ⚠️ Findings to Report
1. **CORS Misconfiguration on www.priceline.com** — Reflects arbitrary origin with `Access-Control-Allow-Credentials: true`. This is a high-severity finding allowing authenticated data exfiltration.
