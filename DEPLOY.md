# Deploying to GitHub Pages with your own domain

## 0. What's in this folder
- `index.html` — the whole site in one self-contained file (fonts, logos, scripts inlined)
- `CNAME` — your custom domain. **Edit this first**: replace `www.yourdomain.com` with your real domain, exactly one line, no `https://`, no trailing slash.

## 1. Create the repo
1. On GitHub: **New repository** → name it e.g. `razk-games-site` → Public → Create.
2. Upload both files from this folder into the repo root (drag-and-drop works: repo page → **Add file → Upload files**).

## 2. Turn on Pages
Repo → **Settings → Pages**:
- Source: **Deploy from a branch**
- Branch: `main`, folder: `/ (root)` → **Save**

Wait ~1 minute. It goes live at `https://<user>.github.io/razk-games-site/`.

## 3. Point your domain at GitHub
In your domain registrar's DNS panel:

**If you use a `www` subdomain (recommended — `www.yourdomain.com`):**

| Type  | Name | Value                |
|-------|------|----------------------|
| CNAME | www  | `<user>.github.io.`  |

Then set the registrar's root-domain forwarding (or an ALIAS/ANAME record) to send `yourdomain.com` → `www.yourdomain.com`.

**If you want the bare root domain (`yourdomain.com`):** four A records on `@`:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

and, optionally, also the `www` CNAME above so both work.

## 4. Finish in GitHub
Settings → Pages → **Custom domain**: type your domain → Save. GitHub re-checks DNS (can take 10 min to a few hours), then tick **Enforce HTTPS** once the certificate is issued.

## 5. Updating the site later
Ask me for a fresh standalone export, then re-upload `index.html` over the old one. Nothing else changes — the `CNAME` file stays put.

## Notes
- The hero art placeholder is empty in this export. Drop the LoopKO render into the design first, then re-export, or the live site shows the empty slot.
- Keep `CNAME` in the repo. If it disappears, GitHub drops the custom domain.
