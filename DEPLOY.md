# Deploy Citeable landing

Target: **https://sites.tanishqnalloju.com**  
Worker name: `citeable-sites`  
Pattern: Cloudflare Workers Assets (same as ppp-calculator / kingindex-v2 desks)

## Prerequisites

- Node.js 18+
- `CLOUDFLARE_API_TOKEN` with Workers deploy + custom domain permissions, **or** `npx wrangler login`
- Zone `tanishqnalloju.com` on the same Cloudflare account

## Install & deploy

```bash
cd /workspace/citeable-landing   # or your clone
npm install
npx wrangler deploy
```

`wrangler.jsonc` already sets:

- `name`: `citeable-sites`
- `routes`: `sites.tanishqnalloju.com` with `custom_domain: true`
- `assets.directory`: `./public`

Custom domain attachment is handled by Wrangler when the zone is on this account. If the route fails, attach in the dashboard:

1. Workers → `citeable-sites` → Settings → Domains & Routes  
2. Add custom domain `sites.tanishqnalloju.com`

## Local preview

```bash
npx wrangler dev
```

## DNS (only if custom_domain does not auto-attach)

If the hostname is not proxied automatically:

| Type | Name | Target |
|---|---|---|
| CNAME | `sites` | `citeable-sites.<your-subdomain>.workers.dev` |

Prefer the Workers **Custom domain** UI (proxied orange cloud) over a manual CNAME when possible.

## Verify after deploy

- https://sites.tanishqnalloju.com/
- https://sites.tanishqnalloju.com/robots.txt
- https://sites.tanishqnalloju.com/sitemap.xml
- View-source: title, canonical, JSON-LD blocks, ₹2,000 pricing

## Rollback

```bash
npx wrangler deployments list
npx wrangler rollback
```
