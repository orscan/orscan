# ORSCAN — Website Intelligence Platform

> **AI-powered website scanner. Brutally honest. Brutally fast.**

[![Version](https://img.shields.io/badge/version-v2.4-8c8880?style=flat-square)](https://github.com/orscan/orscan/releases)
[![License](https://img.shields.io/badge/license-MIT-8c8880?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/status-stable-8a9a80?style=flat-square)](https://status.orscan.io)
[![API](https://img.shields.io/badge/REST-API-3a3731?style=flat-square)](https://docs.orscan.io)

ORSCAN scans any website and delivers a comprehensive analysis of **SEO, Performance, Security, Accessibility, and Core Web Vitals** — in under 10 seconds. No login required. No vague suggestions. Just the truth your agency won't tell you.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Quick Start](#quick-start)
- [API Reference](#api-reference)
- [Scan Modules](#scan-modules)
- [ORBOT AI Agent](#orbot-ai-agent)
- [Configuration](#configuration)
- [Output Formats](#output-formats)
- [Pricing](#pricing)
- [Self-Hosting](#self-hosting)
- [Contributing](#contributing)
- [Changelog](#changelog)

---

## Overview

```bash
# Basic scan via cURL
curl -X POST https://api.orscan.io/v1/scan \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer orsk_your_api_key" \
  -d '{"url": "https://yourwebsite.com", "modules": ["seo", "performance", "security"]}'
```

**Example response scores:**

| SEO | Performance | Security | Accessibility | UX |
|-----|------------|----------|---------------|----|
| 86  | 72         | 94       | 64            | 78 |

---

## Features

### Free Modules
| Module | Key | Checks | Avg Time |
|--------|-----|--------|----------|
| SEO Deep Audit | `seo` | 18 checks | ~0.8s |
| Core Web Vitals | `performance` | 12 checks | ~1.4s |
| Security Headers | `security` | 9 checks | ~0.6s |
| Mobile Optimization | `mobile` | 7 checks | ~0.9s |
| Schema Markup | `schema` | 6 checks | ~0.5s |

### Premium Modules
| Module | Key | Checks | Avg Time |
|--------|-----|--------|----------|
| Accessibility WCAG 2.2 | `accessibility` | 22 checks | ~1.1s |
| Link Audit | `links` | 5 checks | ~2.0s |
| Competitor Analysis | `competitor` | Top 3 rivals | ~3.5s |
| AI Critique (ORBOT) | `ai_critique` | LLM analysis | ~4.2s |

> **Note:** All modules can run simultaneously. Full scan with all 9 modules takes approximately 8–12 seconds.

---

## Quick Start

### Option A — Web Interface

Visit [orscan.io](https://orscan.io), paste your URL, and get results instantly.

> Free tier: 3 scans/day · SEO, Performance, Security, Mobile, Schema · No account needed

### Option B — REST API

**Step 1:** Get your API key at `orscan.io/signup` → Dashboard → API Keys → Generate New Key. Keys start with `orsk_`.

**Step 2:** Make your first scan.

```bash
# cURL
curl -X POST https://api.orscan.io/v1/scan \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer orsk_your_api_key" \
  -d '{
    "url": "https://yourwebsite.com",
    "modules": ["seo", "performance", "security"]
  }'
```

```javascript
// JavaScript / Node.js
const response = await fetch('https://api.orscan.io/v1/scan', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${process.env.ORSCAN_API_KEY}`
  },
  body: JSON.stringify({
    url: 'https://yourwebsite.com',
    modules: ['seo', 'performance', 'security', 'accessibility'],
    options: {
      depth: 3,          // crawl depth 1–10
      screenshots: true, // capture full-page screenshots
      ai_critique: true  // enable ORBOT (Premium)
    }
  })
});

const scan = await response.json();
console.log(scan.scores.seo); // → 86
```

```python
# Python
import requests

response = requests.post(
    "https://api.orscan.io/v1/scan",
    headers={"Authorization": f"Bearer {api_key}"},
    json={
        "url": "https://yourwebsite.com",
        "modules": ["seo", "performance", "security"]
    }
)

data = response.json()
print(data["scores"]["seo"])          # 86
print(len(data["issues"]))            # 5
print(data["ai_critique"]["summary"]) # ORBOT response
```

**Step 3:** For deep scans with all modules, poll results using the returned `scan_id`.

**Step 4 (Optional):** Set up webhooks at `orscan.io/dashboard/webhooks` to receive results in real-time.

---

## API Reference

**Base URL:** `https://api.orscan.io/v1`  
**Auth:** All requests require `Authorization: Bearer <api_key>` header.

### Endpoints

#### `POST /scan` — Initiate a new scan

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | ✓ | Target URL including protocol (`https://`) |
| `modules` | string[] | ✓ | Modules to run (see [Scan Modules](#scan-modules)) |
| `options.depth` | integer | — | Crawl depth 1–10. Default: `3` |
| `options.screenshots` | boolean | — | Capture full-page screenshots. Default: `false` |
| `options.ai_critique` | boolean | — | Enable ORBOT AI analysis (Premium). Default: `false` |
| `webhook_url` | string | — | Endpoint to receive completed scan via POST |

#### `GET /scan/:scan_id` — Get scan results

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `scan_id` | string | ✓ | Scan ID from POST /scan response. Format: `scan_xxxxxxxxxxxxxxxx` |

#### `GET /scans` — List all scans (paginated)

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `limit` | integer | — | Results per page. Default: `20`, Max: `100` |
| `cursor` | string | — | Pagination cursor from previous response |

#### `POST /orbot/chat` — Chat with ORBOT *(Premium)*

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `scan_id` | string | ✓ | Scan ID to provide ORBOT context |
| `message` | string | ✓ | Natural language question. Max 2,000 chars |
| `history` | object[] | — | Previous turns for multi-turn context `[{role, content}]` |

### Response Format

```json
{
  "scan_id":     "scan_k2m9x7dn4qfp",
  "url":         "https://yourwebsite.com",
  "status":      "complete",
  "scanned_at":  "2025-04-12T08:22:14Z",
  "duration_ms": 2340,

  "scores": {
    "seo": 86, "performance": 72, "security": 94,
    "accessibility": 64, "ux": 78
  },

  "issues": [
    {
      "id":       "seo_meta_missing",
      "module":   "seo",
      "severity": "critical",
      "title":    "Missing meta descriptions",
      "detail":   "4 pages have no meta description",
      "pages":    ["/about", "/services", "/blog", "/contact"],
      "fix":      "Add unique meta descriptions under 160 chars"
    }
  ],

  "vitals": {
    "lcp": 3.4, "fid": 45, "cls": 0.04, "ttfb": 820, "fcp": 1.9
  },

  "tech_stack": {
    "cms": "WordPress", "server": "Nginx", "cdn": null, "ssl_days": 284
  },

  "ai_critique": {
    "summary":  "Strong security posture. SEO needs work on meta and H1 tags...",
    "roadmap":  ["Fix meta descriptions (1h)", "Compress images (2h)"],
    "orbot_id": "orb_9xdk2m"
  }
}
```

### HTTP Status Codes

| Code | Status | Notes |
|------|--------|-------|
| `200` | OK | Scan completed successfully |
| `202` | Accepted | Scan queued — poll with `scan_id` |
| `400` | Bad Request | Invalid URL or missing required fields |
| `401` | Unauthorized | Invalid or missing API key |
| `402` | Payment Required | Premium-only module on free plan |
| `429` | Rate Limited | Free: 3/day · Pro: 500/day · Enterprise: custom |
| `500` | Server Error | Check [status.orscan.io](https://status.orscan.io) |

---

## Scan Modules

| Module | Key | Checks | Free | Pro | Avg Time |
|--------|-----|--------|------|-----|----------|
| SEO Audit | `seo` | 18 | ✓ | ✓ | ~0.8s |
| Performance | `performance` | 12 | ✓ | ✓ | ~1.4s |
| Security | `security` | 9 | ✓ | ✓ | ~0.6s |
| Mobile UX | `mobile` | 7 | ✓ | ✓ | ~0.9s |
| Schema Markup | `schema` | 6 | ✓ | ✓ | ~0.5s |
| Accessibility | `accessibility` | 22 (WCAG 2.2) | — | ✓ | ~1.1s |
| Link Audit | `links` | 5 | — | ✓ | ~2.0s |
| Competitor | `competitor` | Top 3 rivals | — | ✓ | ~3.5s |
| AI Critique | `ai_critique` | ORBOT LLM | — | ✓ | ~4.2s |

---

## ORBOT AI Agent

ORBOT is ORSCAN's built-in AI analyst. It reads your full scan report and answers questions in natural language — explaining issues, generating fix plans, rewriting copy, and building prioritized roadmaps on demand.

> **Premium feature.** ORBOT is available on Pro ($19/mo) and above. Demo mode available in the web UI for free users.

### Capabilities

- **Natural Language Q&A** — Ask "Why is my SEO score low?" and get a specific, data-backed answer
- **Copy Rewriter** — Request optimized meta descriptions, H1 tags, page headlines, or full rewrites
- **Fix Roadmap Generator** — Prioritized, time-estimated action plan for every identified issue
- **Competitor Breakdown** — Detailed keyword gap analysis vs. specific competitors
- **API Integration** — Compatible with OpenAI, Anthropic, Gemini, or any custom LLM backend

### Example

```javascript
// Chat with ORBOT about a specific scan
const chat = await fetch('https://api.orscan.io/v1/orbot/chat', {
  method: 'POST',
  headers: { 'Authorization': `Bearer ${apiKey}` },
  body: JSON.stringify({
    scan_id: 'scan_k2m9x7dn4qfp',
    message: 'What is the single biggest issue hurting my SEO right now?'
  })
});
// → { reply: "Your biggest issue is missing meta descriptions on 4 pages..." }
```

```python
# Use ORSCAN data with your own Anthropic integration
import anthropic

scan_data = orscan_client.scan("https://yoursite.com")

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-opus-4-5",
    max_tokens=1024,
    messages=[{
        "role": "user",
        "content": f"Scan results: {scan_data}\nQ: What is the highest-impact fix?"
    }]
)
```

---

## Configuration

Configuration is managed through environment variables. Create a `.env` file in the project root for self-hosted deployments.

| Variable | Default / Example | Required |
|----------|-------------------|----------|
| `ORSCAN_API_KEY` | `orsk_xxxxxxxxxx` | **Yes** |
| `ORSCAN_BASE_URL` | `https://api.orscan.io/v1` | No |
| `ORSCAN_TIMEOUT` | `30000` (ms) | No |
| `ORSCAN_DEFAULT_MODULES` | `seo,performance,security` | No |
| `ORSCAN_WEBHOOK_SECRET` | `whsec_xxxxxxxxxx` | No |
| `ORBOT_ENABLED` | `false` | No |
| `ORBOT_LLM_PROVIDER` | `anthropic \| openai \| custom` | No |
| `ORBOT_LLM_API_KEY` | `sk-xxxxxxxx` | No |
| `SCAN_CRAWL_DEPTH` | `3` | No |
| `SCAN_MAX_PAGES` | `100` | No |

### Sample `.env`

```env
# ORSCAN Configuration
ORSCAN_API_KEY=orsk_your_api_key_here
ORSCAN_TIMEOUT=30000
SCAN_CRAWL_DEPTH=3
SCAN_MAX_PAGES=100
ORSCAN_DEFAULT_MODULES=seo,performance,security,mobile,schema

# ORBOT AI Agent (Premium)
ORBOT_ENABLED=true
ORBOT_LLM_PROVIDER=anthropic
ORBOT_LLM_API_KEY=sk-ant-your-key-here

# Webhooks
ORSCAN_WEBHOOK_SECRET=whsec_your_webhook_secret
```

---

## Output Formats

| Format | Free | Pro |
|--------|------|-----|
| JSON via API | ✓ | ✓ |
| HTML Report (interactive) | ✓ | ✓ |
| PDF Export | — | ✓ |
| CSV Export | — | ✓ |
| White-label PDF | — | ✓ |
| Webhooks | — | ✓ |

```bash
# Export as PDF
curl https://api.orscan.io/v1/scan/scan_k2m9x7dn4qfp/export \
  -H "Authorization: Bearer orsk_your_key" \
  -G -d "format=pdf" --output report.pdf

# Export as CSV
curl https://api.orscan.io/v1/scan/scan_k2m9x7dn4qfp/export \
  -H "Authorization: Bearer orsk_your_key" \
  -G -d "format=csv" --output issues.csv
```

---

## Pricing

| Feature | Free | Pro — $19/mo | Enterprise |
|---------|------|-------------|------------|
| Scans per day | 3 | Unlimited | Unlimited |
| Scan modules | 5 | All 12 | All 12 + custom |
| API access | — | ✓ | ✓ |
| ORBOT AI Agent | Demo only | Full access | Custom model |
| PDF export | — | ✓ | White-label |
| Webhooks | — | ✓ | ✓ |
| Competitor analysis | — | Top 3 | Unlimited |
| Rate limit | 3/day | 500/day | Custom |
| Support | Community | Email priority | Dedicated SLA |
| Uptime SLA | — | 99.5% | 99.9% |

> No credit card required for the free tier. Pro plan billed monthly, cancel anytime.  
> For team and agency pricing: [hello@orscan.io](mailto:hello@orscan.io)

---

## Self-Hosting

ORSCAN can be self-hosted on your own infrastructure. The Docker image is available via GitHub Container Registry.

> **Note:** Self-hosted instances require a valid license key. The free community license allows up to 100 scans/month.

### Docker

```bash
# Pull latest image
docker pull ghcr.io/orscan/orscan:latest

# Run
docker run -d \
  --name orscan \
  -p 3000:3000 \
  -e ORSCAN_API_KEY=orsk_your_key \
  -e ORBOT_ENABLED=true \
  -e ORBOT_LLM_API_KEY=sk-ant-xxx \
  ghcr.io/orscan/orscan:latest
```

### Docker Compose

```yaml
version: '3.9'
services:
  orscan:
    image: ghcr.io/orscan/orscan:latest
    ports: ["3000:3000"]
    environment:
      - ORSCAN_API_KEY=${ORSCAN_API_KEY}
      - SCAN_CRAWL_DEPTH=3
      - ORBOT_ENABLED=true
      - ORBOT_LLM_PROVIDER=anthropic
      - ORBOT_LLM_API_KEY=${ORBOT_LLM_API_KEY}
    volumes: [orscan_data:/data]
    restart: unless-stopped
  redis:
    image: redis:7-alpine
    restart: unless-stopped
volumes:
  orscan_data:
```

### System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| CPU | 1 vCPU | 2+ vCPU |
| RAM | 2GB | 4GB |
| Storage | 10GB | 20GB+ |
| Node.js | v20+ | v22 LTS |
| Redis | v6+ | v7+ |

---

## Contributing

Contributions are welcome. Please read these guidelines before opening a PR.

### Steps

1. **Fork & Clone**
   ```bash
   git clone https://github.com/orscan/orscan.git && cd orscan
   ```

2. **Install Dependencies**
   ```bash
   npm install
   cp .env.example .env  # add your API key
   ```

3. **Create a Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Run Tests**
   ```bash
   npm test  # all tests must pass (80%+ coverage required)
   ```

5. **Open a Pull Request** against the `main` branch with a clear description.

### Code Style

- ESLint + Prettier enforced — run `npm run lint` before committing
- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org): `feat:` / `fix:` / `docs:` / `chore:`
- New scan modules must include unit tests with at least 80% coverage
- Document new environment variables in `README.md` and `.env.example`

### Reporting Bugs

Open an issue at [github.com/orscan/orscan/issues](https://github.com/orscan/orscan/issues) using the bug report template.  
Include your Node.js version, the URL scanned (if possible), and the full error output.

> ⭐ Found ORSCAN useful? **Star this repo** — it genuinely helps visibility.

---

## Changelog

### v2.4 — April 2025 *(Current)*
- **New:** ORBOT AI Agent v2 with multi-turn conversation context
- **New:** Competitor analysis module — top 3 rival comparison
- **New:** White-label PDF reports for agencies
- **New:** Custom LLM provider support (OpenAI, Anthropic, Gemini)
- Webhook HMAC-SHA256 signature verification

### v2.3 — February 2025
- **New:** Full WCAG 2.2 accessibility audit module
- Core Web Vitals now uses live CrUX data from Google
- API rate limit headers added to all responses
- **Fix:** False positives in CSP header detection

### v2.2 — December 2024
- **New:** REST API v1 public release
- Webhook support with automatic retry logic (3 attempts)
- CSV and JSON export endpoints
- 40% faster average scan time

### v2.0 — October 2024
- **New:** ORBOT AI Agent v1 — initial release
- Dashboard redesign
- Pro plan launch at $19/month
- Mobile PWA

### v1.0 — June 2024
- **New:** Public launch — free tier with 5 scan modules
- 50,000 websites scanned in first 30 days

---

## Links

- **Website:** [orscan.io](https://orscan.io)
- **Documentation:** [docs.orscan.io](https://docs.orscan.io)
- **Status:** [status.orscan.io](https://status.orscan.io)
- **Contact:** [hello@orscan.io](mailto:hello@orscan.io)

---

*MIT License · © 2025 ORSCAN*
