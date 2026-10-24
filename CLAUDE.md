# CellHaus Accelerator site

Static marketing and application site for the CellHaus Accelerator (Kobe, Japan), Cohort 2, 2027.
Plain HTML, no build step. Hosted on Netlify. Netlify Forms handles the application form.

## Goal for this session

Deploy a new **draft** site on Netlify from this folder. Do not deploy to production unless Elliot asks.

1. Check the Netlify CLI: `npx netlify-cli --version`. Log in if needed: `npx netlify-cli login`.
2. Create a new site in the `er-creates` team:
   `npx netlify-cli sites:create --name cellhaus-draft --account-slug er-creates`
   If the name is taken, try `cellhaus-accelerator-draft`.
3. Link this folder to that site if the CLI did not: `npx netlify-cli link --name <site-name>`.
4. Draft deploy: `npm run deploy:draft` (this is `netlify deploy --dir=site`, no `--prod`).
5. Report the draft URL back to Elliot.
6. In the Netlify UI (or tell Elliot to do it): Site configuration › Forms › enable form detection, then redeploy.
   Add an email notification for the `apply` form to elliot@haus.fund.

## Layout

```
site/            Published folder (Netlify publish dir)
  index.html     Home: pitch, how it fits, program, process, fit table, safeguards, CTA
  pathway.html   The seven steps, review classes, worked example, checklist (#bring), family track
  apply.html     Application form (Netlify Forms, name="apply", posts to /thanks)
  thanks.html    Confirmation page after submit
  privacy.html   Privacy policy (draft, under legal review). Linked from every footer and the apply consent line
  images/        Optimized JPEGs (Meiji-style CellHaus prints, max 1800px wide)
  brand.css      Brand layer: logo mark, hanko seal, seigaiha wave bands, watermarks, eyebrow dots
  favicon.svg    The CellHaus mark (vermilion ring, rose nucleus)
design/          The original Claude Design canvas sources (.dc.html). Reference only, not deployed.
netlify.toml     Publish dir, pretty URLs, headers, noindex for the draft
```

## Design rules

- Palette: dark #16140F, cream #F3ECDD, card #2A2620, rose #E8B4A6, vermilion #C9452E (bright #FF6A4D on dark, deep #A8361F on cream), indigo #1B2440, muted #3A4160 / #6B6458 / #B8AE9C.
- Fonts (Google Fonts): EB Garamond for display, IBM Plex Sans for body, Shippori Mincho for kanji.
- Styles are inline on purpose (they came from the design canvas). If you refactor to a stylesheet, keep the look identical.
- Brand elements live in `site/brand.css` and are reused as small HTML snippets: `.ch-mark` (inline SVG logo), `.ch-seal` (細胞館 stamp), `.ch-wave` (wave band, with `on-cream`/`on-sand` and `bg-*` modifiers), `.ch-watermark` inside a `.ch-host` section, `.ch-orn` divider, `.ch-eyebrow` labels.
- Every page must work at phone width (no horizontal scroll). Buttons and inputs at least 44px tall.
- Copy style: short plain sentences. **Never use em dashes.** Use commas, colons or separate sentences.
- Brand: CellHaus is "a Haus program". Do not use the Biopunk brand here.
- Partner hospitals, cell facilities and regulators stay generic ("a partner academic hospital in Kobe"). Mirai Tech City and Unchain Bio are named because they run the program.
- Do not add patient names, doctor names, fund size or investment claims.

## Facts on the site (keep consistent)

- Cohort 2: Kobe 1 September to 1 November 2027, then San Francisco 1 November to 15 December 2027, showcase in December.
- Applications close 31 May 2027. Offers go out by 30 June 2027.
- Program fee: $3,000 per month per founder. Sponsors may cover part or all of it.
- Contact: elliot@haus.fund
- All times and risk classes are planning estimates.

## Open items (ask Elliot before changing)

- Custom domain (none set yet). Remove `noindex` in `netlify.toml` and the pages' `<meta name="robots">` only at launch.
- Privacy policy: drafted at site/privacy.html. Needs legal review before launch, then remove the "Draft policy" note. Assumed commitments to confirm: 24 month deletion for non-admitted applicants, 30 day reply to data requests, separate consent before registry entries, US storage via Netlify, under-18s applied for by a parent or guardian. Section 11 (APPI) also needs: the business operator's legal name, address and representative (placeholder on the page), confirmation of Netlify's DPA, and the security measures it lists (personal accounts, reviewer confidentiality).
- Legal review of the consent lines on apply.html: `consent` (program terms) and `data_consent` (health data use, sharing, transfer outside Japan incl. the US, applying for someone else). Both required.
- Analytics (none added).
