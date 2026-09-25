# NutriTwirl — Storefront

A single self-contained `index.html` (no build step, no dependencies) for the NutriTwirl millet noodles & pasta storefront. Cart, checkout, and the "Book an Order" form all run client-side with `localStorage` — there is no backend, so no real payments are processed (see "Payments" below).

## Deploy on GitHub Pages

1. Create a new GitHub repository and push this folder's contents to it (root of the repo, or a `docs/` folder — either works).
2. In the repo: **Settings → Pages → Source**, choose the branch and folder containing `index.html`, then save.
3. GitHub will publish the site at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

```bash
git init
git add .
git commit -m "NutriTwirl storefront"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```
Then enable Pages in the repo settings as above.

## Deploy on Vercel

**Option A — Vercel dashboard (no CLI):**
1. Push this folder to a GitHub repo (steps above).
2. Go to vercel.com → **Add New → Project** → import that repo.
3. Framework preset: choose **Other** (it's a static site — no build command, no output directory needed). Deploy.

**Option B — Vercel CLI:**
```bash
npm i -g vercel
cd nutritwirl-site
vercel        # first deploy, follow the prompts
vercel --prod # promote to production
```
The included `vercel.json` just enables clean URLs; it's optional and safe to delete if you don't need it.

## Files
- `index.html` — the entire site (HTML/CSS/JS in one file, product photos embedded as base64 so there are no separate image files to manage)
- `vercel.json` — optional Vercel config
- `README.md` — this file

## Payments — read before going live
This storefront's checkout and "Book an Order" form collect the order details and show a confirmation, but they do **not** charge any card, UPI ID, or account — a static HTML file has nowhere safe to hold payment API keys. Right now it works as an **order-intake form**: you'll want to follow up by phone/WhatsApp/email to confirm and collect payment (COD, a UPI payment link, etc.).

To accept real online payments, you'd need:
1. A small backend (Node.js, PHP, etc. — Vercel Functions work well alongside this static site) that talks to a gateway like **Razorpay** or **Cashfree** (the two most common in India, supporting UPI/cards/netbanking).
2. That backend creates an order server-side and verifies payment on success — the API keys never touch the browser.
3. Swap the "Place order" button in `index.html` to call your new backend endpoint instead of the local confirmation screen.

Happy to help write that backend when you're ready for it.
