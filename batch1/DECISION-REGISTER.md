# InspiredTax · Design Decision Register (master list)

**Version:** R1 · 2026-11-26 · maintained by Antigravity. Replace this file in Gemini whenever a new version is published.
**Purpose:** the single list of everything the owner and the AI partners will decide, in which batch, and what's already settled. Any AI helping the owner MUST check this list before answering "should we decide X?".

---

## 1. Rules for the AI partner (Gemini or Claude): read first

### 1.1 When the owner mentions anything (a button, a colour, a behaviour…)
1. **Search this register** by keyword and by element (for example "button press" → 4.4, "glow" → 1.6).
2. **Found and `Open`:** say *"It's on the list: item 4.4, in Batch 4. Don't worry about it now."* If the owner states a preference, record it as a **Leaning** (for example "Leaning 4.4: wants a firm, satisfying press"), and carry it into the Ruling Card. Don't decide it early unless the owner insists.
3. **Found and `Ruled`:** state the ruling. Changing it is a **Change Request (CR)**: note what and why. Rulings are frozen to stop churn, so a CR is fine but must be deliberate.
4. **Found and `Locked`:** explain it's a correctness, privacy or accessibility fix, not taste. Its *appearance* can be restyled, but its *behaviour* stays.
5. **Not found:** say so plainly, then either:
   - **It fits a future batch:** add it as a new item (for example `4.N1 · Long-press on rows`) with the owner's words, and park it; or
   - **It's urgent, cross-cutting, or the owner wants it now:** run a mini-decision (2–3 options, a recommendation, one bold idea) and log it as `ADD-01`, `ADD-02`… in the Ruling Card.
6. **Product ideas** (features rather than design, for example "scan my IRP5"): put them in the **Ideas Parking Lot** (section 6), not in a batch.

### 1.2 How a batch session runs
- One question at a time, in plain language; short replies (the owner is on a phone).
- **Core questions** are discussed. **Quick confirms** list a recommended default: the owner says "fine" or changes it.
- Always offer the recommendation (★) **and** the bold idea (⚡). The owner has asked for innovative, left-field thinking; don't just defend the old design.
- Guardrails that can never be broken: text contrast ≥ 4.5:1 in Dark and Light; colour is never the only signal; tap targets ≥ 48 px; works at 360 px wide and at 200% text size; green = refund, red = "You owe SARS", amber = warning/delete; tax figures come from the engine (design never changes the maths); offline-first; no email, date of birth or tax reference stored.
- Finish with the **Ruling Card** (section 5).

### 1.3 Status legend
`Open` = to decide · `Ruled` = decided (frozen) · `Locked` = a correctness fix, not up for taste · `Confirm` = decided earlier, but the owner should re-confirm in the batch named

---

## 2. The batch sequence (dependency order)

| Batch | Topic | Why this position |
|---|---|---|
| 0 | Engineering baseline (no taste decisions) | Puts all the fixes into the main app before any restyle |
| 1 | Personality, colour, surfaces and glow | Affects every element |
| 2 | Type, icons and numbers | Affects every element, after colour |
| 3 | Shell and navigation | Sets the space every page gets |
| 4 | Selection, controls and tap feedback | Components inside pages |
| 5 | Containers, feedback and motion | Cards, sheets, snackbars, transitions |
| 6 | Data entry and saving | Keypad, fields, save and undo |
| 7 | Heroes and page compositions | Assembles 1–6 into pages |
| 8 | Flows, onboarding and page order | Assembles pages into journeys |

---

## 3. The register

★ = Antigravity's current recommendation · ⚡ = bold or left-field option · *Now* = the latest test build (v4-iter3) unless stated

### Batch 0: Engineering baseline (owner confirms only)

| ID | Item | Status | Notes |
|---|---|---|---|
| 0.1 | Land all Tier 0 and Tier 1 fixes from the test branch into the main app | Open (owner merges) | No design input; about 35 fixes, 9 of them serious |
| 0.2 | PIN length 4–8 digits and auto-lock after 5 idle minutes | Confirm | Added in Phase 1; the owner never formally ruled on it |
| 0.3 | Retire C7 ("Undo after the estimate changed the year") | Open | The year switch was a bug, so the rule is moot |
| 0.4 | Phone test of the own keypad (TalkBack, paste, hardware keyboard) | Open | Risk known since Round 2 |
| 0.5 | CLEAN-1 (no migrations) ends once v8.37 reaches anyone | Note | Later design changes to stored data will then need migrations |
| 0.L | Every Tier 0/1 fix in the audit's preservation ledger | Locked | Behaviour stays; look may change |

### Batch 1: Personality, colour, surfaces and glow

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 1.0 | **North Star**: 3 words for how the app should feel | Open, core | — | ★ "Calm · Precise · Quick" · "Warm · Clear · Encouraging" · ⚡ "Sharp · Confident · Effortless" |
| 1.1 | Surfaces: how cards sit on the background | Open, core | Slate | A Glass (8.36.1) · B/C Slate · ★ D Glass · ⚡ E Mono solid (crisp ink cards, no transparency) |
| 1.2 | Area colours (Income / Deductions / Tax / Balances) | Open, core | Fjord | A Rainbow · B Jewel · ★ C/D Fjord · ⚡ E Monochrome (areas told apart by icon and label only; colour is saved for meaning) |
| 1.3 | Green/red/amber used only for money and warnings | Open, core | Mostly | ★ Yes |
| 1.4 | "Saved" tick colour | Open, core | Second green | ★ Brand accent + tick · keep second green |
| 1.5 | Light-mode background | Open, core | Indigo tint | ★ Neutral cool grey · indigo · ⚡ warm paper white |
| 1.6 | Glow | Open, core | Background glow | ★ Background only, subtle · none · on cards too |
| 1.7 | Brand accent hue and strength | Quick confirm | Pale cyan `#67E8F9` | ★ 8.36.1 bright cyan `#1ADDE3` / light `#097C82` |
| 1.8 | Depth model: what separates layers | Quick confirm | Borders + shadows | ★ Hairline borders + tonal steps, almost no shadows · ⚡ no borders, tonal steps only |
| 1.9 | Corner-radius family | Quick confirm | Mixed | ★ Cards 16 · buttons 14 · chips full pill · sheets 24 · ⚡ tighter 10/8 for a sharper "pro tool" look |
| 1.10 | Theme on first launch | Confirm (C6) | Follows phone | ★ Follow phone setting · ⚡ add a true-black OLED option |
| 1.11 | Chart colours (donuts, bars) | Quick confirm | Area hues | ★ Shades of each area hue · ⚡ monochrome ramps with only the selected slice in colour |

### Batch 2: Type, icons and numbers

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 2.1 | Font pairing | Open | Inter + Space Grotesk | ★ keep · single family (Inter only) · ⚡ Inter for text + **JetBrains Mono (already in the app) for every amount**, for a crisp "ledger" feel |
| 2.2 | Type scale (hero, title, body, caption) | Open | Many sizes | ★ 6 fixed sizes only; 12 px floor (Locked) |
| 2.3 | Headings tinted by area (II.c) | Confirm | Tinted | ★ Neutral headings; tint only a small eyebrow or accent line · keep II.c |
| 2.4 | How amounts look (tabular digits, cents, size steps) | Open | Mixed | ★ Tabular digits everywhere, cents only on statements · ⚡ hero amounts huge and thin, as in banking apps |
| 2.5 | Money words: "Refund due" / "You owe SARS", never signed | Ruled (A4) | — | — |
| 2.6 | "R 48 000" format (space separator) | Ruled (A7) | — | — |
| 2.7 | Empty or zero amounts | Confirm | "R —" | ★ keep "R —" · "Not added yet" text |
| 2.8 | Icon style (weight, fill on active, size) | Open | Outline 300, fill on select | ★ Outline at rest, filled when active · ⚡ duotone |
| 2.9 | Icon chip shape behind icons | Open | Rounded square + lip | ★ rounded square, no lip · circle · ⚡ no chip (bare icon) |
| 2.10 | Labels and eyebrows: UPPERCASE or Sentence case | Open | Mixed | ★ Sentence case everywhere; uppercase only for tiny eyebrows |
| 2.11 | Voice of microcopy | Open | Mixed | ★ Plain, warm, short · ⚡ ultra-terse "pro" voice |
| 2.12 | Large text / Easy View reflow | Locked (REFLOW-1) | — | — |

### Batch 3: Shell and navigation

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 3.1 | Top app bar layout | Open | 56 px bar | ★ Large title that shrinks into the bar on scroll · compact always · ⚡ bar disappears on scroll down, returns on scroll up |
| 3.2 | Sticky chrome budget (most screen kept for content) | Open | 138 px top | ★ Rule: ≤ 120 px top + nav at 360×740 |
| 3.3 | Sub-tabs inside a section (e.g. Income › Salary / Rental) | Open | One scrolling row | ★ one scrolling row · no sub-tabs (overview rows open detail) · ⚡ swipe left/right between sub-pages, with a small dot indicator |
| 3.4 | Sub-tabs on scroll | Open | Scroll away | ★ scroll away, come back on a flick up |
| 3.5 | Tax-year control (currently 2 controls that do different things) | Open | Badge + bar | ★ ONE control: tap → sheet showing the year, Quick Tax Facts and "Change year" |
| 3.6 | Bottom nav style (active indicator, icons, labels) | Open | Colour only | ★ Pill behind the active icon (Material 3) · underline · ⚡ floating rounded nav bar |
| 3.7 | Live outcome ("impact") bar | Open | Bar above nav | ★ only while editing · always · ⚡ a floating "answer pill" that morphs as you type and opens the statement when tapped |
| 3.8 | Page help ⓘ placement | Confirm (B13) | App bar | ★ keep |
| 3.9 | More page grouping and order | Open | Grouped list | ★ keep groups, reorder by use · ⚡ "Control centre" grid of tiles |
| 3.10 | Back behaviour (Android back, swipe-back) | Locked behaviour (backAction fix) / Open look | — | — |
| 3.11 | Privacy: hide amounts quickly | Open (new) | — | ⚡ an eye toggle in the bar, or flip the phone face-down, to blur every amount · none |
| 3.12 | Backup/offline status indicator | Open | In More | ★ small status dot on More only when at risk |
| 3.13 | Five nav destinations and their order | Ruled (MORE-1) | — | — |

### Batch 4: Selection, controls and tap feedback

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 4.1 | Selectable row layout (icon, text, control) | Open | Icon chip + text | ★ icon left, text, control right · ⚡ big tappable cards in a 2-column grid for short lists |
| 4.2 | **Selected-state cue** | Open, core | 3.b: icon fills in, no tick | visible tick box · 3.b · ★ row fills with a light accent tint + a bold tick (readable at a glance, passes accessibility) · ⚡ the whole row inverts (solid accent, dark text) |
| 4.3 | Rest (unselected) state | Open | — | ★ plain row, hairline divider |
| 4.4 | **Pressed / tap feedback** (all buttons and rows) | Open, core | Ripple + lip bounce | ripple · ★ quick press-in (scale 0.97, 90 ms) + haptic tick · lip bounce |
| 4.5 | Disabled state | Open | Mixed | ★ 40% opacity + "why" hint when tapped |
| 4.6 | Focus ring (keyboard / TalkBack) | Open | One ring | ★ 2 px accent ring, offset 2 px |
| 4.7 | Single choice vs multiple choice: visually different | Open | Same look | ★ radio dot for single, tick for multiple |
| 4.8 | Yes/No questions | Confirm (blank = No) | Tick box | ★ tick · segmented Yes/No · switch |
| 4.9 | Switches | Open | Mixed | ★ Material 3 switch in the accent colour |
| 4.10 | Button hierarchy (primary / tonal / outline / text) | Open | 3 kinds | ★ max ONE primary per screen; primary full-width at the bottom of flows |
| 4.11 | Destructive buttons | Ruled (C4 amber) | — | Restyle only |
| 4.12 | Chips and pills (status, filters, still-to-add) | Open | Mixed | ★ one chip style, three tones |
| 4.13 | ⓘ info buttons behaviour | Open | Opens sheet | ★ open a bottom sheet |
| 4.14 | Haptics vocabulary | Open (new) | None | ⚡ ★ light tick on select, double tick on save, firm on delete, off-switch in Display |
| 4.15 | Long-press on rows | Open (new) | — | ★ none (⋮ menu exists) · ⚡ long-press = quick edit |

### Batch 5: Containers, feedback and motion

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 5.1 | Card style (padding, border, radius from 1.9) | Open | Mixed | ★ one card style + one "hero" variant |
| 5.2 | Spacing scale | Open | Mixed | ★ 4/8 px grid, 16 px page margins |
| 5.3 | Expandable/collapsible cards: look, chevron, default, memory | Open, core | Mixed | ★ chevron right, rotates; closed by default; remembers state · ⚡ "peek" (show 2 lines, tap to expand) |
| 5.4 | List rows (64 px), row actions (⋮ vs swipe) | Confirm (A15) | ⋮ + swipe | ★ keep |
| 5.5 | How capture forms open | Open, core | Modals + pages | ★ bottom sheets for short forms, full page for long ones · ⚡ everything in rising sheets, never a page jump |
| 5.6 | Confirm dialogs | Ruled (A9 rule) / Open look | — | ★ centred, amber destructive button on the right |
| 5.7 | Snackbars and toasts (place, duration, Undo) | Open | Bottom | ★ above the nav, 5 s, Undo on the right |
| 5.8 | Empty states | Open | Text + Add | ★ one line + Add button · ⚡ Kat mascot illustrations |
| 5.9 | Loading and skeletons | Open | — | ★ ghost lines that fill in |
| 5.10 | Page transitions | Confirm (DEL-03) | Slide + fade 220 ms + ambient glow | ★ ⚡ "snappy budget": all motion ≤ 180 ms, no decorative motion |
| 5.11 | Row expands into its page (container transform) | Confirm (C2) | 240 ms | ★ keep, faster |
| 5.12 | Count-ups on figures | Confirm (limited) | 320 ms on action | ★ only when your edit changes the figure |
| 5.13 | Celebration moments (complete return, refund) | Open | None (D8) | ★ a small check burst on completion · ⚡ the hero number "lands" with one haptic |
| 5.14 | Kat mascot's role | Open | Reward row | ★ reward and empty states only · remove |
| 5.15 | In-page section headers and dividers | Open | Mixed | ★ small label + space, no lines |

### Batch 6: Data entry and saving

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 6.1 | Number keypad look and layout (000, ⌫, Clear, Done, Prev/Next) | Open, core | App keypad | ★ phone-dialler style, large keys, Done in accent |
| 6.2 | Own keypad vs phone keyboard for amounts | Ruled (D5 B), pending 0.4 phone test | — | — |
| 6.3 | Active field highlight while typing | Open | Highlight + label visible | ★ accent outline + label stays visible above the pad |
| 6.4 | Showing the tax effect while typing | Open | Impact bar | ★ inline "+R 1 240 refund" under the field · ⚡ the answer pill (3.7) animates |
| 6.5 | Save model (Done saves, outside tap saves, Keep/Discard) | Ruled (S1, A8) | — | Look only |
| 6.6 | Saved confirmation | Open | Tick (see 1.4) | ★ tick in the field + haptic, no toast |
| 6.7 | Undo/Redo affordance | Open | Snackbar | ★ snackbar Undo; Redo in the ⋮ menu |
| 6.8 | Validation and errors | Open | Red text | ★ inline under the field, error colour + icon, plain words |
| 6.9 | Date entry | Ruled (D2: Day/Month/Year) | — | Look only |
| 6.10 | Steppers (e.g. medical members) | Open | Stepper | ★ − / + buttons at 48 px |
| 6.11 | Text input bar (Prev/Next over the phone keyboard) | Open | IME bar | ★ keep, compact |
| 6.12 | Field labels | Open | Above | ★ label above, hint below · floating labels |
| 6.13 | Example/placeholder text | Open | Mixed | ★ "e.g. R 25 000" grey hint |

### Batch 7: Heroes and page compositions

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 7.0 | Rule: one hero figure per screen (G1) | Confirm | Partly | ★ adopt as a hard rule |
| 7.1 | Dashboard composition | Open, core | Comp C (quick row → ring → checklist → reward → tiles → return line) | A · B statement-first · C · ⚡ ★ **"One answer, one next step"**: the giant refund/owe figure, a progress line, ONE "Next: add medical aid" button, everything else below the fold |
| 7.2 | Dashboard hero form | Open | Progress ring | ring · statement · ⚡ progress line under the number |
| 7.3 | `.quick` 3-tile row above the hero | Confirm (OD-4) | Kept for code reasons | ★ remove or move below; fix the code anchor instead |
| 7.4 | Reward strip | Open | Row | ★ row under the hero |
| 7.5 | Next-step checklist | Open | List | ★ show 1 next step + "3 more" |
| 7.6 | Income/Deductions overview | Confirm (UXR2-5 donut) | Donut + legend + total | ★ keep · ⚡ statement list with inline bars |
| 7.7 | Tax Return page (currently 5 versions of the answer) | Open, core | 5 blocks | ★ one answer + one statement (waterfall), the rest collapsed |
| 7.8 | Provisional page | Confirm (B6/D8) | IRP6 hero + timeline | ★ keep, trim duplicate cards (currently 7) |
| 7.9 | Projection page | Confirm (B7/D9) | Bar chart | ★ keep |
| 7.10 | Optimise page | Open | Hero + list | ★ biggest saving first |
| 7.11 | Profile page (4 sections) | Confirm (D10) | — | — |
| 7.12 | Charts style (donut thickness, labels, legends) | Open | — | ★ thin donut, centre total, tappable legend |
| 7.13 | Statement / waterfall style | Open | Waterfall | ★ ledger lines with right-aligned tabular amounts |
| 7.14 | Goal-lens effect on Dashboard | Confirm (LENS-1) | Reorders | ★ keep |
| 7.15 | Premium/paywall presentation | Confirm (B1, B3, D11) | — | Look only |
| 7.16 | Backup page and risk nudge | Confirm (B4/B5) | — | Look only |

### Batch 8: Flows, onboarding and page order

| ID | Item | Status | Now | Options |
|---|---|---|---|---|
| 8.1 | Welcome screen | Open, core | Compact (34 px logo) | v4 compact · `onboarding-redesign-v2` (8.36.1 style) · ⚡ "number first": the welcome screen asks your salary and shows an instant rough refund before anything else |
| 8.2 | Onboarding structure | Open, core | 4 steps | ★ 4 steps · ⚡ one question per screen, with the estimate building live at the top as you answer |
| 8.3 | Question style (tick what applies, blank = No) | Ruled (ONBOARD-1) | — | + a "None of these" row? (Open) |
| 8.4 | Rough-figures step | Ruled (D7) | — | Look only |
| 8.5 | First-estimate reveal | Open | Statement | ★ number lands + "here's how" statement |
| 8.6 | PIN timing (after answers) | Ruled (A13 B) | — | Look only |
| 8.7 | Skip path | Ruled (D9 C) | — | — |
| 8.8 | Residency gate | Locked behaviour (fixed) / Open copy | — | — |
| 8.9 | Page order inside each tab | Open | — | ★ order by how often used |
| 8.10 | Year-end close-out and submitted years | Ruled (B9a/B9b) | — | Look only |
| 8.11 | Navigation depth | Open | Up to 3 levels | ★ max 2 levels below a tab |
| 8.12 | Fate of the `onboarding-redesign-v2` mockup | Open | On its own branch | Decided by 8.1/8.2 |

---

## 4. Cross-cutting rules (adopted as batches rule them)
G1 one hero per screen · G2 every figure opens to its source · G3 effect shown while typing · G4 statements read as ledgers · no raw colour values outside tokens · one component per pattern (one row, one card, one chip) · motion budget (from 5.10) · chrome budget (from 3.2).

## 5. Ruling Card (the AI fills this in at the end of each session)

```text
RULING CARD · Batch __ · Register version R__
Rulings:        <ID>: <choice> (one line each)
Leanings:       <ID>: <owner preference noted for a later batch>
New items:      <ID or ADD-##>: <what> → <batch or decided now: choice>
Change requests:<ID>: <from> → <to>, because …
Parking lot:    <product ideas>
Confidence:     sure / fairly sure / try it and see
```

## 6. Ideas Parking Lot (features, not design: not decided in batches)
- Photo-scan an IRP5 to fill the certificate (offline text recognition)
- Provisional-tax reminders before the August and February deadlines
- Home-screen widget showing the refund/owe figure
- Share a one-page "my return summary" PDF with an accountant
