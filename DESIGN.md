# DESIGN.md — Bajkamal Singh (Baaz) Portfolio

> **Inspection basis:** Live homepage at `https://bajkamalsingh.me/`, inspected 2026-09-30. Browser viewport was 1280 × 1100 CSS px. The requested 1440 px desktop target below is a normalized implementation target, not a claim that the live site was measured at 1440 px. Values are tagged `observed`, `derived`, or `recommended` so an implementation agent can tell source facts from practical defaults.

## 1. Design-system overview

The portfolio combines a **cinematic, scroll-driven narrative** with **DIY/editorial handwriting**, **brutalist square geometry**, a saturated cobalt-blue signature, cream paper, and dark ink. It deliberately mixes expressive display typography and photographic/artwork layers with compact, monospaced system labels and data-rich case studies. Keep the system intentionally irregular, but make navigation and content legible and predictable.

```yaml
metadata:
  site: "Bajkamal Singh (Baaz) — Structured Arts"
  url: "https://bajkamalsingh.me/"
  inspected_at: "2026-09-30"
  measured_viewport_css_px: { width: 1280, height: 1100 }
  target_desktop_css_px: { width: 1440, height: 900 }
  evidence_key:
    observed: "Directly measured in browser or explicitly present in source CSS/HTML."
    derived: "Calculated from source styles, breakpoint classes, or measured element geometry."
    recommended: "Normalized token or accessibility adjustment for new implementations."
  aesthetic: ["cinematic portfolio", "editorial collage", "brutalist UI", "handwritten annotation", "cobalt blue"]
```

## 2. Design tokens

### 2.1 Color palette

Core values are explicit CSS custom properties in the source. Secondary values are used by particular sections and should not be promoted to global brand colors without purpose.

```yaml
color:
  brand:
    cobalt: { value: "#012CEB", role: "primary brand, active nav indicator, blue feature panels, borders", evidence: observed }
    cobalt-focus: { value: "#0F35FF", role: "focus-visible ring in source", evidence: observed }
    cobalt-deep: { value: "#002FBE", role: "occasional deep-blue artwork/shading", evidence: observed }
  surface:
    paper: { value: "#F4EFE6", role: "primary warm-cream panel, nav, footer", evidence: observed }
    paper-dark: { value: "#E5DFC8", role: "warm paper shade", evidence: observed }
    paper-light: { value: "#ECE8E1", role: "light neutral in showcase / cursor labels", evidence: observed }
    paper-muted: { value: "#F0EDE6", role: "light HUD surface", evidence: observed }
    void: { value: "#01040A", role: "body and hero base", evidence: observed }
    void-panel: { value: "#010204", role: "dark about/contact panel", evidence: observed }
    black: { value: "#0A0A0A", role: "hard-edged ink, labels, border/shadow", evidence: observed }
    navy: { value: "#051024", role: "primary ink, text on paper, dark card", evidence: observed }
  text:
    ink: { value: "#051024", role: "primary text on light surfaces", evidence: observed }
    paper: { value: "#F4EFE6", role: "primary text on dark/blue surfaces", evidence: observed }
    black: { value: "#0B0B0B", role: "near-black on paper", evidence: observed }
    muted-on-dark: { value: "rgba(255,255,255,0.50)", role: "secondary social links", evidence: observed }
  border:
    grid-blue: { value: "#012CEB", width: "2px", role: "grid/section dividers", evidence: observed }
    ink: { value: "#051024", width: "2px", role: "nav and cards; 3px desktop on nav/cards", evidence: observed }
    ink-black: { value: "#0A0A0A", width: "2px", role: "header ribbon / showcase outlines", evidence: observed }
    subtle-on-dark: { value: "rgba(244,239,230,0.20)", width: "1px", role: "quiet dark-surface boundaries", evidence: observed }
  accents:
    signal-yellow: { value: "#F9CE34", role: "small station/attention details; local accent only", evidence: observed }
    signal-amber: { value: "#FFB000", role: "metro / micro-interaction accent; local accent only", evidence: observed }
    success-green: { value: "#8DE254", role: "rare inline highlighted phrase", evidence: observed }
    caution-red: { value: "#FF2A2A", role: "local caution/error graphic only", evidence: observed }
  contrast_pairs:
    paper_on_navy: { foreground: "#F4EFE6", background: "#051024", ratio: "16.58:1", evidence: derived }
    paper_on_void: { foreground: "#F4EFE6", background: "#010204", ratio: "18.12:1", evidence: derived }
    cobalt_on_paper: { foreground: "#012CEB", background: "#F4EFE6", ratio: "7.16:1", evidence: derived }
    white_on_cobalt: { foreground: "#FFFFFF", background: "#012CEB", ratio: "8.20:1", evidence: derived }
    cobalt_on_void: { foreground: "#012CEB", background: "#010204", ratio: "2.53:1", note: "Do not use as small text or a required boundary without another contrast cue.", evidence: derived }
```

### 2.2 Typography

```yaml
typography:
  font_families:
    body: { css: "Inter, Arial, sans-serif", role: "body copy, case study content, general UI", evidence: observed }
    hand_ui: { css: "Schoolbell, cursive", role: "handwritten labels, navigation, display/supporting copy, CTA", evidence: observed }
    logotype: { css: "'Dr Sugiyama', cursive", role: "hero Baaz wordmark", evidence: observed }
    hand_annotation: { css: "'Gloria Hallelujah', cursive", role: "small handwritten nav/identity labels", evidence: observed }
    metadata: { css: "'DM Mono', monospace", role: "footer legal links, machine-like labels, IDs", evidence: observed }
    optional_loaded_faces:
      - "Teko"
      - "Bebas Neue"
      - "DM Sans"
      - "Lilita One"
      - "Open Sauce One"
    optional_note: "These font faces are loaded by the homepage; use only for a specific artwork or local treatment when verified. Core roles above are supported by inspected computed styles."
  weights:
    body: { value: 600, source_computed: true, guidance: "Use 400–600 for long-form body text; reserve 700–900 for short labels and emphasis." }
    hand_ui: { value: 600, guidance: "Use 700 for small uppercase hand labels/buttons." }
    nav: { value: 800, evidence: observed }
    metadata: { value: 600, guidance: "Use 400–600; maintain readable contrast." }
  scale:
    micro: { size: "9px", line_height: "1.25", letter_spacing: "0.10em", role: "tiny uppercase captions; do not use for essential copy", evidence: observed }
    meta: { size: "10.56–13px", line_height: "1.3–1.5", letter_spacing: "0.10–0.15em", role: "HUD, mono/footer labels", evidence: observed }
    small: { size: "12–14px", line_height: "1.5", letter_spacing: "0.05–0.10em", role: "navigation, supporting labels", evidence: observed }
    body: { size: "16px", line_height: "1.55–1.7", letter_spacing: "0", role: "recommended long-form copy", evidence: recommended }
    body_measured: { size: "14.08px", line_height: "21.12px", role: "body computed in inspected 1280px browser", evidence: observed }
    body_large: { size: "18–22px", line_height: "1.4–1.6", role: "lead/about statement", evidence: recommended }
    heading_3: { size: "36–56px", line_height: "0.95–1.1", letter_spacing: "-0.03em", role: "section title or feature heading", evidence: derived }
    heading_2: { size: "clamp(56px, 10vw, 144px)", line_height: "0.85–1.0", letter_spacing: "-0.03em", role: "oversized editorial section title", evidence: derived }
    hero_script: { size: "376px", line_height: "1", letter_spacing: "-0.019em", role: "hero wordmark at 1280px viewport", evidence: observed }
    contact_cta: { size: "clamp(32px, 4.1vw, 60px)", line_height: "1", letter_spacing: "-0.025em", role: "oversized mail link", evidence: derived }
  defaults:
    heading_style: "Handwritten or display face for short expressive headings; never set long paragraphs in the script face."
    body_style: "Inter at 16px recommended for a fresh build, despite the live page's measured 14.08px body."
    casing: "Uppercase is used for short labels, sections, tags, and status text; sentence case for narrative copy."
```

### 2.3 Spacing, shape, shadows, motion

```yaml
spacing:
  unit: "4px"
  xs: "4px"
  sm: "8px"
  md: "16px"
  lg: "24px"
  xl: "32px"
  xxl: "48px"
  xxxl: "80px"
  section_y_desktop: "96px (recommended; live composition also uses viewport/sticky scenes)"
  section_x_desktop: "32–48px"
  section_x_mobile: "20–24px"
  note: "The live Tailwind/rem geometry resolves to 14.08px per rem in the inspected page. The scale here is normalized to a 4px authoring grid; preserve the visual rhythm rather than copying browser-rounded values literally."

radius:
  none: "0px"
  default: "0px"
  pill: "9999px"
  usage: "Square corners are the rule for nav, cards, panels, section borders, and CTA frames. Reserve fully rounded corners for the circular sound control and small circular indicators."

shadow:
  nav_mobile: "4px 4px 0 #051024"
  nav_desktop: "8px 8px 0 #051024"
  hard_offset: "4px 4px 0 #051024"
  card_blue: "14px 14px 0 rgba(1,44,235,0.9), 0 30px 60px -10px rgba(0,0,0,0.3), inset 1px 1px 0 rgba(255,255,255,0.8)"
  card_navy: "14px 14px 0 rgba(1,44,235,0.7), 0 30px 60px -10px rgba(0,0,0,0.8), inset 1px 1px 0 rgba(255,255,255,0.15)"
  button: "4px 4px 0 rgba(244,239,230,0.15)"
  principle: "Prefer crisp, hard-offset paper-cut shadows to soft generic elevation; use large diffuse shadow only for layered project cards."

motion:
  fast: { duration: "180ms", easing: "ease", use: "cursor labels and small opacity changes", evidence: observed }
  ui: { duration: "300ms", easing: "ease", use: "nav text, CTA hover, controls", evidence: observed }
  reveal: { duration: "900ms", easing: "cubic-bezier(0.16, 1, 0.3, 1)", use: "scroll text reveal and clip-path", evidence: observed }
  blur_reveal: { duration: "1000ms", easing: "cubic-bezier(0.16, 1, 0.3, 1)", use: "blur/scale into focus", evidence: observed }
  deck_spread: { duration: "1200ms", easing: "cubic-bezier(0.175, 0.885, 0.32, 1.275)", use: "stacked card fan-out", evidence: observed }
  transit: { duration: "1500ms", use: "train/carriage movement", evidence: observed }
  ticker: { duration: "continuous", animation: "linear translateX", use: "marquee/ticker", evidence: observed }
  decorative_shine: { duration: "15s", easing: "linear", use: "slow glass/reflection drift", evidence: observed }
  hover_float: { amplitude: "7px vertical", use: "subtle decorative float", evidence: observed }
  reduced_motion: "Honor prefers-reduced-motion: reduce; remove nonessential parallax, warp, auto-scroll, looping movement, and long transitions. The source collapses animations/transitions to 0.01ms and disables smooth scrolling."
```

## 3. Component specifications

### 3.1 Header, HUD, and navigation

- **Top ribbon / HUD:** Fixed to the top edge; desktop height is about **40–48px** (42px measured at 1280 px). A dark identity cell, warm-cream central rotating/scroll-context message, and a progress/status cell. Hairline-to-2px dark dividers; handwritten face; tiny live progress percentage. It may begin hidden during the entrance animation and become visible as the page progresses.
- **Main navigation:** Fixed horizontally centered near the bottom (`bottom: 32px` in the live utility classes); a compact six-item bar for **Home, Origin, Projects, Best Work, Visuals, Contact**. Cream background, square corners, 3px navy border and **8px × 8px** hard offset navy shadow on desktop. Measured at 1280 px as approximately **555 × 57px**. Padding 6px at desktop. A cobalt rectangular indicator slides between items; selected item text changes to cream. Link type is handwritten, bold, tracked; active state must not depend on color alone.
- **Entry state:** A full-screen introductory animation overlays the page. It includes the line “I intentionally make misalignment look intentional,” progress, click/drag exploration affordances, and a **Skip Animation** button. Keep the skip action immediately discoverable and make the experience usable without the animation.
- **Sound control:** Circular cream control with 2px ink border, hard shadow, fixed at lower-right. Approx. 56px measured on this viewport; source scales to 48px mobile / 64px desktop. Expose a descriptive accessible name and a clear muted/unmuted state.
- **Status labels:** Small monospaced or handwritten all-caps UI such as `SYS.TRACK_ACTIVE`, `SECTION 03`, `VOL.2026`; treat as decoration or supplementary orientation, not the only navigation cue.

### 3.2 Hero (`#hero`)

- Full-bleed **100vh** canvas, no outer page gutter; live section measured **1280 × 1100px**. Deep near-black base with saturated cobalt/blue-violet photographic/video field, silhouette imagery, glow, texture, and vignette. Provide a static image fallback.
- Central expressive **Baaz** script/logotype (Dr Sugiyama); measured font size **376px** in the 1280px viewport. Scale responsively with `clamp()` and prevent clipping on small screens.
- Supporting copy “Creative by night, more creative by midnight.” sits upper-right in handwritten type with a tiny clock/curve graphic. Career progression and location/student label are grouped on the left; scroll invitation centered near lower-middle.
- Keep hero composition asymmetrical: oversized wordmark is the anchor; compact facts orbit it. Avoid adding a conventional centered headline/subtitle/button stack.
- Interactive affordance: “Click to expand” / “Drag your cursor to explore” may control a visual exploration effect. Cursor-driven transforms must have keyboard/touch equivalents and must not block reading.

### 3.3 About / origin narrative (`#about`)

- Dark section with cobalt hairline/grid borders; **sticky 100vh viewport** driven by a long scroll runway (source spacer is approximately 1500vh in addition to sticky scene). The source section measured roughly **17,602px tall at 1280 × 1100** because it stages the scroll story; this is a narrative duration, not a content container height to copy blindly.
- Content sequence inside the scroll scene: creative philosophy quote → brand/logo/product references → “one yes” / 186M+ views impact → philosophy “Art with a purpose” → places worked/roles → proof-point/stat cards → open-book/origin timeline → personal origin text and image/Polaroid memory.
- Use large hand/display copy and small mono/handwritten labels; alternate dark, cobalt, cream, and image layers for pacing. Statistics should be set as large numerals with short explanatory labels.
- Make each scroll beat understandable when motion is disabled: stacked static sections in the same narrative order. Preserve text as selectable, semantic content rather than rasterized animation.

### 3.4 Project stack / experience (`#experience`)

- A **full-viewport cobalt section**, `min-height: 800px`, approximately **100vh**; live section measured **1280 × 1100px**. Header combines `PROJECTS`, “Sector 03 / Alpha”, live system/section readout, and a quick note pointing time-constrained visitors toward Best Work.
- Not a conventional multi-column card grid. The live site uses a **horizontal, overlapped accordion/deck of stacked case-study cards** (Grimbyte Technologies, Blue Tea, Dr. Water, Frost & Sullivan). The first visible card is about **1005px wide × 197px high** at the inspected viewport, centered with ~97px side margins. Cards are absolute/overlapping and spread apart on desktop scroll/interaction.
- Card surface variants alternate blue/cream/navy. Use **2px mobile / 3px desktop** sharp border; padding ~20px 16px mobile and ~28px 21px desktop (live computed desktop ~28px horizontal, ~21px vertical). Square corners. Hard 14px offset color shadow plus restrained deep blur and inset highlight.
- Collapsed state: organization, short descriptor, role, duration, and a few proof numbers. Expanded state: concise outcome-led case-study detail, supporting metric chips, and explicit close hint (“Click anywhere to close”). Make the full card keyboard operable; add an explicit button/expanded state instead of relying on click-anywhere alone.
- Narrow screens: replace overlapping/fanning stack with a single-column normal-flow accordion; never depend on hover to reveal essential copy.

### 3.5 Best Work / Delhi Metro case study (`#vending`)

- Immersive showcase; full viewport, source `min-height: 750px`, `max-height: 1100px`, `height: 100vh`. The source section was measured **1280 × 1100px** (max-height applied).
- Warm pale background (**#ECE8E1 / adjacent cream**), strong dark 2px boundary, high-contrast graphic/schematic station treatment. The anchor headline is bilingual — large Devanagari “दिल्ली मेट्रो में आपका स्वागत है” with English “Welcome to Delhi Metro.” Preserve language and script; use a Devanagari-capable font fallback.
- Primary “ENTER METRO” button starts an interactive transport/station case study. Provide keyboard arrow-key browsing, visible previous/next buttons, station and project names, concise narrative, and outcome metrics. Source instructions show a metro/train moving horizontally and station-themed project deep dives.
- CTA and station navigation must work by click/tap and keyboard; animate the train as a metaphor, not as the only way to know the active project.

### 3.6 Visuals / “Insomniac Work” gallery (`#gallery`)

- Cream background (`#F4EFE6`), cobalt **3px top divider**, long art-led section. At 1280px its measured section height was approximately **4403px**; this reflects a tall, multi-piece gallery, not a required fixed height.
- Includes a line of creative disciplines (brand design, social media, typography, poster design, colour grading, motion graphics, visual identity, content creation), large handwritten “insomniac Work” title, and “hover around to see the magic” invitation.
- Use an image-led editorial mosaic/stack; retain original work's aspect ratios where possible and use crisp square borders. The live page uses a custom hover cursor/label and animated card highlights. On touch, expose an explicit tap-to-preview / open state and do not hide image captions behind hover.

### 3.7 Contact (`#contact`)

- Dark near-black (`#010204`) section with a fine grid-top boundary, approximately **40vh minimum**. The source utility uses generous vertical padding (about 84px at observed root scale) and horizontal padding around 42px; desktop is a two-sided flex composition.
- Left: expressive handwritten “contact Me” title, short invitation, then prominent email CTA: **“→ say hi before overthinking it”**. Measured computed CTA type was about **52.8px** at 1280 px. Link opens a prefilled `mailto:`; retain that low-friction behavior.
- Right: compact Instagram, LinkedIn, and Mail links; translucent white secondary style that brightens on hover. Ensure visible focus, adequate hit area, and meaningful accessible names.

### 3.8 Footer (`#site-footer`)

- Warm paper surface, 3px navy top border, horizontal desktop layout with generous padding (source uses `px-8 md:px-12`, and about 42px computed padding at captured size). Responsive stack on small screens.
- Contains short sign-off, owner name/alias, copyright/year, and Privacy Policy / Terms of Use links. Legal links are DM Mono, small uppercase, letter-spaced, underlined; hover transitions to cobalt.

## 4. Layout system

```yaml
layout:
  authoring_grid: "4px normalized spacing unit"
  viewport:
    desktop_reference: "1440px wide"
    live_capture: "1280px wide"
  container:
    page_sections: "100vw; edge-to-edge color fields"
    project_card_max_width: "1035px (source responsive class); actual first card ~1005px at 1280 viewport"
    narrative_copy_max_width: "680–760px recommended"
    general_content_max_width: "1200px recommended; full-bleed artwork may exceed it"
  grid:
    columns: "12-column conceptual desktop grid; align narrative to 6–8 columns and supporting facts/art to remaining space"
    gutters: "24px desktop / 16px mobile (recommended)"
    outer_margin: "32–48px desktop / 20–24px mobile"
    actual_pattern: "Custom editorial compositions, sticky scenes, overlapping project deck, and wide image panels rather than a consistent card grid."
  sections:
    hero: "100svh; full bleed"
    about: "sticky 100svh scene + scroll-driven narrative runway; use normal stacked flow for reduced motion"
    experience: "100svh; min-height 800px in source"
    vending: "100vh; min-height 750px; max-height 1100px in source"
    gallery: "content-driven tall image section"
    contact: "min-height about 40vh; 96px vertical padding recommended"
  breakpoints:
    mobile: { max: "639px", status: "derived from default Tailwind breakpoints", guidance: "single column, reduce display type, reveal all controls, replace hover and deck interactions with tap/keyboard" }
    small_tablet: { min: "640px", max: "767px", status: "derived", guidance: "comfortable side padding; avoid multi-layer overlap" }
    tablet: { min: "768px", max: "1023px", status: "observed source md breakpoint", guidance: "activate desktop card/navigation treatments selectively; keep touch targets" }
    desktop: { min: "1024px", max: "1279px", status: "derived from Tailwind defaults", guidance: "full editorial composition with reduced oversize type as needed" }
    wide_desktop: { min: "1280px", status: "observed source xl breakpoint", guidance: "full large-scale type and broad atmospheric layouts" }
  responsive_notes:
    - "Use 100svh/dvh fallbacks for full-screen scenes on mobile browsers."
    - "Navigation must fit or wrap/scroll intentionally; never crop a destination."
    - "Keep hero logo within 90vw and use clamp() for display sizes."
    - "Ensure the project accordion remains readable without overlapping cards below 768px."
```

## 5. Accessibility guidelines

- **Contrast:** target WCAG 2.2 AA: at least **4.5:1** for normal text, **3:1** for large text and meaningful non-text graphics. The observed core pairings pass: cream/navy 16.58:1; cream/near-black 18.12:1; cobalt/cream 7.16:1. Do not use cobalt alone against the dark void for essential small text (observed contrast is only 2.53:1). Semi-transparent muted links must be checked against their actual surface.
- **Keyboard:** use semantic `<nav>`, headings in order, real links/buttons, visible focus and no keyboard traps. Source styles specify a 2px `focus-visible` ring in `#0F35FF`; pair with a contrasting offset or outline on blue backgrounds. Provide keyboard access to the interactive hero, accordion, metro projects, and any gallery preview.
- **Touch:** aim for **44 × 44px minimum** interactive hit areas (WCAG 2.2 target-size minimum where applicable); use 48px where practical. The live sound toggle is about 56px desktop. Some live nav links are shorter; enlarge the mobile target area.
- **Motion:** respect `prefers-reduced-motion`; disable autoplay-like transitions, parallax, warping, cursor-following, and looping ambient motion. Do not force smooth scrolling. Keep the skip-intro action visible and preserve native scrolling as an accessible fallback.
- **Pointer/touch parity:** the live site hides the cursor on fine pointers and uses hover labels. A custom cursor must never replace the system pointer for critical controls and must have touch and keyboard equivalents. Never make “hover to see” the only way to obtain content.
- **Media:** provide useful alt text for portfolio work, mark purely decorative texture/silhouette imagery as decorative, offer poster/static fallbacks for video, and avoid flashing. If sound is present, default to muted and expose the toggle's state.
- **Content:** preserve English and Hindi/Devanagari copy, declare correct document language where possible, and choose fonts with robust script fallbacks. Maintain selectable text, logical focus order, and sufficient line spacing.

## 6. Design guardrails

### Do

- Lead with the electric cobalt / warm-paper / deep-ink palette and maintain clear contrast between each block.
- Use asymmetry and generous negative space to create a personal, handmade, cinematic feel.
- Pair oversized script/display moments with neutral, readable sans-serif body copy and small mono system labels.
- Let case studies show a role, context, action, and measurable outcome; make statistics legible and contextual.
- Keep geometry square and shadows crisp; use one strong outline or offset shadow rather than generic rounded-card UI.
- Use scroll and hover motion as progressive enhancement; content and navigation must remain complete if animation fails.
- Preserve human, playful microcopy and direct-to-email contact, while keeping labels explicit.
- Keep image-led work dominant in the gallery and crop consistently within each individual project grouping.

### Don’t

- Don’t normalize the page into a generic SaaS dashboard, standard rounded card grid, or conventional centered corporate landing page.
- Don’t add gradients, accent colors, rounded corners, or shadows indiscriminately; keep secondary colors confined to their local artwork/feature.
- Don’t set long paragraphs in handwritten or ultra-condensed display faces; don’t use 9–11px for essential text.
- Don’t require hover, drag, sound, a specific pointer, or a successful animation for core content or navigation.
- Don’t use cobalt on near-black as small text/border without a contrast check or companion cue.
- Don’t let decorative metrics/status text compete with the page title or obscure case-study content.
- Don’t crop Devanagari or force English-only typography in the metro case study.

### Visual hierarchy principles

1. **One dominant visual anchor per scene:** hero wordmark; about-story statement; project deck; bilingual metro title; artwork; contact CTA.
2. **Scale contrast:** large expressive display title → concise lead → readable narrative → compact metadata.
3. **Color as structure:** dark/cream/cobalt changes mark narrative chapters, active state, and importance—not decoration alone.
4. **Evidence follows story:** show context and role before metrics; give each metric a short descriptor.
5. **Motion supports narrative:** scene transition or reveal should guide attention, not repeatedly compete with reading.

### Content guidelines

- Maintain the voice: first-person, candid, ambitious, playful, specific; keep jokes short and secondary to the work.
- Use short headings and intentional line breaks; avoid paragraph-wide uppercase.
- Keep project descriptions concrete and outcome-led. Include timeframe and metric definitions when known; do not imply unsupported attribution.
- Write image alt text about the work's content/purpose, not “image of portfolio.”
- Use labels such as “View project details” and “Next station” in accessible names, even when visual microcopy is playful.

## 7. Homepage page structure and order

1. **Intro / animation overlay** — establishes the “intentional misalignment” premise; offers skip and cursor/tap exploration. May transition directly into hero.
2. **Hero (`#hero`)** — identity, creative positioning, career progression, location, scroll cue; cinematic blue-and-silhouette treatment.
3. **Persistent HUD and navigation** — progress/context ribbon, current section status, sound control, six section anchors. These are persistent interface layers rather than separate story chapters.
4. **About / philosophy and proof (`#about`)** — sticky scroll-driven “book” sequence; creative quote, visual references, impact proof (including 186M+ views), philosophy, work history, selected metrics, and personal timeline.
5. **Origin story (inside `#about`)** — early creative work, sneaker/freelance motivation, evolution from making to strategy, early-phase image/memory and milestone.
6. **Projects / experience stack (`#experience`)** — intro note and interactive accordion/deck with Grimbyte Technologies, Blue Tea, Dr. Water, and Frost & Sullivan case studies.
7. **Best Work / Delhi Metro (`#vending`)** — immersive “Welcome to Delhi Metro” bilingual showcase, station metaphor, project browsing, deep dives, and business outcomes.
8. **Visuals / Insomniac Work (`#gallery`)** — image-first showcase of design disciplines and selected creative output; hover/tap exploration.
9. **Contact (`#contact`)** — short invitation and prominent mailto CTA; Instagram, LinkedIn, Mail pathways.
10. **Footer (`#site-footer`)** — sign-off, author identity, copyright, privacy, terms.

**Intended narrative arc:** *identity → philosophy and proof → origin → experience → flagship case study → visual craft → direct contact.*
