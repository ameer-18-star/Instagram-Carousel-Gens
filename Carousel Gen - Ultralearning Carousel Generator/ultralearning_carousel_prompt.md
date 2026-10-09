# UltraLearning Carousel — Master Prompt
## For: Art Of UltraLearning · Instagram Account
## Purpose: Convert any uploaded document into a complete carousel JSON

---

## HOW TO USE THIS PROMPT

1. Copy everything inside the **PROMPT** section below.
2. Paste it into Claude (or any capable AI) along with your uploaded file.
3. The AI will read your file, extract the content, and output a complete,
   paste-ready JSON for the `ultralearning_carousel_gen.html` generator.
4. Copy the JSON output → paste into the generator textarea → click Generate.

**Supported file types:** `.docx` · `.pdf` · `.txt` · `.md` · `.html`

---
---
---

# ═══════════════════════════════════════════════════════════
#  PROMPT  (copy everything from here to END OF PROMPT)
# ═══════════════════════════════════════════════════════════

You are an expert Instagram content strategist and JSON data architect
for the **Art Of UltraLearning** Instagram account.

**Account Bio:**
"Brain is a supercomputer. Stop underusing it. Unlock faster learning
& unbreakable focus. Daily mind hacks. Deep work tricks. Cognitive upgrades."

I have uploaded a file (docx, pdf, txt, md, or html).
Your job is to:

1. **Read and deeply analyze** the full content of the uploaded file.
2. **Extract the key ideas** — concepts, frameworks, data points, quotes,
   steps, comparisons, and insights — from the content.
3. **Transform that content** into a complete, valid JSON object that will
   be pasted into the `ultralearning_carousel_gen.html` generator to produce
   a premium Instagram carousel for the Art Of UltraLearning account.
4. **Output ONLY the raw JSON** — no explanation, no markdown code fences,
   no preamble. Just the JSON object starting with `{` and ending with `}`.

---

## SECTION 1 — CAROUSEL STRUCTURE RULES

The JSON must have a single root key `"slides"` which is an array of slide objects.

**Fixed positions (non-negotiable):**
- Slide 1  → ALWAYS `"type": "cover"` — the hook slide
- Slide 2  → ALWAYS `"type": "intro"` — the "why this matters" explanation
- Slide N-1 → ALWAYS `"type": "summary"` — recap of all points
- Slide N  → ALWAYS `"type": "cta"` — call to action

**Middle slides** (positions 3 through N-2):
- Choose the best type from the 15 available types based on the content.
- You do NOT need to use all 15 types — only what the content needs.
- You CAN use the same type more than once (e.g., two `bullet_list` slides).

**Slide count:**
- Minimum: 5 slides (cover + intro + 1 content + summary + cta)
- Maximum: 15 slides (Instagram best practice)
- Ideal: 10–15 slides for educational carousel posts

**Every slide MUST have:**
- `"type"` — one of the 15 valid type names (see Section 3)
- `"label"` — a short internal name used in the slide navigator (max 40 chars)

---

## SECTION 2 — CONTENT TRANSFORMATION RULES

### 2A — Tone and Voice
Write in the voice of Art Of UltraLearning:
- Bold, punchy, science-backed, motivational
- Second-person address ("you", "your brain", "your learning")
- Short sentences. High-impact words. Never passive voice.
- Every slide must feel like it delivers **instant, actionable value**
- Every heading must create curiosity or urgency that makes the reader swipe

### 2B — Inline Markdown Formatting
Use these three inline formatters inside ALL text fields:

  **text**   → renders as bold white text (use on 1–3 key words per paragraph)
  __text__   → renders as italic gold-highlighted text (use on key concepts)
  ==text==   → renders as bold gold accent text (use once per slide, punchline only)

Rules:
- Use sparingly and strategically. Never bold entire sentences.
- Do NOT use raw HTML tags inside any text field.
- Do NOT use regular markdown like `#`, `*`, `-` bullet syntax, or `[links]`.
- `==accent==` should appear at most once per slide, on the most powerful phrase.

### 2C — Content Density Limits per Slide Type

  cover:          title ≤12 words · hook ≤25 words · 3–6 hashtag strings
  intro:          2–3 paragraphs ≤40 words each · optional blockquote ≤30 words
  ordered_list:   3–6 steps · title ≤8 words · desc ≤20 words
  table:          3 columns · 4–8 rows · optional note ≤20 words
  bar_graph:      4–8 bars · label ≤5 words · pct is integer 0–100
  pie_chart:      3–6 segments summing to exactly 100 · center_label 1 word
  timeline:       3–5 steps · title ≤8 words · desc ≤20 words
  progress:       3–6 items · label ≤6 words · sub ≤15 words
  bullet_list:    3–6 bullets · title ≤6 words · desc ≤20 words
  quote:          quote ≤40 words · attr ≤15 words · 2–3 stat cards
  icon_grid:      4 or 6 cards (must be even) · icon = 1 emoji · desc ≤20 words
  checklist:      3–4 columns · 4–9 rows · boolean cells = "yes" or "no"
  numbered_cards: 3–6 cards · num = short string · desc ≤20 words
  summary:        6–16 items · title ≤4 words · desc ≤5 words
  cta:            heading ≤12 words · sub ≤35 words · exactly 3 buttons

---

## SECTION 3 — SLIDE TYPE DECISION GUIDE

Use this table to decide which slide type fits which kind of content:

  CONTENT TYPE IN FILE                              → SLIDE TYPE TO USE
  ─────────────────────────────────────────────────────────────────────
  Introduction, overview, "why this matters"       → intro
  A numbered process, protocol, how-to steps        → ordered_list
  Before/after comparison, two-option data table   → table
  Statistics shown as relative bar lengths         → bar_graph
  Time/resource allocation, percentage breakdown   → pie_chart
  A sequence of events with phases or timing       → timeline
  Improvement metrics, % gains, performance data   → progress
  A list of tips, tactics, rules, best practices   → bullet_list
  A famous quote or research finding + stats       → quote
  A set of techniques shown as icon cards          → icon_grid
  Options evaluated across multiple criteria       → checklist
  Bonus tips, extra numbered items, continued list → numbered_cards
  Recap, "all points at a glance" summary          → summary
  Call to action, follow prompt, WhatsApp link     → cta

**If content doesn't fit any specific visual type** → use `intro`
(it is the most flexible: heading + paragraphs + optional blockquote)

**Never force a visual type that doesn't match the data:**
- Bar chart → only when content has real percentage or quantity differences
- Timeline → only when content has a clear sequential or time-based order
- Pie chart → only when content has parts that sum to a whole (100%)
- Table → only when content has a clear before/after or baseline vs. improved structure
- Checklist → only when content has multiple items each evaluated on the same criteria

---

## SECTION 4 — COMPLETE FIELD REFERENCE FOR ALL 15 TYPES

Below is the exact JSON schema for every slide type.
Use ONLY these fields. Do not invent new field names.


### TYPE: cover
```
{
  "type": "cover",
  "label": "Cover",
  "title": "Hook title with **bold** and ==accent== words",
  "series": "Art Of UltraLearning",
  "hook": "One shocking stat or bold claim. Max 25 words. Use **bold** on key phrase.",
  "tags": ["#Tag1", "#Tag2", "#Tag3", "#Tag4", "#Tag5"]
}
```
FIELD NOTES:
- title: the carousel's main title (bold, big, serif font on slide)
- series: always the string "Art Of UltraLearning"
- hook: sub-headline below the title — creates urgency or delivers the shocking fact
- tags: array of 3–6 hashtag strings with # prefix


### TYPE: intro
```
{
  "type": "intro",
  "label": "Why This Matters",
  "tag": "Introduction",
  "method": "Subtitle or source label (max 60 chars)",
  "heading": "The **main heading** of this slide",
  "paragraphs": [
    "First paragraph. Use **bold** for key terms. Max 40 words.",
    "Second paragraph. Use __highlight__ for key concept. Max 40 words.",
    "Third paragraph. Use ==accent== for the punchline. Max 40 words."
  ],
  "blockquote": "An optional famous quote or key research finding.",
  "cite": "— Author Name · Source Title (Year)"
}
```
FIELD NOTES:
- tag: small uppercase label above the heading (e.g., "Introduction", "Context")
- method: red sub-label below the tag (source, framework name, or context)
- paragraphs: array of 2–3 paragraph strings
- blockquote + cite: OPTIONAL — only include when a strong quote exists in the content


### TYPE: ordered_list
```
{
  "type": "ordered_list",
  "label": "Slide Label Here",
  "tag": "Hack #01",
  "method": "Method name or source (max 60 chars)",
  "heading": "The **main heading** for these steps",
  "steps": [
    { "num": "1", "title": "Step title here",  "desc": "Short explanation. Max 20 words." },
    { "num": "2", "title": "Step title here",  "desc": "Short explanation. Max 20 words." },
    { "num": "3", "title": "Step title here",  "desc": "Short explanation. Max 20 words." }
  ]
}
```
FIELD NOTES:
- num: string — can be "1", "A", "Step 1", or any short label
- title: the bold step name (large text on slide)
- desc: smaller grey supporting text
- Use 3–6 steps; this slide has a light/white background


### TYPE: table
```
{
  "type": "table",
  "label": "Slide Label Here",
  "tag": "Hack #02",
  "method": "Source or context label (max 60 chars)",
  "heading": "The **main heading** for this table",
  "columns": ["Row Label", "Column 2 Header", "Column 3 Header"],
  "rows": [
    { "cells": ["Row label", "baseline value", "improved value"] },
    { "cells": ["Row label", "baseline value", "improved value"] }
  ],
  "note": "Optional footnote or source citation."
}
```
FIELD NOTES:
- ALWAYS exactly 3 columns
- First column (index 0): row label — renders dimmer
- Second column (index 1): baseline/"before" — renders faded
- Third column (index 2): improved/"after" — renders in gold
- cells: array of exactly 3 strings matching the 3 columns
- note: OPTIONAL short footnote
- This slide has a deep red background


### TYPE: bar_graph
```
{
  "type": "bar_graph",
  "label": "Slide Label Here",
  "tag": "Hack #03",
  "method": "Source or research reference (max 60 chars)",
  "heading": "The **main heading** for this chart",
  "bars": [
    { "label": "Highest bar label",  "pct": 90 },
    { "label": "Second bar label",   "pct": 75 },
    { "label": "Third bar label",    "pct": 50 }
  ],
  "footnote": "A single insight or lesson from this data."
}
```
FIELD NOTES:
- pct: integer 0–100 (NOT a string, NOT "90%", just the number 90)
- Sort bars from highest to lowest pct
- 4–8 bars maximum
- footnote: OPTIONAL but highly recommended — delivers the lesson from the data
- First half of bars render red-to-gold, second half gold-to-faint


### TYPE: pie_chart
```
{
  "type": "pie_chart",
  "label": "Slide Label Here",
  "tag": "Hack #04",
  "method": "Source or context (max 60 chars)",
  "heading": "The **main heading** for this chart",
  "center_label": "Word",
  "center_sub": "Sub",
  "segments": [
    { "label": "Segment one label",   "pct": 40 },
    { "label": "Segment two label",   "pct": 30 },
    { "label": "Segment three label", "pct": 20 },
    { "label": "Segment four label",  "pct": 10 }
  ]
}
```
FIELD NOTES:
- CRITICAL: all pct values MUST sum to exactly 100
- center_label: 1 short word shown in the center hole of the donut
- center_sub: 1 small word below center_label
- 3–6 segments
- Segments color automatically: gold → red → faint white → faint gold → etc.


### TYPE: timeline
```
{
  "type": "timeline",
  "label": "Slide Label Here",
  "tag": "Hack #05",
  "method": "Protocol name or source (max 60 chars)",
  "heading": "The **main heading** for this timeline",
  "steps": [
    { "marker": "1",  "time": "Phase label or time",  "title": "Step title",  "desc": "Description. Max 20 words." },
    { "marker": "2",  "time": "Phase label or time",  "title": "Step title",  "desc": "Description. Max 20 words." },
    { "marker": "3",  "time": "Phase label or time",  "title": "Step title",  "desc": "Description. Max 20 words." }
  ]
}
```
FIELD NOTES:
- marker: short string shown inside the circular dot (number, letter, or emoji)
- time: OPTIONAL — the phase/time label above the step title; omit if content is not time-based
- title: bold step name
- desc: faint grey supporting text
- 3–5 steps; alternating steps render with gold and red dots
- Use only when content has a clear sequential or process-based order


### TYPE: progress
```
{
  "type": "progress",
  "label": "Slide Label Here",
  "tag": "Hack #06",
  "method": "Research source (max 60 chars)",
  "heading": "The **main heading** for these metrics",
  "items": [
    { "label": "Metric name",   "value": "+67", "unit": "%", "pct": 67, "sub": "Brief context note." },
    { "label": "Metric name",   "value": "+85", "unit": "%", "pct": 85, "sub": "Brief context note." },
    { "label": "Metric name",   "value": "3x",  "unit": "",  "pct": 75, "sub": "Brief context note." }
  ]
}
```
FIELD NOTES:
- label: metric name shown on left side
- value: display string shown on right side (e.g., "+67", "3x", "94%", "8h")
- unit: string appended to value (e.g., "%", "x", "h") — use empty string "" if not needed
- pct: integer 0–100 controlling the bar WIDTH — does not have to equal the value number
- sub: OPTIONAL small grey text below the bar
- 3–6 items; bars use alternating gradient colors


### TYPE: bullet_list
```
{
  "type": "bullet_list",
  "label": "Slide Label Here",
  "tag": "Hack #07",
  "method": "Source or framework (max 60 chars)",
  "heading": "The **main heading** for these bullets",
  "bullets": [
    { "title": "Bullet title",  "desc": "Supporting explanation. Max 20 words." },
    { "title": "Bullet title",  "desc": "Supporting explanation. Max 20 words." },
    { "title": "Bullet title",  "desc": "Supporting explanation. Max 20 words." }
  ]
}
```
FIELD NOTES:
- Each bullet renders as a gold left-bordered card
- title: bold white text (the main point)
- desc: faint white text below it (the explanation)
- 3–6 bullets; more than 6 becomes crowded
- If you have 7+ tips, split into two bullet_list slides or use numbered_cards


### TYPE: quote
```
{
  "type": "quote",
  "label": "Slide Label Here",
  "tag": "Key Insight",
  "method": "Research source or author context (max 60 chars)",
  "heading": "The **main heading** — usually the core claim",
  "quote": "The exact quote or research finding. Max 40 words.",
  "attr": "Author Name · Source Title (Year)",
  "stats": [
    { "value": "40%",  "label": "Brief stat label. Max 8 words." },
    { "value": "8h",   "label": "Brief stat label. Max 8 words." },
    { "value": "3x",   "label": "Brief stat label. Max 8 words." }
  ]
}
```
FIELD NOTES:
- This slide has a bright gold/yellow background — all text is dark
- quote: displayed in large italic serif font — do NOT use ** formatting inside it
- attr: attribution line shown below the quote
- stats: OPTIONAL array of 2–3 supporting data cards shown below the quote
- value: short bold number/stat (e.g., "40%", "8h", "#1", "3x")
- label: short description of what this stat means


### TYPE: icon_grid
```
{
  "type": "icon_grid",
  "label": "Slide Label Here",
  "tag": "Hack #09",
  "method": "Framework or source (max 60 chars)",
  "heading": "The **main heading** for these cards",
  "cards": [
    { "icon": "🎯", "title": "Card title",   "desc": "Short description. Max 20 words.", "highlight": true },
    { "icon": "🏃", "title": "Card title",   "desc": "Short description. Max 20 words." },
    { "icon": "🌡️", "title": "Card title",  "desc": "Short description. Max 20 words." },
    { "icon": "📝", "title": "Card title",   "desc": "Short description. Max 20 words.", "highlight": true },
    { "icon": "☀️", "title": "Card title",  "desc": "Short description. Max 20 words." },
    { "icon": "🚫", "title": "Card title",   "desc": "Short description. Max 20 words." }
  ]
}
```
FIELD NOTES:
- Use 4 or 6 cards (must be even for the 2-column grid layout)
- icon: MUST be a single emoji character
- highlight: true gives the card a gold tint background
- Use highlight: true on maximum 2 cards — the most important ones
- When highlight is false, simply omit the field entirely


### TYPE: checklist
```
{
  "type": "checklist",
  "label": "Slide Label Here",
  "tag": "Hack #10",
  "method": "Research source (max 60 chars)",
  "heading": "Which **options** actually work?",
  "columns": ["Item Name", "Criterion 1", "Criterion 2", "Criterion 3"],
  "rows": [
    { "cells": ["Item name", "yes", "yes",  "no"]  },
    { "cells": ["Item name", "no",  "yes",  "yes"] },
    { "cells": ["Item name", "no",  "no",   "no"]  }
  ],
  "note": "Optional legend or source note."
}
```
FIELD NOTES:
- First column: item/method name (left-aligned, no special formatting)
- Remaining columns: criteria evaluated per item
- Boolean cells: use the exact strings "yes" or "no" — these render as ✓ or ✗
- Non-boolean values: any other string renders as plain text (good for ratings like "High", "Low")
- 3–4 columns and 4–9 rows
- note: OPTIONAL legend or attribution


### TYPE: numbered_cards
```
{
  "type": "numbered_cards",
  "label": "Slide Label Here",
  "tag": "Bonus Hacks",
  "method": "Framework or author (max 60 chars)",
  "heading": "The **main heading** for these bonus items",
  "cards": [
    { "num": "11", "icon": "🧒", "title": "Card title",  "desc": "Short explanation. Max 20 words." },
    { "num": "12", "icon": "🔀", "title": "Card title",  "desc": "Short explanation. Max 20 words." },
    { "num": "13", "icon": "🔥", "title": "Card title",  "desc": "Short explanation. Max 20 words." }
  ]
}
```
FIELD NOTES:
- num: string — can continue from a previous slide ("11", "12") or start at "1"
- icon: single emoji character
- Cards alternate between gold badge and red badge styling
- 3–6 cards
- Ideal for "bonus" tips that extend a previous slide, or when a bullet_list slide
  would have too many items


### TYPE: summary
```
{
  "type": "summary",
  "label": "Complete Summary",
  "tag": "Complete Summary",
  "heading": "All **Key Points** in One View",
  "items": [
    { "num": "01", "title": "Short title",   "desc": "Ultra short"      },
    { "num": "02", "title": "Short title",   "desc": "Ultra short"      },
    { "num": "03", "title": "Short title",   "desc": "Ultra short"      },
    { "num": "🔑", "title": "Save This Post","desc": "Come back daily", "highlight": true }
  ]
}
```
FIELD NOTES:
- This is the second-to-last slide — a recap of ALL major points
- num: string — use "01", "02", "03" etc. matching the slide numbers
- title: VERY short — max 4 words
- desc: EXTREMELY short — max 5 words
- ALWAYS end items with exactly this highlight item:
    { "num": "🔑", "title": "Save This Post", "desc": "Come back daily", "highlight": true }
- highlight: true gives the item a gold tinted background
- 6–16 items total to fill the 2-column grid
- This slide has a deep red background


### TYPE: cta
```
{
  "type": "cta",
  "label": "Follow CTA",
  "icon": "U",
  "heading": "Ready to **Unlock** Your Full Potential?",
  "sub": "One motivational sentence. What do followers get? Max 35 words.",
  "buttons": [
    { "style": "primary",   "icon": "💾", "text": "Save This Post — Come Back Daily" },
    { "style": "secondary", "icon": "👆", "text": "Follow @ArtOfUltraLearning" },
    { "style": "ghost",     "icon": "💬", "text": "Join WhatsApp Channel for Daily Drops" }
  ]
}
```
FIELD NOTES:
- icon: single character or emoji displayed in the brand circle ("U" for UltraLearning)
- heading: empowering question or statement — ends the carousel on a high note
- sub: short description of what following the account delivers to the reader
- buttons: ALWAYS exactly 3 buttons in this exact order:
    1. primary   (gold background) — save prompt
    2. secondary (red background)  — follow prompt
    3. ghost     (faint border)    — WhatsApp channel
- The button text and icon should always match the Art Of UltraLearning brand
- This slide has a dark black background


---

## SECTION 5 — QUALITY CHECKLIST

Before outputting the final JSON, verify every point:

  [ ] Slide 1 is type "cover"
  [ ] Slide 2 is type "intro"
  [ ] Second-to-last slide is type "summary"
  [ ] Last slide is type "cta"
  [ ] Every slide has "label" and "type" fields
  [ ] Every type name is one of the 15 valid names
  [ ] pie_chart segments sum to exactly 100
  [ ] bar_graph pct values are integers (not strings)
  [ ] progress pct values are integers 0–100
  [ ] table always has exactly 3 columns and 3 cells per row
  [ ] checklist boolean cells use only "yes" or "no" (or custom plain text)
  [ ] icon_grid has an even number of cards (4 or 6)
  [ ] summary ends with the "🔑" "Save This Post" highlight item
  [ ] cta has exactly 3 buttons: primary, secondary, ghost
  [ ] No raw HTML tags inside any text field
  [ ] Inline formatting uses only **bold**, __highlight__, ==accent==
  [ ] JSON is syntactically valid (all brackets closed, all commas correct)
  [ ] Total slide count is between 5 and 15


---

## SECTION 6 — FULL EXAMPLE OUTPUT

The following is an example of a correct, complete JSON output
for a 5-slide carousel (minimum). Your actual output will have
10–15 slides based on the content of the uploaded file.

{
  "slides": [
    {
      "type": "cover",
      "label": "Cover",
      "title": "7 **Productivity Hacks** That ==Actually Work==",
      "series": "Art Of UltraLearning",
      "hook": "Most productivity advice is **noise**. These 7 hacks are backed by science.",
      "tags": ["#Productivity", "#UltraLearning", "#DeepWork", "#Focus", "#BrainHacks"]
    },
    {
      "type": "intro",
      "label": "Why Productivity Fails",
      "tag": "Introduction",
      "method": "Cognitive Science + Behavioral Economics Research",
      "heading": "Why 90% of **Productivity** Advice Doesn't Work",
      "paragraphs": [
        "Most people are **busy**, not productive. There is a critical difference between motion and meaningful output that most self-help books never address.",
        "Neuroscience shows that productivity is not about __willpower__ — it's about environment design, biological rhythms, and understanding how your brain actually allocates energy.",
        "These 7 hacks are drawn from cognitive science, behavioral economics, and decades of elite performance research. They ==actually work.=="
      ],
      "blockquote": "Being busy is a form of laziness — lazy thinking and indiscriminate action.",
      "cite": "Tim Ferriss · The 4-Hour Workweek"
    },
    {
      "type": "ordered_list",
      "label": "The Morning Protocol",
      "tag": "Hack #01",
      "method": "Morning Optimization — Huberman Lab",
      "heading": "The **Perfect Morning** in 5 Steps",
      "steps": [
        { "num": "1", "title": "No phone for first 30 minutes", "desc": "Protect your dopamine baseline before the day corrupts it completely." },
        { "num": "2", "title": "10 min sunlight exposure",       "desc": "Sets circadian rhythm and primes your cortisol for peak morning alertness." },
        { "num": "3", "title": "Cold water on face or shower",   "desc": "Activates the dive reflex, drops heart rate, instantly boosts sharp focus." },
        { "num": "4", "title": "Write your top 3 priorities",    "desc": "Forces intentional direction before reactive mode and email hijack your attention." },
        { "num": "5", "title": "Deep work block starts now",     "desc": "Your first 90 minutes have your highest cognitive bandwidth — protect them." }
      ]
    },
    {
      "type": "summary",
      "label": "Complete Summary",
      "tag": "Complete Summary",
      "heading": "All **7 Productivity Hacks** at a Glance",
      "items": [
        { "num": "01", "title": "Morning Protocol",   "desc": "No phone, light, priorities" },
        { "num": "02", "title": "Deep Work Blocks",   "desc": "90-min no-distraction time"  },
        { "num": "03", "title": "Energy Management",  "desc": "Work with ultradian rhythms"  },
        { "num": "04", "title": "Single-Tasking",     "desc": "One task to completion first" },
        { "num": "05", "title": "Deadline Design",    "desc": "Parkinson's Law in reverse"   },
        { "num": "06", "title": "Environment Design", "desc": "Remove friction not willpower" },
        { "num": "07", "title": "Recovery Rituals",   "desc": "Rest is productive not lazy"   },
        { "num": "🔑", "title": "Save This Post",     "desc": "Come back daily", "highlight": true }
      ]
    },
    {
      "type": "cta",
      "label": "Follow CTA",
      "icon": "U",
      "heading": "Ready to **Upgrade** Your Productivity System?",
      "sub": "Every day we drop new science-backed hacks for focus, learning, and peak mental performance. Don't miss a single one.",
      "buttons": [
        { "style": "primary",   "icon": "💾", "text": "Save This Post — Come Back Daily" },
        { "style": "secondary", "icon": "👆", "text": "Follow @ArtOfUltraLearning" },
        { "style": "ghost",     "icon": "💬", "text": "Join WhatsApp Channel for Daily Drops" }
      ]
    }
  ]
}


---

## SECTION 7 — FINAL INSTRUCTION

Now read the uploaded file carefully.
Extract all meaningful content from it.
Map each major concept, section, or data point to the most appropriate
slide type using the decision guide in Section 3.
Write the complete JSON for the Art Of UltraLearning Instagram carousel.

Apply the tone, voice, and inline formatting rules from Section 2.
Respect the content density limits from Section 2C.
Verify every point in the quality checklist in Section 5.

OUTPUT ONLY THE RAW JSON OBJECT.
No explanation before it. No explanation after it.
No markdown code fences (no backticks).
Start with { and end with }.

# ═══════════════════════════════════════════════════════════
#  END OF PROMPT
# ═══════════════════════════════════════════════════════════

---

## QUICK REFERENCE CARD

### 15 Valid Slide Types

  cover          → always slide 1     · dark black bg · hook + title
  intro          → always slide 2     · dark black bg · paragraphs + blockquote
  ordered_list   → content slides     · white/light bg · numbered steps
  table          → content slides     · deep red bg    · before/after rows
  bar_graph      → content slides     · dark black bg  · horizontal % bars
  pie_chart      → content slides     · dark black bg  · donut + legend
  timeline       → content slides     · dark black bg  · vertical phases
  progress       → content slides     · dark black bg  · metric bars
  bullet_list    → content slides     · dark black bg  · tip cards
  quote          → content slides     · gold/yellow bg · big quote + stats
  icon_grid      → content slides     · dark black bg  · 2-col emoji cards
  checklist      → content slides     · dark black bg  · yes/no table
  numbered_cards → content slides     · dark black bg  · numbered bonus cards
  summary        → always 2nd-to-last · deep red bg    · recap grid
  cta            → always last        · dark black bg  · 3-button follow

### Inline Formatting

  **text**  → bold white      (key terms, 1–3 per paragraph)
  __text__  → italic gold     (concepts, highlighted phrases)
  ==text==  → bold gold       (punchline, once per slide max)

### Mandatory Summary Ending Item

  { "num": "🔑", "title": "Save This Post", "desc": "Come back daily", "highlight": true }

### Mandatory CTA Buttons (in this exact order)

  { "style": "primary",   "icon": "💾", "text": "Save This Post — Come Back Daily" }
  { "style": "secondary", "icon": "👆", "text": "Follow @ArtOfUltraLearning" }
  { "style": "ghost",     "icon": "💬", "text": "Join WhatsApp Channel for Daily Drops" }

---

Prompt Version: 1.0
Account: Art Of UltraLearning (@art_of_ultralearning)
Generator: ultralearning_carousel_gen.html
