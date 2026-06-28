# Layers Psychotherapy — Complete Website Workflow

Everything from building the site to getting it live, and how to change it later.

---

## The Stack
- **Files:** Plain HTML + CSS, stored in `/Users/jack/Hambrick Psychotherapy LLC Website/`
- **Version control:** Git → GitHub (repo: brick-work/layers-psychotherapy)
- **Hosting:** GitHub Pages (free)
- **Domain registrar + DNS:** Cloudflare (account: jackhambrick.mft@gmail.com)
- **Live URL:** layerspsychotherapy.com

---

## Part 1 — Building the Site

The site is made up of these files in the website folder:
- `index.html` — home/landing page
- `about.html` — about the therapist
- `services.html` — what you offer
- `contact.html` — how to reach you
- `shared.css` — all the styles for every page (change once, updates everywhere)
- `CNAME` — tells GitHub Pages which domain to serve (contains just: `layerspsychotherapy.com`)

### Design system
All pages use the Layers design system. Reference file: `Layers Therapist Dashboard.html`

**Fonts** (loaded from Google Fonts):
- Display/headings: Cormorant Garamond
- Body: Hanken Grotesk
- Mono: IBM Plex Mono

**Colors:**
- `#2C4257` — Slate 700 (primary dark)
- `#5B7E9C` — Blue 500 (accent)
- `#8FA9A0` — Sage 500 (secondary)
- `#D7E3EC` — Mist 200 (subtle backgrounds)
- `#FBFDFE` — Cloud (raised surfaces)

---

## Part 2 — Pushing to GitHub

After making changes to any files, push them to GitHub so the live site updates.

Open Terminal and run:
```
cd "/Users/jack/Hambrick Psychotherapy LLC Website"
git add .
git commit -m "describe what you changed"
git push origin main
```

**Password:** Use your GitHub personal access token (not your GitHub password).

### How to generate a personal access token
1. Go to github.com → click your profile picture → Settings
2. Scroll to the bottom of the left sidebar → Developer settings
3. Personal access tokens → Tokens (classic)
4. Generate new token (classic)
5. Give it a name, set expiration, check the **repo** checkbox
6. Hit Generate — **copy it immediately**, GitHub only shows it once
7. Paste it as your password when Terminal asks

---

## Part 3 — GitHub Pages Setup

This is how the site gets hosted for free. Only needs to be done once.

1. Go to github.com/brick-work/layers-psychotherapy
2. Click **Settings** → **Pages**
3. Under Build and deployment, set Source to **Deploy from a branch**
4. Set Branch to **main**, folder to **/ (root)** → Save
5. In the Custom domain field, type `layerspsychotherapy.com` → Save

GitHub will automatically deploy every time you push to main.

---

## Part 4 — Cloudflare DNS Setup

This connects your domain to GitHub Pages. Only needs to be done once per domain.

1. Log into dash.cloudflare.com
2. Select the domain → DNS → Records
3. Add these 4 **A records**:
   - Type: A | Name: @ | IPv4: `185.199.108.153` | Proxy: DNS only
   - Type: A | Name: @ | IPv4: `185.199.109.153` | Proxy: DNS only
   - Type: A | Name: @ | IPv4: `185.199.110.153` | Proxy: DNS only
   - Type: A | Name: @ | IPv4: `185.199.111.153` | Proxy: DNS only
4. Add 1 **CNAME record**:
   - Type: CNAME | Name: www | Target: `brick-work.github.io` | Proxy: DNS only

DNS propagation takes 10–30 minutes. Once it resolves, go back to GitHub Pages settings and check **Enforce HTTPS** — GitHub will issue the SSL certificate automatically.

---

## Part 5 — Buying a Domain via Cloudflare

Cloudflare Registrar charges at-cost (no markup, ~$10/year for .com).

1. Go to dash.cloudflare.com → left sidebar → Domain Registration → Register Domains
2. Search for your domain name
3. If available, purchase it
4. Then follow Part 4 to set up DNS

---

## Part 6 — Renaming the Practice / Changing the Domain

If you change the practice name and need a new domain:

### Step 1 — Buy the new domain
Follow Part 5 with the new domain name.

### Step 2 — Update the site files
- Find and replace the old practice name across all HTML files
- Update the `CNAME` file to contain just the new domain (e.g. `newpracticename.com`)

### Step 3 — Push to GitHub
Follow Part 2.

### Step 4 — Update GitHub Pages custom domain
- github.com/brick-work/layers-psychotherapy → Settings → Pages
- Change the Custom Domain to the new domain → Save

### Step 5 — Set up Cloudflare DNS for the new domain
Follow Part 4 for the new domain.

### Step 6 — Wait
10–30 minutes for DNS. SSL certificate issues automatically after that.

### Step 7 — (Optional) Redirect the old domain
In Cloudflare on the old domain, set up a redirect rule pointing to the new domain so old links still work.

---

## Notes
- The GitHub repo name (layers-psychotherapy) does not need to change when the domain changes
- The legal entity (Hambrick Psychotherapy, LLC) never appears on the registrar or GitHub
- Proxy status in Cloudflare must be **DNS only** (grey cloud) for GitHub Pages to work — not the orange proxied cloud
