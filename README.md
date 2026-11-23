# ReUnion 31 website

Multi-page wholesale site with an admin panel at `/admin` for uploading photos and videos and editing every page, with no code.

**Pages:** Home · Catalogue (12 categories, 69 brand listings, with search and filters) · About · How to order (steps + FAQ) · Contact (quote form)

## How it works

```
You edit in /admin  →  saved to this GitHub repo  →  Cloudflare rebuilds the site (about 1 minute)
```

- `content/`: all text, listings and posts as JSON files (the admin panel edits these)
- `public/images/uploads/`: your uploaded photos and videos
- `public/admin/config.yml`: what the admin panel shows
- `build.mjs`: turns `content/` into the HTML pages in `dist/`. No dependencies needed.

## One-time setup

### 1. Host it on Cloudflare Pages (free)
1. Create a free account at **dash.cloudflare.com**.
2. Go to **Workers & Pages → Create → Pages → Connect to Git**. Choose *Pages*, not *Workers*.
3. Connect GitHub and pick **reunion31**.
4. Build settings:
   - Framework preset: **None**
   - Build command: **`node build.mjs`**
   - Build output directory: **`dist`**
5. Click **Save and Deploy**. Your site goes live at `https://reunion31.pages.dev` or similar.

### 2. Log in to the admin panel
1. Open `https://YOUR-SITE.pages.dev/admin`.
2. Click **Sign In with Token**. The link opens GitHub's token page with the right permissions pre-selected.
3. Under *Repository access*, choose **Only select repositories → reunion31**. Set the expiry to the longest allowed and click **Generate token**.
4. Paste the token into the admin panel. Save it in your password manager, because GitHub only shows it once.

### 3. First things to fill in (admin → Pages & settings → Business details)
- **Website address**: your pages.dev URL, or your own domain later
- **WhatsApp number**: adds WhatsApp buttons across the site
- **Fleek store link**

### 4. Switch on the quote form
The contact form emails enquiries to the address in *Business details* through FormSubmit, which is free and needs no signup.
Send one test enquiry yourself. FormSubmit then emails **reunion31thrift@gmail.com** an activation link. Click it once, and every enquiry after that arrives in your inbox.

### 5. Your own domain (optional)
Buy `reunion31.com` or similar, then go to **Cloudflare → your Pages project → Custom domains → Set up a domain**.

## Day-to-day: adding photos and videos
- **New stock photos:** Admin → *Catalogue listings* → open a listing → *Photos* → add. The first photo is the cover.
- **Video:** clips under 25 MB (about 30 seconds) upload directly. For longer ones, post to YouTube or Instagram and paste the link in *Video link*.
- **Out of stock:** untick *In stock* to hide a listing without deleting it.
- **Home page picks:** tick *Feature on home page* on a listing that has a photo.

Photos are automatically resized and converted to WebP when you upload them, so phone photos are fine.

## Limits to know
- Cloudflare's free plan allows 500 builds a month, and each *Save* is one build, so it's best to finish editing a listing before saving. Bandwidth is unlimited.
- Keep video files small. Big files slow down the repo; links to YouTube or Instagram have no size limit.
