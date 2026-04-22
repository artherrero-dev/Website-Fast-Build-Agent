# Website Rebuild Agent — Instructions

Use this prompt template when you have an existing website and want a more elevated, production-ready version built from scratch.

---

## Prompt Template

> I want to rebuild **[business name]**'s website. Here's the existing site: **[URL]**
>
> GitHub: **[your GitHub username]** — create the repo if it doesn't exist.
>
> Use Claude in Chrome to browse the existing site and pull any content, copy, and structure worth keeping. Also look up the business on Google Maps and grab 3–6 five-star reviews from real people (first and last name only — no business names, no weird formatting).
>
> Build a more elevated version using a lightweight frontend framework (no build step, easy to host anywhere). Sync to GitHub when done.

---

## What I'll Do

### 1. Audit the existing site
- Open the URL in Chrome and read all visible content — headline, services, about copy, contact info, CTAs
- Note what's working and what's holding it back (weak hierarchy, dated design, no social proof, etc.)
- Extract any reusable copy worth keeping

### 2. Pull Google reviews
- Search Google Maps for the business
- Grab 3–6 five-star reviews with proper first and last names
- Skip business names, single names, usernames, or anything with unusual characters

### 3. Set up the repo
- Initialize a local git repo in the workspace folder
- Create a new GitHub repo under your account (public by default) via VS Code's Publish Branch
- Push the initial commit once the site is ready

### 4. Build the site
**Stack:** Single `index.html` — Tailwind CDN + vanilla JS. No build step, no dependencies, deploys anywhere (Netlify, Vercel, GitHub Pages, Cloudflare Pages).

**Sections built by default:**
- `Nav` — logo, anchor links, phone CTA
- `Hero` — strong headline, subheadline, trust badge (star rating + review count), dual CTAs
- `Stats strip` — 3–4 proof points (rating, years, jobs done, availability)
- `Services` — card grid with icons, descriptions, and starting prices
- `Reviews` — cards with reviewer name, initials avatar, star rating, quote, time ago
- `Booking/Contact form` — name, phone, email, service selector, date, address, notes field; success state on submit
- `Footer` — contact details, service list, hours, copyright

**Design principles applied:**
- Dark premium base (`#080B12`) or light neutral — chosen based on the industry and existing brand
- One accent color pulled from the existing brand (or chosen to elevate it)
- Subtle gradients, card hover states, and a shimmer accent line for depth
- Mobile-first, fully responsive
- Google Fonts loaded via CDN (Inter or similar)
- Smooth scroll, sticky nav with backdrop blur

### 5. Elevation checklist
Things I'll improve over a typical existing small-business site:

| Common issue on old site | What I'll do instead |
|---|---|
| Generic stock headline | Specific, benefit-led headline tied to the business |
| No social proof above the fold | Star rating + review count in the hero badge |
| Wall-of-text service descriptions | Scannable cards with icon, 2-line description, price anchor |
| Contact page buried in nav | Booking form on the same page, anchored from every CTA |
| No visual hierarchy | Clear type scale: 7xl hero → 5xl section → lg card |
| Slow load from heavy framework | Tailwind CDN only — sub-second load, no JS framework |

### 6. Push to GitHub
- Commit everything to `main`
- Use VS Code Source Control → Publish Branch to create and push the repo
- Repo name defaults to the folder name; adjust if needed

---

## Options You Can Add to the Prompt

| Option | What to say |
|---|---|
| Keep existing color palette | "Match the brand colors from the existing site" |
| Light theme | "Use a light/white background" |
| Specific services to feature | "Focus on [service A] and [service B]" |
| Pricing visible | "Show pricing" or "Hide pricing, use 'Get a Quote'" |
| No booking form | "Just a contact section with phone and email" |
| Add a gallery section | "Add a before/after or portfolio section" |
| Custom domain note | "It'll be hosted on [domain]" |

---

## Hosting (after the push)

The output is a single `index.html`. To go live:

- **Netlify** — drag the folder into netlify.com/drop. Done in 30 seconds.
- **Vercel** — connect the GitHub repo, auto-deploys on every push.
- **GitHub Pages** — enable in repo Settings → Pages → deploy from `main`.
- **Cloudflare Pages** — connect GitHub repo, build command: none, output: `/`.
