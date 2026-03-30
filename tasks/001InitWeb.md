# Implementation Plan — pavla-mudrochova.cz

## Overview

Static single-page website for a private psychotherapy practice in Olomouc.
Stack: plain HTML + CSS only. Hosted on GitHub Pages with custom domain.

---

## Steps

### 1. File Structure

```
index.html
style.css
CNAME
```

### 2. HTML Structure (`index.html`)

Single page with the following sections in order:

| Section     | Czech label | Content                      |
| ----------- | ----------- | ---------------------------- |
| Header/Hero | —           | Name, title, short tagline   |
| O mně       | "O mně"     | Bio, photo, approach         |
| Ceník       | "Ceník"     | Price list (table or cards)  |
| Kontakt     | "Kontakt"   | Contact form + address/phone |
| Footer      | —           | Copyright                    |

SEO essentials in `<head>`:

- `<title>` — e.g. "Terapie Olomouc | Pavla Mudrochovová"
- `<meta name="description">` — targeted at "psychoterapie olomouc" _(hidden SEO — "psychoterapie" is intentionally used here and in `<meta name="keywords">` but never in visible page content)_
- `<meta name="keywords">`
- Open Graph tags (`og:title`, `og:description`, `og:url`, `og:image`)
- `<link rel="canonical">`
- `lang="cs"` on `<html>`

### 3. Contact Form (`Web3Forms`)

Use the following form (access key already configured):

```html
<form action="https://api.web3forms.com/submit" method="POST">
  <input type="hidden" name="access_key" value="cbb1a3f6-2eb1-4c79-bfb4-72852ab9bf72" />
  <input type="text" name="name" required />
  <input type="email" name="email" required />
  <textarea name="message" required></textarea>
  <button type="submit">Submit</button>
</form>
```

- Add labels in Czech: `Jméno`, `Email`, `Zpráva`
- Show simple success/error message after submission (minimal inline JS)

### 4. CSS (`style.css`)

- Mobile-first responsive layout
- Single clean color palette (calm, professional — e.g. soft sage/warm white)
- Sections full-width, max-width container centered (~900px)
- Smooth scroll: `scroll-behavior: smooth` on `html`
- Sticky or simple top navigation with anchor links to each section
- Media queries for breakpoints (≥768px desktop)

### 5. SEO & Performance

- Semantic HTML5 elements (`<header>`, `<main>`, `<section>`, `<footer>`)
- `aria-label` on sections and form fields
- Descriptive `alt` attributes on images
- Minify CSS before final deploy (optional)
- Add `robots.txt` allowing all
- Add `sitemap.xml` with single URL entry

### 6. Testing & Deploy

- Test on mobile (Chrome DevTools) and desktop
- Validate HTML at [validator.w3.org](https://validator.w3.org)
- Check Lighthouse score (aim for 90+ Performance, 100 SEO, 100 Accessibility)
- Push to GitHub → GitHub Pages auto-deploys
- Verify custom domain resolves correctly (may take up to 24h for DNS)

---

## Deliverables

- `index.html`
- `style.css`
- `CNAME`
- `robots.txt`
- `sitemap.xml`
