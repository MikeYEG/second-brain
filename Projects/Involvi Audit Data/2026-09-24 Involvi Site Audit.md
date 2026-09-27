---
type: reference
client: Involvi HR
updated: 2026-09-24
tags: [involvi, site-audit, seo, performance, ux]
---

# Involvi site audit, 2026-09-24 (baseline)

Baseline for the monthly re-audit (1st Wednesday). Compare future runs against the tables below. Client page: [[Involvi HR]]. Project: [[Involvi Website Refresh]].

Method: PageSpeed Insights (Lighthouse lab, mobile + desktop) run in Chrome; full crawl of all 38 sitemap URLs (pages + posts) parsed for titles, meta, headings, alt text, schema; live DOM + screenshots at desktop and 390px mobile; Cloudways vulnerability scan (2026-09-23). Field data (CrUX): none, not enough Chrome traffic for Google to report.

## Scores

| Page | Mobile perf | Desktop perf | Accessibility | Best practices | SEO |
|---|---|---|---|---|---|
| Home | 56 | 85 | 88 | 100 | 92 |
| HR Health Check | 44 | 80 | 89 | 77 | 92 |
| Contact Us | 57 | 80 | 91 | 77 | 100 |

## Core metrics (lab)

| Page | Device | FCP | LCP | TBT | CLS | Speed Index | Page weight |
|---|---|---|---|---|---|---|---|
| Home | Mobile | 10.4 s | 17.1 s | 0 ms | 0 | 10.4 s | 3,121 KiB |
| Home | Desktop | 0.8 s | 2.2 s | 140 ms | 0.027 | 1.2 s | 3,405 KiB |
| HR Health Check | Mobile | 5.9 s | 6.8 s | 680 ms | 0 | 6.4 s | 2,752 KiB |
| HR Health Check | Desktop | 1.2 s | 1.4 s | 310 ms | 0 | 1.3 s | |
| Contact Us | Mobile | 4.8 s | 6.8 s | 250 ms | 0.001 | 6.2 s | |
| Contact Us | Desktop | 0.9 s | 1.0 s | 330 ms | 0 | 2.0 s | |

Targets (Google "good"): LCP 2.5 s or less, CLS 0.1 or less, INP 200 ms or less; mobile perf score 80+.

## Speed root causes
- Render-blocking CSS/JS: est. 5.1 s savings on mobile home, 4.8 s on HR Health Check. Home loads 38 stylesheets and 26 scripts.
- Unused JavaScript: 261 KiB (home, mobile) to 681 KiB (HR Health Check). Three Elementor add-on packs active (Elementor Pro, ElementsKit Lite, Essential Addons) plus Envato Elements.
- Google Fonts: Roboto Slab + Open Sans requested in every weight 100 to 900 incl. italics.
- Images: 98 KiB (mobile) / 470 KiB (desktop) savings; several JPGs not WebP, one "-scaled" 2560 px photo on home.
- LCP element is the home H1, which uses an Elementor fade-in entrance animation: 3,610 ms element render delay (mobile). Server response is fast (4 ms observed, Cloudflare), so the bottleneck is front end.
- Third-party embeds: Google Map on nearly every page, YouTube embeds on Resources/Compensation/HR Health Check (third-party cookies drop Best Practices to 77).
- Two captcha stacks: Cloudflare Turnstile loads on every page; Forminator form on Contact uses Google reCAPTCHA.

## SEO findings
- Placeholder pages indexed and in sitemap: /sample-page/ (WordPress default), /elementor-6/ ("Elementor #6").
- Lorem-ipsum post URLs: /pharetra-et-ultrices-neque/, /ac-orci-phasellus-egestas/, /nec-dui-nunc-mattis/.
- H1: only the homepage has one. 11 other pages use H2 for the page title; 24/24 posts have no H1.
- Meta descriptions: missing on all 24 posts. 25 of 38 titles over 60 characters.
- About Us duplicates the homepage title and meta description.
- Alt text: ~94% of images across the 38 URLs have none (235 of 251).
- Blog: 24 posts, all dated 2023-08-23 or 2023-12-14; nothing new since Dec 2023; author schema = "admin".
- /author/admin/ and /category/uncategorized/ indexable (thin; exposes the "admin" username).
- Schema: Organization only (name, url, logo). No LocalBusiness/ProfessionalService (address, phone, hours, sameAs), no FAQPage despite FAQ sections on 5 pages.
- Uncrawlable links: testimonial star icons are anchors with no href.
- No privacy policy (/privacy-policy/ 404).
- No Google Analytics 4, Tag Manager, ads pixels or Search Console verification tag found in page source (only Cloudflare Web Analytics beacon). Search Console may be DNS-verified; confirm.
- Services named on home with no page: Investigations, HR Metrics & Reporting. Recruitment Packages not in main nav.

## UX / conversion findings
- Hero headline starts invisible and fades in; on mobile the headline fills the first screen and the CTA sits below the fold.
- Copy is generic ("revolutionize your HR strategy", "Ignite Organizational Excellence"); does not name who it is for, what they get, cost or timeline.
- Free HR Health Check (main lead magnet) sends visitors to four Microsoft Forms by company size, off-site, untracked.
- Most sections end in the same "Contact Us" button; no booking link; phone not tap-to-call on home/header.
- Contact form (Forminator): 8 fields incl. file upload accepting almost any file type; message box capped at 180 characters; placeholder-only labels; a second hidden Elementor form on the same page.
- Social proof: 3 first-name-only testimonials; no logos, case studies, ratings, credential badges, or the 2025 Edmonton Chamber BIE feature.
- Content errors: Careers "please to submit your resume" (no link/email); About says Ashley "is a CPHR Candidate" while her title shows CPHR; Twitter icon links to the X login page; Resources repeats a video card; review links inconsistent; /blog/ meta typo "reltated".
- Accessibility: skip link not focusable, unnamed icon links (logo, social), low-contrast white-on-teal buttons, heading order skips, no main landmark. Body text #5F6EA5 on white = 4.93:1 (passes AA, light).

## Platform / security (40Two hosting)
- Cloudways 40Two-ClientSites-2 (app 6661478), live since 2026-09-09. WordPress 7.1.2, Elementor/Pro 4.3.0, Forminator 1.57.3. 0 known vulnerabilities (scan 2026-09-23). Let's Encrypt auto-renew.
- Housekeeping: inactive plugins (Hummingbird, WPForms Lite, Akismet, Object Cache Pro, 10Web Init, 0 Worker, Hello Dolly) and inactive themes (Twenty Twenty-Three/Four/Five, 10Web builder); overlapping tools (WPvivid + Cloudways backups; WP Remote + ManageWP Worker); Envato Elements active in production.

## Crawl data
Per-URL crawl: `Attachments/Involvi/crawl_2026-09-24.csv`. Client report PDF (with screenshots): `Attachments/Involvi/Involvi Website Review - September 2026.pdf`. Deck: "Involvi Website Review" Slides artifact.
