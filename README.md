# Aleman Family Care Center — Website

A 6-page, fully responsive marketing website for **Aleman Family Care Center**.

## File Structure

```
aleman-family-medical/
├── index.html         Home page (hero, services, philosophy, stats, testimonials)
├── about.html         Practice story, values, philosophy
├── services.html      Detailed service breakdown + FAQ
├── providers.html     Bios of Dr. Aleman + co-founder
├── patients.html      New patient info, forms, insurance, resources
├── contact.html       Address, hours, appointment request form, map
├── README.md          ← you are here
└── assets/
    ├── styles.css     All styling (single file)
    ├── script.js      Mobile nav, scroll reveals, form handler
    ├── images/        DROP PHOTOS HERE — see "Adding Photos" below
    └── forms/         DROP PDF FORMS HERE (intake, HIPAA, etc.)
```

## How to View

Open `index.html` in any browser. No build step, no dependencies. Fonts load from Google Fonts.

## Brand & Design

- **Primary:** Forest green (`#2d5a3d`), deep variant (`#1f3a2b`), mid (`#3d7a52`)
- **Secondary:** Warm greys + sage tints (`#e3ede5`, `#cfd4d1`, `#fbfaf6` cream background)
- **Accent:** Soft gold (`#c8a967`) for warmth in dark sections
- **Type:** Playfair Display (serif headings) + Inter (sans body)
- All colors live as CSS variables at the top of `assets/styles.css` — change `--forest-700` to recolor the whole site.

## ⚠️ Placeholders That MUST Be Replaced Before Going Live

Every spot below has a visible "Replace with…" note on the page so you can find it easily.

### 1. Contact details (every page)
Search for and replace across all HTML files:

- `(000) 000-0000` — main phone (appears in nav, footer, utility bar, contact page)
- `(000) 000-0001` — fax
- `hello@alemanfamilymed.com` — email
- `3529 W National Ave` — street
- `Milwaukee, WI 53215` — city/state/zip
- Office hours table on `contact.html` — adjust if different

### 2. Provider bios (`providers.html`)
- Replace `Dr. Daniela Aleman` with her real first name
- Replace `Alvaro Aleman` and `Alvaro` with real name
- Pick a real title for uncle (Practice Administrator / Operations Director / Co-Founder)
- Rewrite the bio paragraphs with actual medical school, residency, professional memberships, languages, hobbies, etc.
- Update credential pills (Board Certified, AAFP Member, etc.) to match her actual credentials

### 3. Stats section (home page)
- "3,000+ families served" and "98% patient satisfaction" are placeholders — replace with real numbers or remove the section entirely

### 4. Founding story (`about.html`)
The paragraphs under "Our Story" are placeholder copy. Rewrite with:
- Why your aunt and uncle started the practice
- Her training background
- What "family medicine" means to your family personally
- Local community connection

### 5. Testimonials (`index.html`)
Three placeholder testimonials exist. Replace with real patient quotes (with written permission) or remove the section entirely until you have them.

### 6. Insurance list (`index.html`, `patients.html`)
Replace the placeholder insurance chips with the plans your aunt actually contracts with. Common ones (Aetna, BCBS, Cigna, Humana, UHC, Medicare) are pre-filled as starting points.

### 7. Map (`contact.html`)
Replace the `.map-placeholder` div with a Google Maps embed iframe:

1. Go to [maps.google.com](https://maps.google.com), search your address
2. Click "Share" → "Embed a map" → Copy HTML
3. Paste it in place of the `.map-placeholder` div

## Adding Photos

Drop photos in `/assets/images/` with these names, then they'll automatically appear:

| File name | Where it appears | Suggested size |
|---|---|---|
| `hero.jpg` | Home page hero | 800 × 1000 px, vertical |
| `practice.jpg` | Home — Philosophy split | 800 × 1000 px, vertical |
| `about-1.jpg` | About — Our Story split | 800 × 1000 px, vertical |
| `about-2.jpg` | About — What sets us apart | 800 × 1000 px, vertical |
| `dr-aleman.jpg` | Providers — Dr. Aleman card | 480 × 600 px |
| `co-founder.jpg` | Providers — Co-founder card | 480 × 600 px |
| `forms.jpg` | Patient Resources — Forms section | 800 × 800 px |

**To wire each photo up**, replace this pattern in the HTML:

```html
<div class="hero-visual">
  <div class="placeholder-label">…</div>
</div>
```

with:

```html
<div class="hero-visual">
  <img src="assets/images/hero.jpg" alt="Dr. Aleman with a young patient" style="position:absolute; inset:0; width:100%; height:100%; object-fit:cover;" />
</div>
```

The placeholder gradient stays as a fallback if the image is missing.

**Photo tips:**
- Use natural, candid photos over stiff stock images — patients respond to faces
- Include the providers themselves — the more the practice feels human, the more it stands out from the reference sites
- Add a few of the office interior (reception, exam rooms) on the about page
- Compress images first ([squoosh.app](https://squoosh.app) is free) — keep each under 200 KB

## Wiring Up The Appointment Form

Currently `contact.html` has a working-looking form that shows a thank-you message but doesn't actually send anywhere. To make it live, pick one:

- **Easiest:** Use [Formspree](https://formspree.io/) — change `<form id="contact-form">` to `<form action="https://formspree.io/f/YOUR_ID" method="POST">` and remove the JS handler in `script.js`.
- **Best:** Connect to whatever EHR/scheduling system the practice uses (Athena, eClinicalWorks, Practice Fusion, Healow, Tebra, etc.) — most provide an embeddable "Request appointment" widget.
- **Email only:** Use [Tally](https://tally.so/) or [Google Forms](https://forms.google.com/) and link to it.

## Deploying

Any static host will work — no server needed:

- **Netlify Drop**: [app.netlify.com/drop](https://app.netlify.com/drop) — drag the folder, get a live URL in ~10 seconds
- **Vercel**: connect a Git repo, auto-deploys on every push
- **GitHub Pages**: push to a `gh-pages` branch
- Or upload to any web host (Bluehost, SiteGround, etc.) via FTP

## A Note on Healthcare Compliance

Before going live:
- Add a real **HIPAA Notice of Privacy Practices** (link in footer)
- Add a **Privacy Policy** and **Terms of Service**
- Make sure the contact form is HIPAA-compliant if it collects any health info — Formspree free tier is NOT. Use a HIPAA-eligible service or have patients call/use the patient portal for anything health-related.
- Add an ADA/accessibility statement
