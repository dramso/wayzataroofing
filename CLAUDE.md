# Wayzata Roofing — project rules

## Global component rules (apply to every page on this site)

**FAQ sections** must match the homepage FAQ exactly: two-column layout (left = eyebrow pill + Barlow Condensed heading with one word in `<em style="font-style:normal;font-weight:800">` + supporting line + image; right = list), hairline `1px solid #d2d2d6` row dividers, question in Barlow Condensed 700 / 18.5px, a `+` that rotates 45° when open (`.hx-faq-plus.is-open`), and the answer revealed by animated max-height (`.hx-faq-body.is-open`) — not a card grid, not `sc-if` show/hide.

**Process / step sections** must match the homepage process: numbered rows (`/01`, `/02`…) in a left column with a 2px vertical rail that fills on the active step, Barlow Condensed titles that go from `#b0b3b8` to `#0f1f3a` when active (`.hx-proc-title.is-active`), the description revealed only on the active step, the first row's top border `transparent` (only rows 2+ get the `#e4e4e7` hairline), and a paired image panel on the right (`aspect-ratio:16/11`, `border-radius:32px`) that changes with the step — not a grid of numbered cards.

When adding either pattern to a new page, copy the markup and CSS from `Homepage.dc.html` rather than re-inventing it.
