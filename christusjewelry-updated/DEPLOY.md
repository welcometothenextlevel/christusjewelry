# Going live on christusjewelry.com (GoDaddy → GitHub Pages)

> ⚠️ **Order matters.** The `CNAME` file in this repo switches GitHub Pages over to
> the custom domain the moment it is pushed. Until the DNS records below exist,
> `welcometothenextlevel.github.io/christusjewelry/` will stop serving the site.
> Add the DNS records **first**, then push `CNAME`.

## 1. DNS records to add in GoDaddy

In GoDaddy → **My Products → christusjewelry.com → DNS → Manage Zones**:

| Type  | Name | Value                          | TTL      |
|-------|------|--------------------------------|----------|
| CNAME | www  | welcometothenextlevel.github.io | 1 hour   |
| A     | @    | 185.199.108.153                | 1 hour   |
| A     | @    | 185.199.109.153                | 1 hour   |
| A     | @    | 185.199.110.153                | 1 hour   |
| A     | @    | 185.199.111.153                | 1 hour   |

The `www` CNAME is the one that serves the site. The four `A` records make the bare
`christusjewelry.com` redirect to `www.christusjewelry.com` instead of erroring.

Delete any existing GoDaddy "parked" / forwarding record on `@` or `www` first —
they conflict with the records above.

## 2. GitHub Pages settings

Repo → **Settings → Pages**:

- Source: `Deploy from a branch` → `main` / `(root)`
- Custom domain: `www.christusjewelry.com` (pushing the `CNAME` file sets this)
- Tick **Enforce HTTPS** once the certificate is issued (can take up to an hour after DNS propagates)

## 3. After it resolves

- Verify `https://www.christusjewelry.com/` loads and `http://christusjewelry.com` redirects to it.
- Submit `https://www.christusjewelry.com/sitemap.xml` in Google Search Console.
