# Layers Psychotherapy — Domain & Hosting Workflow

## Current setup
- Domain: layerspsychotherapy.com (registered via Cloudflare, account: jackhambrick.mft@gmail.com)
- Hosting: GitHub Pages (repo: brick-work/layers-psychotherapy)
- DNS: Cloudflare (DNS only, not proxied)
- Files live in: /Users/jack/Hambrick Psychotherapy LLC Website/

---

## How to rename the practice / change the domain

### 1. Buy the new domain
- Go to dash.cloudflare.com → Registrar → Register a domain
- Search for the new domain and purchase it

### 2. Update the site files
- Edit the practice name in index.html, about.html, services.html, contact.html
- Update the CNAME file to contain just the new domain (e.g. `newname.com`)

### 3. Push changes to GitHub
Open Terminal and run:
```
cd "/Users/jack/Hambrick Psychotherapy LLC Website"
git add .
git commit -m "Rename practice to [new name]"
git push origin main
```
When prompted for a password, use your GitHub personal access token (not your GitHub password).

To generate a token: github.com → profile → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token → check the "repo" box → copy it immediately.

### 4. Update GitHub Pages custom domain
- Go to github.com/brick-work/layers-psychotherapy → Settings → Pages
- Change the Custom Domain field to the new domain → Save

### 5. Set up Cloudflare DNS for the new domain
Add 4 A records (Type: A, Name: @, Proxy status: DNS only):
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
Add 1 CNAME record (Type: CNAME, Name: www, Target: brick-work.github.io, Proxy: DNS only)

### 6. Wait
DNS propagation takes 10–30 minutes. GitHub will reissue an SSL certificate automatically once DNS resolves.

### 7. (Optional) Redirect the old domain
In Cloudflare, set up a redirect rule on the old domain pointing to the new one so old links still work.

---

## Notes
- The legal entity (Hambrick Psychotherapy, LLC) never needs to change on the registrar
- The GitHub repo name (layers-psychotherapy) can stay the same even if the domain changes
- Always use `git push origin main` with a personal access token as the password
