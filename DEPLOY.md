# Deploying the Singapore Mahjong Website

## Files to upload
```
website/
├── index.html        ← Coming-soon landing page
├── privacy.html      ← Privacy policy (MUST always be live)
├── CNAME             ← GitHub Pages custom domain (GitHub only)
├── css/
│   └── style.css
└── images/
    └── app-icon.png
```

---

## Option A — GoDaddy Web Hosting (if you have it)

GoDaddy often sells hosting separately from domain registration.
Log in at godaddy.com → My Products → check if you have "Web Hosting".

If yes:
1. Open **cPanel → File Manager**
2. Navigate to `public_html/`
3. Delete the default GoDaddy placeholder files (index.html etc.)
4. Upload ALL files above (keeping the folder structure: css/ and images/)
5. Your site is live immediately at gooseberrystudio.com

If you don't have hosting, use Option B (it's free and better).

---

## Option B — GitHub Pages (FREE, recommended)

### One-time setup

1. Go to github.com and create a free account
2. Log in as **straycatsgp**, then click **New repository**
   - Name it: `singapore-mahjong-website` (or any name you like)
   - Set to **Public**
   - Click Create repository
3. Upload files:
   - Click **Add file → Upload files**
   - Drag in ALL the files from the `website/` folder
     (maintain the folder structure: css/ and images/ as subfolders)
   - Click **Commit changes**
4. Enable GitHub Pages:
   - Go to repository **Settings → Pages**
   - Source: **Deploy from branch** → branch: `main` → folder: `/ (root)`
   - Click Save
   - Under "Custom domain" type: `gooseberrystudio.com` → Save

### Point GoDaddy DNS at GitHub

In GoDaddy → My Domains → gooseberrystudio.com → DNS:

Delete any existing A records, then add these four:

| Type | Name | Value              | TTL |
|------|------|--------------------|-----|
| A    | @    | 185.199.108.153    | 600 |
| A    | @    | 185.199.109.153    | 600 |
| A    | @    | 185.199.110.153    | 600 |
| A    | @    | 185.199.111.153    | 600 |

Also add (or update) a CNAME:

| Type  | Name | Value                        | TTL |
|-------|------|------------------------------|-----|
| CNAME | www  | straycatsgp.github.io        | 600 |

DNS changes take 10–30 minutes. GitHub then automatically issues a free
HTTPS certificate — tick "Enforce HTTPS" in Pages settings once it appears.

---

## Going live (when app is released)

To switch from "Coming Soon" to the full launch page:
1. Remove `<meta name="robots" content="noindex, nofollow" />` from index.html
2. Replace the coming-soon badge and placeholder button with
   the real App Store link badge
3. Add your screenshots to the images/ folder and a screenshots section

The privacy policy URL to enter in App Store Connect is:
  https://gooseberrystudio.com/privacy.html

---

## App icon note

The current icon (App Icon Template.png) appears to be a placeholder/template.
Confirm in Xcode that your final app icon artwork is assigned to the
AppIcon asset in Assets.xcassets before submitting to the App Store.
The dark and tinted variants in the asset catalogue have no image assigned yet.
