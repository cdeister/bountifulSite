# Bountiful Mental Health — bountifulmentalhealth.com

Static website for Dr. Diana Deister's psychiatry practice. Plain HTML + CSS,
no build step, nothing to maintain or renew except the domain itself.

## Structure

- `index.html`, `about.html`, `services.html`, `fees.html`, `contact.html` — the site
- `css/style.css` — all styling
- `photos/web/` — web-optimized images (2400px and 1200px versions)
- `photos/designInspiration/` — original full-resolution photos
- `recovered/` — the old site's homepage recovered from the Wayback Machine (Aug 2024)
- `CNAME` — tells GitHub Pages the custom domain

## Preview locally

```bash
python3 -m http.server 8123
```

Then open http://localhost:8123

## Deploy: GitHub Pages (recommended — free forever, no card to expire)

1. Create a repo on GitHub (e.g. `bountifulSite`), then:

   ```bash
   git remote add origin git@github.com:YOUR_USERNAME/bountifulSite.git
   git push -u origin main
   ```

2. On GitHub: **Settings → Pages → Source: Deploy from a branch → main / (root)**.
3. Under **Custom domain**, enter `bountifulmentalhealth.com` (the CNAME file
   in this repo keeps that setting on every deploy). Check **Enforce HTTPS**
   once the certificate is issued (can take up to an hour after DNS is set).

Every future edit is just: commit, push — live in about a minute.

## DNS at Hover

In the Hover control panel for `bountifulmentalhealth.com`:

1. **First**: change nameservers from `ns1–ns5.linode.com` back to Hover's own
   (`ns1.hover.com` / `ns2.hover.com`). The Linode nameservers are dead — this
   alone is why the site vanished.
2. Then add these DNS records:

   | Type  | Hostname | Value                     |
   |-------|----------|---------------------------|
   | A     | @        | 185.199.108.153           |
   | A     | @        | 185.199.109.153           |
   | A     | @        | 185.199.110.153           |
   | A     | @        | 185.199.111.153           |
   | CNAME | www      | YOUR_USERNAME.github.io   |

   (Those four A records are GitHub Pages' anycast IPs.)

3. Delete any old A/AAAA records pointing at the former Linode server.

DNS changes take minutes to a few hours to propagate.

## Alternative hosts

Netlify or Cloudflare Pages work equally well for a static site (also free,
also git-driven). GitHub Pages was chosen because the repo already lives on
GitHub and there is no separate account or billing to lapse.
