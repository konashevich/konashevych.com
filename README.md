# konashevych.com
Lightweight landing page that routes visitors to:

- `translator.konashevych.com` — Translator service
- `oleksii.konashevych.com` — Personal website

This repository is ready to be served via GitHub Pages from the repository root.

## What I added

- `index.html` — the landing page
- `CNAME` — tells GitHub Pages the custom domain (contains `konashevych.com`)
- `.nojekyll` — prevents GitHub Pages from ignoring files that start with an underscore

## How to publish (GitHub Pages)

1. Push the repo to GitHub (owner: `konashevich` / repo: `konashevych.com`).
	 - Recommended: publish from the `main` branch, root (not /docs). GitHub Pages will serve `index.html`.
2. In the repository on GitHub: Settings → Pages → Source → choose `main` branch and `/ (root)` → Save.
3. GitHub will provision a TLS certificate automatically for your custom domain `konashevych.com`. This can take a few minutes.

## Recommended Cloudflare DNS configuration for a GitHub Pages custom domain

If you want `konashevych.com` to serve the site directly at the apex (no `www`):

- Add these A records (type: A) in Cloudflare for `konashevych.com`:
	- 185.199.108.153
	- 185.199.109.153
	- 185.199.110.153
	- 185.199.111.153
- Add a CNAME for `www` pointing to `konashevich.github.io` (or `konashevych.com`'s repo page) if you want `www` to redirect or serve the same site.

Important notes for Cloudflare:

- If you use Cloudflare proxy (orange cloud), GitHub Pages' automatic TLS certificate will not be shown; instead Cloudflare serves its certificate. To avoid complications and ensure GitHub's certificate is used, set the A records to "DNS only" (grey cloud) while certificates are provisioned. After successful HTTPS via GitHub you may experiment with the proxy, but keep `SSL/TLS` mode on Cloudflare set to `Full (strict)`.
- Alternatively, you can leave CNAME flattening enabled and configure the apex to point to `konashevich.github.io` — Cloudflare supports that as well.

## Want me to update Cloudflare DNS for you?

I can change Cloudflare DNS programmatically if you provide a scoped Cloudflare API token with the DNS:Edit permission for the `konashevych.com` zone (or provide temporary UI access). If you'd like that, paste the API token and confirm and I will apply the recommended DNS edits for the apex and `www`.

## After publishing

- Validate that `https://konashevych.com` is serving the page and TLS is active.
- If you want `translator.konashevych.com` and `oleksii.konashevych.com` to be redirected from the apex or configured differently, tell me which behavior you prefer and I can either update DNS or provide further instructions.

--
If you'd like, I can push the changes for you (I need your GitHub credentials or a PAT with repo scope), or you can push locally — either works.
