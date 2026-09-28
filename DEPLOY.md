# Deploy Site Desk landing

Worker name: `site-desk-landing`  
Live now: **https://site-desk-landing.tanishq-nalloju.workers.dev**  
Custom domain: **not bound yet** — wait for Tanishq’s subdomain letter.

Pattern: Cloudflare Workers Assets (same as ppp-calculator / kingindex-v2 desks).

## Prerequisites

- Node.js 18+
- `CLOUDFLARE_API_TOKEN` with Workers deploy permissions, **or** `npx wrangler login`

## Install & deploy (workers.dev)

```bash
cd /workspace/site-desk-landing   # or your clone
npm install
npx wrangler deploy
```

`wrangler.jsonc` currently has **no** `routes` / custom domain — only `workers_dev: true`.

## Custom domain (placeholder — do this later)

When the subdomain letter is chosen (example only: `sites.tanishqnalloju.com` or another host), then:

1. Add a route to `wrangler.jsonc`:

```jsonc
"routes": [
  { "pattern": "<SUBDOMAIN>.tanishqnalloju.com", "custom_domain": true }
]
```

2. Update canonical / OG / JSON-LD / robots.txt / sitemap.xml to that HTTPS origin.
3. Redeploy: `npx wrangler deploy`
4. If auto-attach fails, in the dashboard: Workers → `site-desk-landing` → Domains & Routes → Add custom domain.

Optional DNS fallback (prefer Workers Custom Domain UI):

| Type | Name | Target |
|---|---|---|
| CNAME | `<SUBDOMAIN>` | `site-desk-landing.tanishq-nalloju.workers.dev` |

## Local preview

```bash
npx wrangler dev
```

## Verify (current)

- https://site-desk-landing.tanishq-nalloju.workers.dev/
- …/robots.txt
- …/sitemap.xml
- View-source: title, canonical, JSON-LD, ₹2,000 pricing, “Site Desk” branding

## Rollback

```bash
npx wrangler deployments list
npx wrangler rollback
```
