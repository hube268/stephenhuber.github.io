# Stephen Huber — Personal Portfolio Website

Single-page portfolio and consulting site for **www.stephenhuber.com**, hosted on GitHub Pages.

---

## Deployment to GitHub Pages

### Step 1 — Create a GitHub repository

1. Log in to [github.com](https://github.com)
2. Click **New repository**
3. Name it exactly: `stephenhuber.github.io`
   *(replace `stephenhuber` with your actual GitHub username)*
4. Set it to **Public**
5. Do NOT initialize with a README (you already have one)
6. Click **Create repository**

> If you prefer a custom repo name (e.g. `portfolio`), that works too — see Step 4 for the settings difference.

---

### Step 2 — Push the site files

Open a terminal in this folder and run:

```bash
git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/hube268/stephenhuber.github.io.git
git push -u origin main
```

---

### Step 3 — Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under **Source**, select **Deploy from a branch**
4. Branch: `main` / folder: `/ (root)` → click **Save**
5. GitHub will build and publish the site (takes ~1–2 minutes)
6. A temporary URL like `https://hube268.github.io` will appear

---

### Step 4 — Connect your custom domain (www.stephenhuber.com)

#### A. Enter the domain in GitHub Pages settings

1. Still in **Settings → Pages**, find the **Custom domain** field
2. Enter: `www.stephenhuber.com`
3. Click **Save** — GitHub will verify DNS (may take a few minutes)
4. Check **Enforce HTTPS** once the certificate is issued (~10 minutes)

The `CNAME` file in this repo is already set to `www.stephenhuber.com` — GitHub Pages uses it automatically.

#### B. Configure your DNS provider

Log in to wherever you purchased `stephenhuber.com` (GoDaddy, Namecheap, Cloudflare, etc.) and add these DNS records:

| Type  | Host/Name | Value                      | TTL  |
|-------|-----------|----------------------------|------|
| CNAME | `www`     | `hube268.github.io.`       | 3600 |
| A     | `@`       | `185.199.108.153`          | 3600 |
| A     | `@`       | `185.199.109.153`          | 3600 |
| A     | `@`       | `185.199.110.153`          | 3600 |
| A     | `@`       | `185.199.111.153`          | 3600 |

> The `A` records point the apex domain (`stephenhuber.com`) to GitHub Pages so bare-domain visitors are redirected to `www`.

DNS propagation typically takes 15 minutes to a few hours.

---

### Step 5 — Add your resume PDF (optional but recommended)

The "Download Resume" button links to `Stephen_Huber_Resume.pdf`.
Copy your PDF into this folder with that exact filename before pushing:

```
stephenhuber-portfolio/
├── index.html
├── CNAME
├── README.md
└── Stephen_Huber_Resume.pdf   ← add this file
```

---

## Customization Tips

| What to change | Where in index.html |
|---|---|
| Profile photo | Replace the SVG placeholder in the `#about` section with an `<img>` tag |
| Contact form (production) | Replace the `handleSubmit` mailto function with [Formspree](https://formspree.io) or [Netlify Forms](https://docs.netlify.com/forms/setup/) |
| Portfolio project details | Edit the `.portfolio-card` blocks in the `#portfolio` section |
| Services & pricing | Edit the `.service-card` blocks in the `#services` section |
| Colors | Update the CSS variables at the top of the `<style>` block |

---

## Tech Stack

- **Pure HTML / CSS / Vanilla JS** — no build tools or frameworks required
- **Google Fonts** — Inter + Playfair Display
- **GitHub Pages** — free static hosting with HTTPS
- **Custom domain** — via DNS CNAME + GitHub Pages custom domain setting
