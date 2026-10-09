# VM CarouselGen — JSON Schema Reference

## The fix this tool makes over the original `ethical_hacking_carousel_gen.html`

The original tool's `generateSlides()` always did `JSON.parse(raw)` and read
`DATA.day` / `DATA.cover` / `DATA.slides` directly off the parsed result —
so it only ever worked with **one day object at a time**. Feeding it your
7-day array (`phase01_days1-7.json`) silently broke, because `DATA.slides`
doesn't exist on an array.

This tool fixes that by normalizing the input first:

```js
function normalizeInput(raw){
  let parsed = JSON.parse(raw);
  if(Array.isArray(parsed)) return parsed;   // 7-day file → 7 posts
  return [parsed];                            // single post → still works
}
```

Paste either shape and it just works — a dropdown appears automatically
when there's more than one post, and a "ZIP — All Posts" button exports
every post in one go, each into its own subfolder.

---

## Top-level shapes accepted

**Single post:**
```json
{ "title": "...", "brand": {...}, "slides": [ ... ] }
```

**Array of posts (e.g. 7 days):**
```json
[
  { "day": 1, "title": "...", "slides": [ ... ] },
  { "day": 2, "title": "...", "slides": [ ... ] },
  ...
]
```

`day` is optional — used only to label the post-switcher dropdown and to
name exported files/folders (`day01-carousel.zip` vs `post1-carousel.zip`).

`brand` is optional per-post — if omitted, the tool falls back to the
Brand Name / Handle / Shortcode fields in the left panel.

---

## Slide types

### `cover` (always slide 1 of a post)
```json
{
  "type": "cover",
  "headline": "🧑‍💻 Unlock the Mindset of Successful Programmers... 💡💾",
  "concept_echo_label": "Programmer Mindset",
  "float_emoji": "&#127918;"
}
```
- `headline` — plain string, inline emoji are detected automatically and sized correctly. `**bold**` works too.
- `concept_echo_label` — optional. Omit it to skip the hand-drawn arrow callout entirely.
- `float_emoji` — optional decorative floating emoji, HTML entity format (e.g. `&#127918;` for 🕹️).

### `content` (the repeatable body slides — use 8–18 of these per post)
```json
{
  "type": "content",
  "label": "Practical Application, Ego, Discomfort",
  "points": [
    { "lead_emoji": "&#128273;", "text": "**Bold lead-in.** Rest of sentence.", "trail_emoji": "&#127775;" }
  ]
}
```
- `points` — array of 2–4 objects. 3 is the sweet spot (matches reference design). The CSS auto-adjusts spacing/font-size if you use 2 or 4.
- `text` supports `**bold**` markdown, auto-converted to `<strong>`.
- `label` is only used in the right-hand slide list in the UI — not rendered on the actual slide.

### `cta` (always the last slide of a post)
```json
{
  "type": "cta",
  "heading": "That's the Mindset.<br>Now Go Build.",
  "sub": "Supporting sentence under the heading.",
  "rows": [
    { "icon": "&#128278;", "title": "Join Our WhatsApp Channel", "sub": "wa.me/yourchannel" }
  ],
  "follow_text": "Follow @virtual_mentors_soit",
  "share_label": "share with a friend"
}
```

### `divider` (optional — section-break slide for long 15-20 slide posts)
```json
{ "type": "divider", "heading": "Part Two:<br>Building Habits", "sub": "optional hand-drawn subtitle" }
```
Use this between thematic groups of content slides if a post runs long
and needs a visual breather — it's a big numbered slide with minimal text.

---

## Hitting the 10–20 slide target per post

```
1  cover
8–18  content  (each with 2-4 points → 16-72 individual statements per post)
1  cta
─────────────
10–20 total
```

For a 90-day series broken into 7-day phase files like your existing
`phase01_days1-7.json` through `phase09...json`, each **day** becomes
one **post** in the array, and each day's existing slide types (`dark`,
`red`, `yellow`, `white`, `quote`, `stats`, etc. from the old EH generator)
need their bullet/body content re-bucketed into this tool's `content`
slide's `points` array — 2-3 points worth of text per old slide, split
across as many `content` slides as needed to land in the 10-20 range.

---

## What stays fixed vs what's dynamic (per the original design audit)

**Fixed every slide, every post** — never put these in JSON:
- Logo badge visual (black circle, red ring, checkmark)
- Swipe indicator + save-for-later doodles (cover only)
- Footer brand lockup position/style
- Hand-drawn arrow curve shape

**Dynamic, comes from JSON:**
- Headline text + its inline emoji
- Concept echo label text
- All point text/emoji
- CTA rows, heading, follow text
- Brand name/handle/shortcode (if you rebrand)
