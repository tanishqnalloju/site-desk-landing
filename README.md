# Site Desk landing

Marketing site for **Site Desk** — customized SEO + answer-engine (AO) websites for India SMBs and freelancers at **₹2,000 INR** flat per site.

- Live: https://site-desk-landing.tanishq-nalloju.workers.dev  
- Custom domain: pending subdomain letter (see [DEPLOY.md](./DEPLOY.md))  
- Contact: tanishqnrao@gmail.com  
- Operator: [Tanishq Nalloju](https://tanishqnalloju.com)

## Stack

Single Cloudflare Worker serving static assets from `public/` (HTML / CSS / SVG). Minimal deps — only `wrangler` for deploy.

## Docs

- [PRODUCT.md](./PRODUCT.md) — offer definition  
- [DEPLOY.md](./DEPLOY.md) — wrangler + future custom-domain steps  

## Develop

```bash
npm install
npm run dev
```

## Deploy

```bash
npm run deploy
```
