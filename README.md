# NutriTwirl storefront — deploy guide

One file, `index.html`. No build step, no dependencies, nothing else needed.

## GitHub Pages (exact steps)

1. Create a new repository on GitHub (any name).
2. Click **Add file → Upload files**, and upload `index.html` directly — do NOT upload a folder, and do NOT put it inside a subfolder. It must land at the repo's root, so the repo's main file list shows `index.html` right there.
3. Commit the upload.
4. Go to **Settings → Pages**.
5. Under **Build and deployment → Source**, choose **Deploy from a branch**.
6. Under **Branch**, choose `main` and folder `/ (root)`, then **Save**.
7. Wait ~1 minute. Refresh the Settings → Pages screen — it will show "Your site is live at https://<your-username>.github.io/<repo-name>/".
8. Open that exact URL (including the `/<repo-name>/` part).

## Vercel (exact steps — no GitHub needed)

1. Go to **vercel.com/new** and log in.
2. Put `index.html` alone in an empty folder on your computer.
3. Drag that folder onto the "Deploy" drop zone on that page (not the "Import Git Repository" box).
4. Vercel deploys instantly and gives you a live `.vercel.app` URL.

## If you still get a 404
It's almost always one of these:
- `index.html` isn't at the root of the branch/folder your host is actually serving from.
- You're visiting the wrong URL (missing the `/<repo-name>/` part for GitHub Pages).
- Not enough time has passed since your last change (GitHub Pages takes ~30–90 seconds to rebuild).

## Payments — read before taking real orders
This page's checkout and "Book an Order" form collect and confirm orders but do not charge any card or UPI ID — a static file can't hold payment API keys safely. Use it as an order-intake form (confirm and collect payment by phone/WhatsApp/UPI link) until a real backend with Razorpay or Cashfree is added.
