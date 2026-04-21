# QA Report: Daniel Almendrades

**Date:** 2026-04-21
**URL:** https://daniel-almendrades.cofoundy.dev
**Tier:** Pro S/.120
**Template:** pro/pro-starter
**Status:** PASS (after fix)

## Technical Health
- [x] HTML 200
- [x] CSS 200 (/_astro/index.D0l4pzYI.css)
- [x] favicon.svg 200
- [x] guia.pdf 200
- [x] cv.pdf 200
- [ ] og.jpg 404 (WARNING — non-blocking, social previews won't show image)

## Visual — Desktop (1280px)
- [x] Styled correctly, no raw HTML
- [x] Name renders "Daniel Almendrades" (serif, Libre Baskerville)
- [x] Title "Executive Director | Logística Internacional" visible with beige underline
- [x] DA monogram — large, square, navy gradient background, beige DA letters, double-border frame — renders perfectly
- [x] Stats show: 30+ años | 4 países (Perú · Canadá · USA · México) | MBA
- [x] Colors match palette: navy #0F2A4A headers, beige #B8956A accents
- [x] Fonts loaded: Libre Baskerville (serif headers) + Source Sans 3 (body)
- [x] All 5 sections render (Hero, About, Experience, Education, Footer) — no Projects section as expected
- [x] No horizontal overflow
- [x] Experience timeline: 7 numbered nodes with beige dots + year + company labels
- [x] 7 experience cards in 2-column grid, balanced spacing
- [x] Education: 4 cards in 2-column grid, clean typography
- [x] Footer: Daniel Almendrades, title, social icons (email/whatsapp/linkedin), copyright 2026

## Visual — Mobile (375px)
- [x] Name fits, no horizontal overflow
- [x] DA monogram scales down properly, still centered and visible
- [x] Stats stack in single row with reduced type size — readable
- [x] Section headers (Sobre Mí, Experiencia, Educación) legible
- [x] Skills (14 chips) wrap naturally
- [x] Experience cards stack vertically, 1 column — dates + company clear
- [x] Education cards stack vertically, 1 column
- [x] Footer adapts cleanly
- [x] No horizontal scroll

## Client Preferences (form match)
- [x] Bicultural Peruvian-Canadian identity reflected (tagline: "No solo bilingüe — bicultural")
- [x] 4 countries called out in stats (Perú · Canadá · USA · México)
- [x] Professional/executive style matches 52yo logistics director profile
- [x] Conservative color palette (navy + warm beige) appropriate for B2B executive
- [x] No photo → DA initials monogram, looking sharp

## Data Validation
- [x] Name: Daniel Almendrades (matches research-notes)
- [x] Email: daniel.almendrades@seacargo.com
- [x] WhatsApp: +51 994 127 981
- [x] LinkedIn: daniel-almendrades-574a2830 (real profile)
- [x] Current role: Gerente Regional de Desarrollo @ SEA Cargo Logistics Perú (2024—Presente)
- [x] 7 experience positions: SEA Cargo (2x), EMO Trans Perú, EMO Trans Houston, Geodis México (2x), Inchcape Vancouver
- [x] 4 education entries: California Coast (MBA 2002), ITESM Guadalajara (1999), BCIT Vancouver (1994), Capilano College (1992)
- [x] Dates consistent with 30+ years experience since 1994
- [x] No hallucinated data

## Clean Deploy
- [x] No template artifacts ("Diego Quispe", etc.)
- [x] No Lorem ipsum or placeholder markers
- [x] No undefined/null in rendered output
- [x] Social links point to real profiles
- [x] Colors are custom (navy + beige), not defaults

## Issues Found

### CRITICAL (fixed)
1. **Education logo placeholders rendered as empty beige squares** — The Education.astro component had outer `<div>` with `background-color: highlightColor15` that showed even when BrandIcon rendered nothing (no icons available for California Coast, ITESM, BCIT, Capilano). Visual artifact — 4 empty boxes next to each education card.
   - **Fix:** Added `getIconInfo(edu.school).file !== null` check — placeholder div now only renders when an icon file exists. Result: clean cards with degree/school/date/achievements, no empty boxes.
   - **Redeployed:** 2026-04-21 after fix, screenshots retaken, issue resolved.

### WARNING (non-blocking)
1. **og.jpg returns 404** — Open Graph image not generated. Social media shares (LinkedIn, WhatsApp previews) will fall back to default. Not critical for direct URL access but worth generating for LinkedIn sharing given the executive audience.

## Evidence
- qa-screenshots/desktop-full.png (full page desktop)
- qa-screenshots/mobile-full.png (full page mobile)
- qa-screenshots/desktop-hero.png, mobile-hero.png (DA monogram)
- qa-screenshots/desktop-about.png, mobile-about.png (skills)
- qa-screenshots/desktop-experience.png, mobile-experience.png (7 positions)
- qa-screenshots/desktop-education.png, mobile-education.png (4 entries — post-fix, clean)
- qa-screenshots/desktop-footer-4.png, mobile-footer-4.png

## Final Verdict
**PASS** — All critical issues resolved. Site is production-ready and delivery-ready. One non-blocking warning (og.jpg 404) noted for future polish but does not block delivery.
