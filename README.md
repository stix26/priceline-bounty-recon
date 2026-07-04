# Priceline.com Reconnaissance Summary

## Overview
Subdomain enumeration and reconnaissance scan performed on priceline.com.

## Results

### Subdomains
- **Total subdomains found:** 406
- **Live hosts:** 80

### CORS Misconfiguration
14 hosts reflected the `Access-Control-Allow-Origin: https://evil.com` header, indicating potential CORS misconfiguration:

| Host | Status |
|------|--------|
| ids-qa.priceline.com | Vulnerable |
| wildcard.qaa.priceline.com | Vulnerable |
| qaa.priceline.com | Vulnerable |
| wildcard.preprod.priceline.com | Vulnerable |
| 1psb.priceline.com | Vulnerable |
| www.qaa.priceline.com | Vulnerable |
| www.priceline.com | Vulnerable |
| pkg-whitelabel.priceline.com | Vulnerable |
| offers.priceline.com | Vulnerable |
| experiences.priceline.com | Vulnerable |
| ids.priceline.com | Vulnerable |
| preprod.priceline.com | Vulnerable |
| qa.priceline.com | Vulnerable |
| links.priceline.com | Vulnerable |

### Exposed Endpoints (www.priceline.com)

| Endpoint | Status | Size |
|----------|--------|------|
| /.git/config | 403 | 5354 bytes |
| /.env | 403 | 5354 bytes |
| /robots.txt | 200 | 4163 bytes |
| /sitemap.xml | 200 | 1673 bytes |

`/.git/config` and `/.env` return 403 (blocked but detected). `robots.txt` and `sitemap.xml` are publicly accessible.

### Notable Live Subdomains
- `api.priceline.com` (403)
- `booking.priceline.com` (301 redirect)
- `help.priceline.com` (301 redirect)
- `partners.priceline.com` (301 redirect)
- `careers.priceline.com` (200)
- `cruises.priceline.com` (200)
- `press.priceline.com` (200)
- `customerservice-ccp.priceline.com` (200)
- `flight-deals.priceline.com` (301 redirect)
- `travel.priceline.com` (301 redirect)

### Files Generated
| File | Description |
|------|-------------|
| `subdomains.txt` | 406 subdomains from subfinder |
| `live-hosts.txt` | 80 live hosts with HTTP status codes |
| `cors-check.txt` | CORS misconfiguration scan results |
| `exposed-endpoints.txt` | Common endpoint accessibility check |

## Tools Used
- **subfinder** - subdomain enumeration
- **curl** - live host checking, CORS testing, endpoint discovery
