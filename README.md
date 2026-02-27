# Trackaroo marketing site (static)

This repository contains a **static** marketing site for Trackaroo with the same key URL slugs as the current WordPress site:

- `/`
- `/school-bus-tracking/`
- `/school-bus-ticketing/`
- `/bods-compliance/`
- `/for-operators/`
- `/faqs/`

## Local preview
Open `index.html` in a browser (or use any simple static server).

If you have Python installed:

```bash
python3 -m http.server 5173
```

Then visit `http://localhost:5173/`.

## Deploy to a Plesk subdomain via Git (typical)
Plesk setups vary, but the common flow is:

1. Create a subdomain in Plesk (e.g. `staging.trackaroo.co.uk`).
2. Ensure its document root points to the folder where Plesk deploys the repo (commonly `httpdocs/`).
3. In Plesk, open **Git** (for that subdomain) and click **Add Repository**.
4. Choose a deployment path that is the document root (or a subfolder you point the document root at).
5. Add your SSH key (or use HTTPS credentials) so Plesk can pull.
6. Click **Deploy** after each push (or enable auto-deploy if your Plesk supports it).

### Pushing this repo to GitHub (example)
If you don’t already have a remote repo, create one on GitHub (e.g. `trackaroo-marketing`). Then:

```bash
git remote add origin git@github.com:<your-org-or-user>/trackaroo-marketing.git
git push -u origin main
```

In Plesk Git, point the repository to that GitHub URL and deploy.

This repo is pure static HTML/CSS/JS, so there’s no Node build step required.

## SEO / staging note
This repo is set up to be safe on a subdomain:

- Each page includes `meta name="robots" content="noindex,nofollow"`.
- `robots.txt` blocks crawling with `Disallow: /`.

When you’re ready to go live on the main domain:

1. Remove the `noindex,nofollow` meta tag from pages (search for `noindex,nofollow`).
2. Update `robots.txt` to allow crawling by changing `Disallow: /` to `Disallow:`.
