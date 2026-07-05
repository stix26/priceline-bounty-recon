# Priceline Bug Bounty Reconnaissance

Bug bounty recon pipeline output for Priceline (hackerone.com/priceline).

## Session: 2026-07-05
- **CORS:** Reflective CORS with `Access-Control-Allow-Credentials: true` on www.priceline.com
- **Accepts `Origin: null`** — potentially exploitable
- **Note:** Cloudflare WAF returns 403 before application content
- **Status:** Informational finding — WAF-limited
