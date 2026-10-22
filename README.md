# Her Wellness Daily — GLP-1 Gut Support Comparison Funnel

Premium editorial comparison advertorial for **Her Wellness Daily**
(https://herwellness-daily.com), evaluating five gut-support options
relevant to women taking GLP-1 medications.

## Stack

Static semantic HTML + CSS. No framework, no build step, no dependencies —
chosen for fastest LCP on paid traffic and zero-friction hosting. Fonts are
the only external request (Google Fonts, `display=swap`, preconnected).

## Structure

```
index.html              Full page markup; sections are commented blocks
assets/css/base.css     Design tokens, reset, type scale, layout primitives
assets/css/sections.css Per-section styles — append new blocks as sections ship
assets/img/             Imagery (hero placeholders in place today)
```

## Local preview

```sh
python3 -m http.server 4173
# → http://localhost:4173
```

## Design tokens

| Token | Value | Use |
|---|---|---|
| `--c-white` | `#FFFFFF` | page background |
| `--c-ink` | `#242424` | primary text |
| `--c-ink-soft` | `#4A4A4A` | secondary text |
| `--c-ink-muted` | `#767676` | metadata (AA 4.5:1 on white) |
| `--c-burgundy` | `#873D55` | accent |
| `--c-rose` | `#F3E6EA` | secondary accent |
| `--c-neutral` | `#F8F7F5` | light section fills |
| `--c-rule` | `#E7E7E7` | dividers |

Reading column `--measure: 660px`; wide blocks `--wide: 1040px`.
Breakpoint: `48em` (768px), mobile-first.

## Hero image — replacing the placeholder

`assets/img/hero-placeholder-*.svg` are clearly marked placeholders, not stock
photography. To ship the real asset:

1. Export two crops — desktop **16:9** (1600×900) and mobile **4:5**
   (1000×1250), cropped so the subject is not cut off.
2. Save as AVIF + WebP + JPG fallback in `assets/img/`.
3. In `index.html`, point the `<source>` / `<img>` at the real files and update
   `alt` to describe the photograph.
4. Delete the `.hero__note` `<figcaption>`.

Aspect ratios are pinned in CSS, so swapping assets causes no layout shift.

Image brief: natural woman aged 45–60, realistic American home, casual
authentic lifestyle photography, soft daylight, natural skin texture, no
retouching, no medical imagery, no packaging or logos, no text overlays.

## Section roadmap

- [x] **Section 1** — header, metadata, headline, subheadline, hero, intro, disclosure
- [x] **Section 2** — ranking methodology: 5 evaluation criteria, evaluation note, transition
- [x] **Section 3** — Top 5 comparison overview (all five entries, Veylen featured)
- [x] **Section 4** — detailed #1 review: Veylen Labs GLP-1 Comfort+, guarantee, first CTA
- [x] **Section 5** — detailed #2 review: Metamucil Psyllium Fiber
- [x] **Section 6** — detailed #3 review: Benefiber Prebiotic Fiber
- [x] **Section 7** — detailed #4 review: Align 24/7 Digestive Support
- [x] **Section 8** — detailed #5 review: GLP-1 SOS + head-to-head table
- [x] **Section 9** — final comparison verdict, product reminder, CTA
- [x] **Section 10** — Buy 2 Get 1 Free offer (**pricing + buy CTAs gated**)
- [x] **Section 11** — FAQ, disclaimers, footer

Each mounts at the marked insertion point near the bottom of `index.html`.

Criteria rows (`.criterion`) are one repeated markup pattern; the 01–05 markers
come from a CSS counter (`decimal-leading-zero`), so rows can be added or
reordered without renumbering anything by hand.

## LAUNCH STATUS: NOT READY

Three blockers, all requiring a human. Details below.

1. **Veylen product identity unresolved** — see `content/offer.json`.
2. **All product imagery is placeholder.**
3. **Legal operator of the publication unconfirmed** — see `content/routes.json`.

## Two things blocking publication

**1. Product imagery.** All six images are labeled placeholders. Official
photography is required for: Veylen Comfort+, Metamucil (psyllium *powder*
variant), Benefiber (original *wheat dextrin powder* — not gummies or
chewables), Align 24/7, GLP-1 SOS, plus the editorial hero. Unaltered
packaging, true proportions, no variant substitution, no AI recreation.

**2. Scores are withheld by design.** The briefs gate every grade and rating
on a documented scoring rubric applied identically to all five products. No
rubric exists yet, so no number is rendered anywhere — the proposed values
live in `content/rankings.json` with `published: false`. Section 4's scorecard
uses the briefs' qualitative fallback instead of numeric bars. To publish
scores: define each category, recompute from evidence for all five products,
then surface them. The 1–5 order is article presentation order, not a score
sort (entry 5 scores above entries 2–4).

Also omitted: the 89% / 92% / 89% / 98% customer-survey figures, which have no
underlying verified records.

## Verified against the live Veylen label (2026-10-22)

Checked at veylenlabs.com; the brief's specs matched exactly — magnesium
300 mg elemental, ginger 500 mg standardized to min. 5% gingerols,
*Weizmannia coagulans* BC99 2 billion CFU, B1 5 mg / B6 5 mg / B12 50 mcg,
60 capsules = 30 servings (two daily). Re-verify before launch.

Outbound links in use (both confirmed live):

- Product / CTA — `https://veylenlabs.com/products/veylen-labs-support-complex`
- Guarantee — `https://veylenlabs.com/policies/refund-policy`

Both carry `rel="noopener sponsored"` and sit next to the promotional-link
disclosure.

## Editorial standards

No invented author or medical-review credentials, no independent testing team,
no fabricated customer reviews or medical evidence. Product claims must trace
to verifiable source material. The commercial relationship with Veylen Labs is
disclosed in-article.
