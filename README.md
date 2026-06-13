# Mott Design

Portfolio site for Mott Design LLC. Static site (HTML/CSS/JS, no build step), deployed on Vercel from GitHub.

## Stack
- Plain HTML/CSS/JS — no framework, no build, no CMS
- Hosted on Vercel
- Domain `mott.design` (currently registered via Bluehost)

## Run locally
Just open `index.html` in a browser, or serve it:
```
python3 -m http.server 8000
```
Then visit http://localhost:8000

## Before you launch — two edits
1. **Contact form:** create a free endpoint at [formspree.io](https://formspree.io) (or similar), then replace `YOUR_FORM_ID` in the `<form action>` in `index.html`.
2. **LinkedIn:** replace `YOUR_HANDLE` in the LinkedIn link with your profile URL.

(Email `mike@mott.design` is already wired — change it if that's not the address you want.)

## Deploy to Vercel via GitHub
1. Create a new repo on GitHub and push this folder:
   ```
   git init
   git add .
   git commit -m "Initial Mott Design site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/mott-design.git
   git push -u origin main
   ```
2. Go to [vercel.com](https://vercel.com), sign in with GitHub, and "Import Project" → pick this repo.
3. Framework preset: **Other**. No build command, no output dir needed — it's static. Deploy.
4. You'll get a `*.vercel.app` URL immediately to preview.

## Point mott.design (on Bluehost) at Vercel
You do NOT need to move the domain off Bluehost — just update DNS.

1. In Vercel: Project → Settings → Domains → add `mott.design` and `www.mott.design`.
2. Vercel will show you the exact records. Typically:
   - **A record** for `mott.design` (apex) → `76.76.21.21`
   - **CNAME** for `www` → `cname.vercel-dns.com`
   *(Use the exact values Vercel shows you — they can change.)*
3. In Bluehost: cPanel → Domains / Zone Editor → DNS for mott.design.
   - Edit the apex `A` record to the Vercel IP.
   - Add/point the `www` CNAME to the Vercel target.
4. Wait for propagation (minutes to a few hours). Vercel auto-issues the SSL cert once DNS resolves.

> Note: entering DNS records and confirming the domain in Bluehost/Vercel happens in your own dashboards while you're logged in — I can't do those account actions for you, but the values above are everything you need to type in.

## Editing later
Edit `index.html`, commit, and push — Vercel redeploys automatically on every push to `main`. That's the whole workflow.
