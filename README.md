# Northwest Wax — Static Website

A self-hosted static website for **Northwest Wax** in Beaverton, OR. No CMS, no build tools — just HTML, CSS, and JavaScript.

## What's included

| File | Purpose |
|------|---------|
| `index.html` | Homepage |
| `services.html` | Full services & pricing |
| `about.html` | About Tori |
| `contact.html` | Address, hours, map, contact |
| `style.css` | Design system & styles |
| `main.js` | Navigation, scroll animations |
| `assets/images/` | Logo, hero photo, social icons |

## Preview locally

Open `index.html` in your browser, or run a simple server:

```bash
cd northwest-wax
python3 -m http.server 8891
```

Then visit: http://127.0.0.1:8891

---

## Deploy free on Cloudflare Pages

Cloudflare Pages hosts static sites for free. No server to manage.

### Step 1 — Create a Cloudflare account

1. Go to [https://dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up)
2. Sign up (free plan is fine)

### Step 2 — Upload your site

**Option A — Drag & drop (easiest)**

1. Log in to Cloudflare → **Workers & Pages** in the left sidebar
2. Click **Create** → **Pages** → **Upload assets**
3. Name your project (e.g. `northwest-wax`)
4. Drag the entire `northwest-wax` folder contents into the upload area  
   (all HTML files, `style.css`, `main.js`, and the `assets` folder must be at the root)
5. Click **Deploy site**
6. Cloudflare gives you a URL like `https://northwest-wax.pages.dev`

**Option B — Connect GitHub (for future updates)**

1. Push this folder to a GitHub repository
2. In Cloudflare Pages → **Create** → **Connect to Git**
3. Select the repo, set **Build command** to none (leave empty), **Build output directory** to `/` or the folder root
4. Deploy

### Step 3 — Connect your custom domain

If you own `northwestwaxbeaverton.com` (or another domain):

1. In your Pages project → **Custom domains** → **Set up a custom domain**
2. Enter your domain (e.g. `www.northwestwaxbeaverton.com`)
3. Cloudflare shows DNS records to add. Typically:
   - **CNAME** `www` → `northwest-wax.pages.dev` (your project URL)
   - Or use Cloudflare as your nameserver and let it configure automatically
4. If your domain is registered elsewhere (GoDaddy, Google Domains, etc.), add the CNAME record in that provider's DNS panel
5. Wait a few minutes to 48 hours for DNS to propagate

**Root domain (`northwestwaxbeaverton.com` without www):**  
Cloudflare Pages supports apex domains via CNAME flattening when your domain uses Cloudflare DNS.

---

## Updating content

Edit files in any text editor (VS Code, Cursor, Notepad++, etc.) and redeploy.

### Change text or prices

- **Homepage sections:** `index.html`
- **Pricing:** `services.html` — find the `.price-row` entries
- **About bio:** `about.html` and `index.html` (about section)
- **Hours / address:** `contact.html`, footer on every page

### Change images

1. Replace files in `assets/images/` (keep the same filename), or
2. Add a new image and update the `src` path in the HTML

Recommended: compress photos before uploading (under 500 KB for hero images).

### Replace Tori's photo

1. Add photo as `assets/images/tori.jpg` (or `.png`)
2. In `index.html` and `about.html`, replace the `.about-photo` placeholder `<div>` with:

```html
<img src="assets/images/tori.jpg" alt="Tori Gledhill, esthetician at Northwest Wax" width="800" height="1000" loading="lazy" style="width:100%;height:100%;object-fit:cover;">
```

### Add client testimonials

In `index.html`, find the `.testimonial-card` blocks and replace the placeholder quote and author name.

### Update the Square booking link

All **Book Now** buttons use one URL. To change it:

1. Open `main.js` and update `BOOKING_URL` at the top
2. Also search all `.html` files for `my-site-103202-105206.square.site` in `href` attributes (header/footer fallbacks)

Current booking URL: `https://my-site-103202-105206.square.site/`

### Update social links

Search for `instagram.com/northwestwax` and `facebook.com/northwestwaxbeaverton` in the HTML files.

---

## After deploying

- [ ] Visit every page and click **Book Now** — should open Square booking
- [ ] Test on your phone (navigation, pricing readability)
- [ ] Point your domain DNS to Cloudflare Pages
- [ ] Cancel Wix subscription once the new site is live
- [ ] Add Tori's photo and real testimonials when ready

---

## Support

This site is plain HTML/CSS/JS. Any web developer can host or modify it. You own all the files forever.

© Northwest Wax · Beaverton, OR · Tori Gledhill
