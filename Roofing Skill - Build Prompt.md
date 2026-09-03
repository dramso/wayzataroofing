# Prompt: build me a reusable "Roofing Website" Claude Skill

Copy everything below the line and give it to Claude. It is written as instructions *to* Claude.

---

## What I want you to build

Author a complete, reusable Claude Skill called **`roofing-website`**. It is a standalone skill — it must not depend on, defer to, or reference my existing `home-services-cro-website` or `coach-consultant-website` skills. Everything it needs lives inside it.

The skill's job: whenever I start a roofing website project, it runs a four-phase build (strategy brief → wireframe spec → copy → code) using a fixed structural and visual system that I have already proven on a live client site. The skill's value is that it removes all re-invention: the structure, the section order, the storytelling beats, the component mechanics, the CSS, and the copy laws are all decided in advance. Only the client's facts change.

### Trigger description (write the frontmatter description to fire on these)

Roofing companies, roofing contractors, exteriors companies (roofing + siding + windows + gutters), storm restoration companies. Fire on: "new roofing site", "build a site for [roofing company]", "wireframe this roofer", "write the strategy brief for [roofer]", pasted roofing-client intake forms or discovery-call transcripts, or any mention of a roofing/exteriors contractor needing a website. Do NOT fire for other trades — that is what the general home-services skill is for.

### Skill file structure

Split it so I can maintain it:

```
roofing-website/
  SKILL.md                  ← phases, triggers, decision rules, the four-phase runbook
  references/
    design-system.md        ← tokens, type scale, component CSS, effect grammar
    components.md           ← the 10 mandatory components with full markup mechanics
    page-recipes.md         ← section order for each of the 11 page types
    copy-system.md          ← storytelling method, copy laws, headline formulas, banned language
    city-pages.md           ← the local page playbook
    cro-rules.md            ← the conversion checklist enforced on every page
```

SKILL.md stays short enough to always load; the references get read on demand.

---

## Phase behaviour

**Run all four phases straight through in one response.** Do not stop for my approval between phases. Do not ask me questions mid-build — if a fact is missing, make the best inference, use it, and list it under a short "Assumptions to confirm" block at the very end.

**Phase 1 — Strategy Brief.** Client snapshot; service list; service area list; target homeowner profile; the client's positioning angle (see below); competitive read if I gave you competitor URLs; the sitemap; the primary and secondary conversion actions; the proof inventory (reviews, photos, credentials, warranty terms, financing) with gaps flagged.

**Phase 2 — Wireframe Spec.** Page by page, section by section, in order. Each section gets: section name, the component it uses (named from the component library), the copy direction (what this section must argue, not the final copy), the asset it needs, and the CTA if any.

**Phase 3 — Copy.** Final copy for every page, written to the copy laws below. Verbatim-ready. Never lorem.

**Phase 4 — Build.** Code the pages. Default output is Omelette Design Components (`.dc.html`, one file per page, plus shared `Site Nav` and `Site Footer` DCs imported via `dc-import`). If I say "plain HTML" or "for a developer", output standalone HTML files instead with the same structure and an extracted stylesheet. If I say "spec only", stop after Phase 3.

---

## Positioning: derive it, never assume it

Positioning comes entirely from client intake. The skill must not carry a default angle. But it must carry the *method*:

1. Find the client's real differentiator in the intake — the thing a competitor cannot copy by Friday. Ownership and local roots, employed crews vs. subs, a fixed written price, an instant quote, insurance advocacy, a give-back program, a specific material specialism, response time.
2. Name the failure mode of the alternative. Every roofing market has a villain the homeowner already fears: the out-of-town storm crew, the pushy in-home appointment, the bid that changes after tear-off, the roofer who vanishes after the check clears. Pick the one the client's differentiator actually answers.
3. Write the positioning as one sentence in the brief, and make every page carry it. The homepage hero eyebrow, the "Why us" comparison table, and the process section are the three places it must be explicit.
4. If intake gives you nothing usable, say so in the brief and default to *verifiable specifics over adjectives* — real numbers, real names, real photos — rather than inventing a claim.

## Storm damage / insurance module

Optional, not core. Include the storm/insurance track **only** if intake says the client does insurance work. When included:

- One dedicated page: Storm Damage & Insurance Claims.
- Homepage gets one storm mention, no more, placed in the services grid — not the hero.
- Content pattern: what hail and wind damage actually looks like → what the insurance process is step by step → what the client does on the homeowner's behalf (adjuster meetings, documentation, supplements) → what it costs the homeowner (deductible only, stated plainly).
- Never imply a guaranteed claim approval and never suggest the homeowner's deductible can be waived or absorbed. That is insurance fraud in most states and it must be an explicit prohibition in the skill.

When intake says the client is retail-focused and does *not* chase storms, the absence of a storm page is itself a positioning statement — say so in the brief.

---

## The copy system

### Laws (non-negotiable)

1. **H1 = outcome + service + geography. Never a slogan.** "Wayzata's top-rated roofer, built to outlast Minnesota winters" — not "Excellence in every shingle."
2. **Name the problem before naming the service.** Every service section and service page opens on the homeowner's condition (ice dams, curling shingles, a ceiling stain, an insurance letter), then introduces the service as the answer. Never open on the company.
3. **Warranty = years + what it covers.** "10-year workmanship warranty covering labor and flashing" — never "industry-leading warranty," never "lifetime" without the qualifier that makes it true.
4. **Every service page names materials and brands by name.** GAF Timberline HDZ, CertainTeed Landmark, standing-seam steel, LP SmartSide, James Hardie, 5" vs 6" K-style aluminum. Homeowners comparison-shop on product names; unnamed products read as evasion. Pull the real brands from intake — never invent a partnership or a certification the client did not state.
5. **Every CTA offers a free quote or a conversation with an expert.** Those are the only two offers. Primary CTA wording rotates within that family — "Get an instant quote", "Get my free estimate", "Free instant estimate", "Talk to a roofer". Never "Learn more", never "Submit", never "Contact us" as a primary button.

### Additional rules to enforce

- Address the homeowner as **you**, speak as **we**. Never "our clients", never third person.
- Numbers only from intake. Never invent review counts, years in business, project counts, crew sizes, or response times. If a number is missing, write the sentence without it rather than estimating.
- Body copy in blocks of 2–3 sentences. If a paragraph needs four, it is two paragraphs.
- Reviews quoted verbatim with first name, last name if given, city, and the job type. Never a paraphrased or composed review.
- Banned: "quality craftsmanship", "attention to detail", "peace of mind", "your trusted partner", "one-stop shop", "we go above and beyond", "unmatched", "state-of-the-art", "nestled". No em-dash pileups. No emoji.
- Minnesota-style specificity is the target register: plain, concrete, slightly understated. A roofer talking to a neighbor, not a marketer talking to a lead.

### Section headline pattern

Every section headline is Barlow Condensed 800, with **one word wrapped in `<em style="font-style:normal;font-weight:800">`** so the emphasis reads as weight, not italic. On dark grounds the `<em>` takes the accent color instead. Examples from the reference build: "Work that *speaks for itself*", "From estimate to *done*", "The difference, *itemized*", "A price range in under a *minute*", "What your *neighbors* say".

Every section headline is preceded by an **eyebrow pill**: 2–4 words, uppercase, letter-spacing `.28em`, 11.5px Barlow 600, in a rounded 99px chip. On light grounds: `background:#f2f2f3; border:1px solid #d9d9dc; color:var(--hxd)`. On dark grounds: `background:rgba(255,255,255,.1); border:1px solid rgba(255,255,255,.28); backdrop-filter:blur(12px); color:#fff`.

---

## The design system (locked structure, locked effects)

Reproduce these values literally in `references/design-system.md`. They are the system, not suggestions.

### Palette

| Role | Value | Use |
| --- | --- | --- |
| Deep navy | `#0f1f3a` | Primary brand ground, all headings, dark sections, nav, footer |
| Hero navy | `#0a1830` | Behind hero video only |
| Accent | `#e8a020` (exposed as `--hx`) | CTAs, stat figures, active states, `<em>` on dark |
| Accent deep | `#b87c14` (`--hxd`) | Accent-colored *text* on light grounds — eyebrows, links, checkmarks |
| Accent ink | `#ffffff` (`--hxi`) | Text on accent fills |
| Body text | `#54585f` | All paragraph copy |
| Muted | `#8c9098` | Meta, captions, the "typical roofer" column |
| Light ground | `#f2f2f3` | Alternating section background |
| Hairline | `#d9d9dc`, rows `#d2d2d6`, dividers `#e4e4e7` | All borders |
| Confirm green | `#3fae5f` | Hero trust-strip checkmarks only |

Accent-as-text always uses `--hxd`, never `--hx` — the amber fails contrast at paragraph size. Bake that rule in.

**Client brand override:** navy + amber is the skill's default identity and should ship as-is unless the client's brand demands otherwise. When it does, the only edit is the token block at the top: swap the navy for the client's dark, the amber for their accent, and derive `--hxd` as a darkened accent step that clears 4.5:1 on white. Nothing else in the system changes. Document this as a single-block override, not a re-theme.

### Type

- Headings: **Barlow Condensed** 700/800, `letter-spacing:-.01em` to `-.025em`, `line-height:1.04–1.15`.
- Body and all UI: **Barlow** 400/500/600/700.
- Load: `https://fonts.googleapis.com/css2?family=Barlow:wght@400;500;600;700&family=Barlow+Condensed:wght@500;600;700;800&display=swap`
- Scale: H1 `clamp(40px,5vw,68px)` · H2 `clamp(30px,3.4vw,42px)` · H3 28px · lead `17.5px/1.65` · body `15–16px/1.7` · eyebrow `11.5px` `.28em` uppercase · button `15px/700` · micro-label `11.5px` `.18em` uppercase.
- `text-wrap: pretty` on every paragraph.

### Geometry and rhythm

- Content max-width `1180px`; narrow blocks `640px`; comparison table `900px`.
- **Section padding is a client variable.** Default `clamp(56px,9vw,104px) 20px`; expose a Comfortable (`clamp(72px,11vw,128px)`) and Tight (`clamp(44px,7vw,80px)`) alternative that swaps globally.
- Radii: cards and images `14px`; panels `18–24px`; the process image panel `32px`; every pill and button `99px`.
- Backgrounds alternate white → `#f2f2f3` → white, with one navy or photo-parallax break per page. Never two photo breaks in a row.
- Shadows: cards `0 12px 40px rgba(15,31,58,.06)`; images `0 20px 40px rgba(15,31,58,.18)`; glass `0 16px 44px rgba(0,0,0,.32)`; hover lift `0 14px 36px rgba(15,31,58,.1)`.

### The effect grammar (locked — these are the site's signature)

Reproduce these verbatim in the skill.

1. **`.shiny-cta`** — the primary button. Navy fill, animated conic-gradient border that sweeps the accent around the perimeter via `@property --gradient-angle`, a stippled radial mask inside, a rotating shimmer, and a breathing inner glow on hover. `border-radius:360px`. Hover widens `--gradient-percent` to 20% and offsets the angle 95deg. This is the hero/nav/section CTA.
2. **`.yellow-cta`** — the alternate primary. Solid accent fill, a `115deg` white sheen sweeping across every 3.2s (`@keyframes hxShine`), `translateY(-2px)` on hover, text flips to navy. Use where the ground is already navy.
3. **Glass panels** — `background:linear-gradient(150deg, rgba(255,255,255,.17), rgba(255,255,255,.06))`, `backdrop-filter:blur(26px) saturate(1.5)`, `1px solid rgba(255,255,255,.3)`, plus a diagonal sheen sweep on `::after`. Used for hero proof cards, the featured-project review card, and hero eyebrow pills.
4. **Tilt on hover** — glass badges track the cursor via `onMouseMove` and apply a `perspective(600px) rotateX/rotateY` transform with `transition:transform 200ms ease-out`.
5. **Parallax break** — `background-attachment:fixed` with a navy gradient scrim over it (`rgba(15,31,58,.82)` → `.72` → `.88`), a 3px accent rule pinned to the bottom edge, centered copy at `max-width:760px`. Must degrade to `background-attachment:scroll` under 900px.
6. **Ken Burns** — hero and feature images scale `1.02 → 1.1` over a long duration (`@keyframes hxKen`).
7. **Reveal set** — `hxSlideL` / `hxSlideR` / `hxScaleIn` / `hxFade` / `hxPanY`, 0.35–0.5s, staggered 50ms per element. Used on process step changes.
8. **Reduced motion** — one `@media (prefers-reduced-motion: reduce)` block kills every animation via the `[data-anim]`, `[data-ken]`, `[data-ring-spin]` attribute hooks. Mandatory, never optional.
9. **Animation intensity is a client variable:** Full (default) / Reduced (reveals only, no ambient loops) / Off (respects reduced-motion globally).

---

## The component library (all ten mandatory)

Write `references/components.md` with the full mechanics of each. Every one of these appears in every roofing build.

**1. Video hero with glass proof cards.** Full-bleed `<video autoplay muted loop playsinline>` with a poster, a five-stop navy-to-solid gradient scrim, min-height 100vh. Content stack: Google-review chip (real Google G mark, review count, five amber stars) → eyebrow pill carrying the positioning → H1 at `clamp(42px,5.4vw,74px)` → 17.5px lead at `max-width:600px` → primary `.shiny-cta` + ghost secondary → a trust strip above a hairline top border with three green-check items (licensed & insured / financing / experience). Glass proof cards pinned bottom-right on desktop, hidden under 1120px. **Hero media is a client variable:** video, or the same layout on a static image with Ken Burns. Ship both branches.

**2. Sticky mobile call bar / desktop CTA pill.** Fixed, centered, `bottom:28px`, accent fill, navy text, `border-radius:99px`, entering with `hxStickyIn`. Hidden under 840px in favour of a full-width tap-to-call bar. This is how "phone visible at every scroll position" gets satisfied.

**3. Before/after drag slider.** Two stacked absolutely-positioned images in a 16/11 or 4/3 frame with `border-radius:14px`; the after image clipped by `clip-path:inset(0 calc(100% - var(--pos)) 0 0)` or a width-driven wrapper; a 2px accent handle with a circular grab knob at `--pos`; pointer, touch and keyboard (arrow key) control; BEFORE / AFTER labels in `11.5px .18em` uppercase pinned to the corners. Every build ships at least three, captioned with the real job type and city.

**4. Numbered process rail.** Left column of five numbered rows (`/01`…`/05` in 10px Barlow 500, `#8c9098`). Each row: `padding:26px 0 26px 22px`, a 2px vertical rail at `left:0` in `#e4e4e7`, with an accent fill element that animates height over 5s (`hxGrowV`) on the active step only. Titles Barlow Condensed `clamp(22px,2.6vw,30px)`, `#b0b3b8` → `#0f1f3a` when active (`.hx-proc-title.is-active`, `transition:color .5s`). The description renders only on the active step, fading in. **Row 1's top border is `transparent`; rows 2–5 get `1px solid #e4e4e7`.** Right column: a paired image panel, `aspect-ratio:1/1`, `border-radius:32px`, changing with the step, with prev/next circular glass buttons bottom-right and auto-advance that pauses on hover. Not a grid of numbered cards, ever.

**5. Two-column accordion FAQ.** Left column: eyebrow pill → Barlow Condensed H2 with the `<em>` emphasis → a supporting line at `max-width:380px` promising a real human reply → a photo at `border-radius:14px`. Right column: rows separated by `1px solid #d2d2d6` hairlines (the list has a bottom border and each row a top border). Question in Barlow Condensed 700 / 18.5px; a `+` in Barlow Condensed 26px `--hxd` that rotates 45° when open; the answer revealed by animated `max-height` 0 → 340px with opacity, `transition:max-height .4s, opacity .35s`. Not a card grid, not show/hide. 8 questions minimum, drawn from real objections in the discovery call.

**6. Instant estimate calculator.** A four-step, no-contact-details-required estimator that returns a price *range*, embedded in an iframe at `border-radius:20px` with a "open in its own page" link beneath. Steps: project type → home size or roof footprint → material tier → timeline. Output a range with a stated basis ("priced against current industry benchmarks") and a single CTA to convert the range into a fixed written quote. Copy law: the range is never presented as a quote. If the client refuses pricing transparency, replace with a multi-step quote form of the same visual weight — never delete the section.

**7. Parallax image break.** As specified in the effect grammar. One per page, used for the community / values / give-back beat.

**8. Owner welcome section.** Two-column, `align-items:stretch`, `gap:44px 60px`. Left: owner-with-crew photo, `min-height:420px`, `object-fit:cover`, `border-radius:14px`, hairline border. Right: eyebrow → H2 → two paragraphs of first-person founder story (where he's from, why he started it, what he refuses to do) → an underlined text CTA with an arrow → a service-area chip row. This is the trust engine of the whole site; it is never a generic "About us" blurb.

**9. Reviews wall.** Photo-parallax section, navy scrim, header row with the section heading left and a floating white Google-rating card right (count + stars + "5-star Google reviews"). Then a `repeat(auto-fit,minmax(290px,1fr))` grid of white cards, `border-radius:16px`, each with a giant Georgia `"` glyph at 12% opacity top-right, amber stars, verbatim quote, and an attribution row: initial avatar circle, name, job type, and a "Verified Google review" line with the Google mark. Never anonymous, never composed.

**10. Warranty & credentials block.** The "Why us, itemized" comparison table: a `1fr 1fr` grid inside a `border-radius:14px` hairline frame. Left header navy with the client's name in Barlow Condensed; right header `#f2f2f3` reading "The Typical Roofer" (or the villain named in positioning). Then 8–9 paired rows — left `✓` in `--hxd` with the client's practice in 600 weight navy; right `✗` in `#c4c4c8` with the failure mode in 400 weight `#8c9098`. Each row `border-top:1px solid #d9d9dc`, left cell `border-right`. Warranty terms, license and insurance status, and financing all appear as rows here with real specifics.

**Supporting components** to also spec: the nav (fixed, transparent over hero, gaining a navy gradient on scroll; logo at `clamp(62px,9.8vw,95px)`; uppercase `.14em` links; Services and Service Areas dropdowns; phone number with icon; primary CTA — plus a mobile hamburger sheet), the stats bar (equal navy cells, 1px gaps, 44px Barlow Condensed accent figures over `.2em` uppercase labels), the services grid, the gallery (coverflow / 3D turntable / auto-scrolling marquee — ship all three as a variant), and the footer.

---

## Page recipes

Write `references/page-recipes.md` with the section order for each. Defaults:

**Homepage** — Nav · Hero (video + proof cards) · Stats bar · Owner welcome + service-area chips · Featured project (full-bleed, with a floating glass review card) · Services grid · Gallery · Reviews wall · Before/after sliders · Process rail · Instant estimate · Parallax community break · Why us comparison · FAQ · Footer.

**About** — Hero (owner portrait) · Founder story long-form · The crew · Values / give-back · Credentials and licensing · Reviews · CTA band.

**Services index** — Hero · Services grid with photo per service · Why us comparison · Process rail · FAQ · CTA band.

**Individual service page** (one per: roofing, siding, windows, gutters, commercial, storm if applicable) — Hero naming service + geography · The problem (symptoms the homeowner recognizes) · What we install, **by brand and material name**, with specs · Before/after slider for that service · Process rail scoped to that service · Warranty terms for that service · Pricing guidance or estimator link · Service-specific FAQ · CTA band.

**Commercial roofing** — as above but with the audience swapped to property managers: flat-roof systems (TPO, EPDM, modified bitumen), tenant-disruption handling, maintenance programs, references, and a "request a building assessment" CTA in place of the estimator.

**Process** — Hero · The full rail expanded with a paragraph per step · What we need from you · What happens on day one · Timeline expectations · FAQ · CTA.

**Our Work** — Hero · Filter tabs by service · Before/after sliders as the primary content, three minimum per service · Project detail cards with city, material, and duration · Reviews · CTA.

**Why Choose Us** — Hero · The comparison table as the centrepiece · Credentials and warranty detail · The give-back or community commitment · Reviews · FAQ · CTA.

**Contact** — Hero · Form (name, phone, email, address, service, timeline, message) beside the phone number, hours, and service-area list · Map · Response-time promise · FAQ on what happens after you submit.

**Free quote landing** — No nav links except the logo. Hero with the form or estimator above the fold. Trust strip. Three reviews. The process in three compressed steps. One CTA, repeated. Nothing else — no gallery, no blog, no footer nav.

**City page** — see below.

---

## City pages: deep, not templated

This is the highest-value part of the skill. Each city page must read as though it were written for that town only. Section order:

1. **Hero** — photo of a real local roof, navy scrim plus a radial accent glow at 78% 12%, eyebrow reading "Roofing, Siding, Windows & Gutters in [City], [ST]", H1 in uppercase Barlow Condensed with the accent `<em>` carrying the local claim, a lead paragraph that proves local knowledge in its first clause, primary CTA + tap-to-call, and a trust strip whose middle item names the state license.
2. **Credibility bar** — a full-width accent-fill band with 4 figures in navy Barlow Condensed 30px over `.16em` uppercase labels. One of the four is the city's zip code. That single detail does more for local credibility than a paragraph.
3. **Local intro** — two columns; why this city specifically, named by neighborhood, lake, or landmark.
4. **Quick answers** — parallax break with 4–6 city-specific Q&As: permit process and cost in that jurisdiction, typical roof age in that housing stock, the weather pattern that actually kills roofs there (hail corridor, ice dams, lake wind, freeze-thaw cycles), and typical turnaround.
5. **Services in [City]** — the grid, with each card's copy naming a local condition.
6. **Local reviews** — reviews from that city only. If there are fewer than three, use the nearest ones and label the city honestly.
7. **Process rail** · **Why us comparison** · **City FAQ** · **Nearby areas** cross-link grid · Footer.

**Rules:** every city page must contain at least four facts true only of that city — housing stock era, permit authority and fee, a named weather exposure, named neighborhoods, and a local project. Never publish two city pages whose body copy differs only by a find-and-replace on the name. If intake doesn't supply local specifics, the skill lists what to ask the client rather than inventing them. And never state a permit fee or code requirement as fact unless intake supplied it — flag it for the client to confirm.

---

## CRO rules (enforce on every page, every time)

1. Phone number reachable at every scroll position — nav on desktop, sticky bar on mobile, tap-to-call `href="tel:"` always.
2. A primary CTA every two sections, minimum. Never two sections in a row without one.
3. Trust signals inside the first viewport: review count with stars, licensed and insured, and one local proof.
4. Real project photography over stock, always. A real photo of an average roof beats a stock photo of a perfect one.
5. Financing mentioned in the first half of the homepage and as a row in the comparison table.
6. A response-time promise stated explicitly and identically everywhere ("a real person replies within one business day").
7. Every form field justified — if it isn't used to price or schedule the job, delete it.
8. One primary offer per page. The free-quote landing has exactly one CTA target.

## Missing assets

When the client hasn't supplied photos, build the section anyway with stock placeholders carried through the design system's photo treatment — full colour, no filter, same radius, same hairline border, same shadow — so the layout reads correctly at review. Then output a **shot list** at the end of Phase 4: exactly which photos are needed, at what aspect ratio, and what each must show (owner with crew, three before/after pairs per service, one crew-at-work shot per process step, one local roof per city page).

## Tweaks to expose

When building as Design Components, expose these as props so I can switch them without editing code: hero style (video / static), proof cards (glass / badges), nav style, gallery style, services layout, section rhythm (tight / default / comfortable), animation intensity, estimator on/off, sticky CTA on/off, storm module on/off.

## Prohibitions

- Never invent a review, a statistic, a certification, a manufacturer partnership, a warranty term, a permit fee, or a years-in-business figure.
- Never promise an insurance outcome or imply a deductible can be waived.
- Never replace the FAQ pattern with a card grid, or the process rail with numbered cards.
- Never use the amber at paragraph size on white.
- Never ship a page whose only local content is a swapped city name.
- No emoji, no gradient-soup backgrounds, no rounded box with a left accent border, no Inter.

## Deliverable format

For each phase, output in chat as clean markdown I can paste into client docs. For Phase 4, write the files. Close with the "Assumptions to confirm" list and the shot list. Nothing else — no summary of what you just did.
