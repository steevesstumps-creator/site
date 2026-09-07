# Steeves Stump Services — steevesstumpservices.ca

Static one-page local-SEO landing site. **No build step, no framework, no JavaScript.**
Every heading, paragraph, FAQ answer and JSON-LD block is in the raw HTML.

## Deploy
Vercel (or any static host). Root directory = repo root, no build command,
output = repo root. `vercel.json` sets caching + security headers.

## Files
```
index.html          the whole page
styles.css          tokens + classes (self-hosted @font-face at the top)
assets/             responsive WebP + JPEG at 1x/2x, pre-cropped to their display ratio
fonts/              Oswald 600/700, Open Sans 400/700 — latin subset only
robots.txt, sitemap.xml, site.webmanifest, favicon.ico, apple-touch-icon.png
vercel.json         headers: 1-year immutable cache on /assets + /fonts, HSTS, nosniff
```

## Rules that must not be broken

1. **No JavaScript.** The sticky mobile CTA bar is pure CSS: `#sticky-cta` is the
   last child of `#post-hero` with `position:sticky;bottom:0`. A JS scroll-listener
   version was tried before and failed. Do not reintroduce one.
2. **The FAQ must match the schema.** The eight `<details>` Q&As and the `FAQPage`
   JSON-LD in `<head>` are word-for-word identical. Edit both in the same commit.
3. **No `AggregateRating` / `Review` schema** until there are real Google reviews —
   self-reported review markup violates Google's structured-data policy.
4. **Header and footer are `#171717`, not `--black-900`.** That matches the baked-in
   background of the logo PNG so the logo's square edge disappears. If a genuinely
   transparent logo ever arrives, both can go back to `--black-900`.
5. **The work photos are three different properties, not a before/after pair.**
   Do not label them as one.
6. **Keep `min(100%, …)` in every `minmax()`.** It is what stops horizontal
   overflow at 320px.

## Before launch
- [ ] Confirm the `steevesstumpservices.ca` domain, then attach it in Vercel.
      If the domain changes, update the canonical + `og:url` in `index.html`,
      both JSON-LD blocks, `robots.txt` and `sitemap.xml`.
- [ ] Confirm the street address; NAP must match the Google Business Profile exactly.
- [ ] Verify in Google Search Console and submit `sitemap.xml`.
- [ ] Paste the Google reviews embed into `#google-reviews-widget`.
- [ ] Tap every call/text button on a real phone.

## Copy direction (applied)
- One CTA: **text a photo**. Text is the red primary button everywhere (hero, services,
  about, final CTA, sticky bar); Call is the secondary. Email appears once, in the footer.
- Offer framing: one photo -> same-day price -> free -> nobody comes to your house.
- No specs (no grind depth in inches). Outcome only: the stump is gone.
- "We are insured." stated plainly, once in the hero ticks, once in About, once in the FAQ.
- No prices, no review counts, no invented guarantees or certifications.
- French: `essouchage` / `broyage de souches` appear once so the page is findable on those
  terms. No French-language service is promised, because nobody at the company speaks French.

## SEO changes in this pass
- All 8 H2s now carry "Moncton" or "Greater Moncton" (4 previously did not).
- H1 picks up the offer and keeps the primary keyword.
- Service-area cards expanded 6 -> 8 (added Hillsborough, Berry Mills).
- FAQ expanded 8 -> 10: added "Are you insured?" and "Do you take down trees too?"
  (the second one covers tree-removal search intent honestly and sets up referrals).
- FAQ answers and the FAQPage JSON-LD are generated from one source (`faq.json`) so they
  cannot drift apart. If you edit an answer, regenerate both.
- Fixed a congruence bug: the reviews section previously said "Have a read below and see
  for yourself" above a widget containing zero reviews.
