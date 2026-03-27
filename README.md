# Agentic Programming for Beginners — Landing Page

Landing page for the DataTrav course "Agentic Programming for Beginners." Single-file static site deployed via Cloudflare Pages at [agentic-beginners.datatrav.com](https://agentic-beginners.datatrav.com).

---

## What's in this repo

```
/
  index.html   ← complete single-file site (all CSS and JS embedded)
  README.md
  .gitignore
```

No build step. No dependencies. Drop it on any static host and it works.

---

## Deploy to Cloudflare Pages

1. Push this repo to GitHub.
2. In the [Cloudflare Dashboard](https://dash.cloudflare.com), go to **Workers & Pages → Create → Pages → Connect to Git**.
3. Select this repo.
4. Set the following build settings:
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/` (root)
5. Click **Save and Deploy**.

Cloudflare will serve `index.html` automatically from the root.

---

## Set the custom domain

1. In the Cloudflare Pages project, go to **Custom Domains → Set up a custom domain**.
2. Enter: `agentic-beginners.datatrav.com`
3. Cloudflare will create a CNAME record on the `datatrav.com` zone automatically (since it's on the same account). If not, create it manually:
   - **Type:** CNAME
   - **Name:** `agentic-beginners`
   - **Target:** `<your-pages-project>.pages.dev`

---

## Activating Phase 2 at launch

When enrollment opens, flip the page from waitlist mode to live purchase mode in **one edit**:

Open `index.html`, find the opening `<body>` tag, and add the class `launched`:

```html
<!-- BEFORE (Phase 1 — waitlist) -->
<body>

<!-- AFTER (Phase 2 — enrollment live) -->
<body class="launched">
```

That single change:
- Hides the "Join the Early Access List" hero CTA
- Shows the "Enroll Now" and "Start Learning" hero CTAs
- Hides the `#waitlist` email capture section
- Shows the `#pricing` section with the three tier cards

---

## Update the Formspree endpoint

1. Go to [formspree.io](https://formspree.io), create a form, and copy the endpoint ID (looks like `xabc1234`).
2. In `index.html`, find:
   ```html
   action="https://formspree.io/f/REPLACE_WITH_YOUR_ID"
   ```
3. Replace `REPLACE_WITH_YOUR_ID` with your actual form ID.

---

## Update pricing in the Phase 2 section

Search `index.html` for `$XX` — there are three instances, one per pricing tier (Starter, Core, Pro). Replace each with the actual price.

The pricing section is inside `<section id="pricing">`. Each card follows this pattern:

```html
<div class="pricing-price">$XX</div>
<div class="pricing-period">one-time payment</div>
```

Update the `href="#"` on each **Enroll** button to point to your payment/enrollment platform when ready.

---

## Local development

No build tools needed. Open `index.html` directly in a browser, or run a simple local server:

```bash
npx serve .
# or
python3 -m http.server 8080
```
