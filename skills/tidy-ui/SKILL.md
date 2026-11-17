---
name: tidy-ui
description: Brings one app screen up to a clean, honest minimum, for people who aren't designers or don't have time to be. Checks and fixes spacing rhythm, alignment and optical alignment, hierarchy, sizing, font choice and settings, contrast, AI-default colour palettes, corner radius, depth, consistency, and light and dark mode, on iOS, Android or the web. Fixes by default, then reports every change with its design term. Use when a screen "looks off", "looks amateur", "looks AI generated", or "needs a clean-up", or before a design review or a release. Not for redesigns, new features, copy or motion.
---

# tidy-ui

Brings one screen up to a clean, honest minimum. It's a floor, not a redesign.

Made for The Weekend Project (https://theweekendproject.club), and free for everyone. It pairs with the design-vocabulary skill: that one names what's wrong, this one fixes it. For motion, use Emil Kowalski's skills (https://aiforui.dev).

## What it does

- Checks one screen against 12 basics, in an order that matters: structure first, then type, then colour, then detail
- Fixes what fails with the smallest change that works, and pulls stray values into a few tokens so the fixes stick
- Spots the default AI looks (cream and terracotta, indigo and slate, the unstyled component kit), swaps them, and tells you
- Recommends a good free font when the screen needs one, with the settings that make it look considered
- Reports every change in a short table, using the design word for it, so you learn as it fixes

## When to use it

- A screen works, and still looks off, amateur, or generated
- Before you send a screen for review (lesson 3.1 of The Weekend Project), so the review is about the idea, not the basics
- As a last pass before a release

## Example prompts

- /tidy-ui the home screen
- /tidy-ui SettingsView.swift
- /tidy-ui audit the pricing page (lists problems, changes nothing)
- /tidy-ui the profile screen, keep my colours

## Ground rules

1. **A floor, not a redesign.** Never add features, screens, sections or copy. Never move things around beyond what a fix needs. Never touch animation.
2. **One screen at a time.** If asked for the whole app, start with the screen people use most, then offer the next.
3. **Adapt first.** If the project already has a clear system (design tokens, a theme, a spacing or type scale used in most places), fix against that system. Only bring in the presets below when the values are scattered with no system behind them.
4. **A stated brand wins.** Read `context.md`, `voiceandtone.md`, a design tokens file, or a brand note if the project has one. Colours and fonts named there stay; only their contrast and settings get fixed.
5. **Work out the platform** from the code (SwiftUI or UIKit, Jetpack Compose or Android views, HTML/CSS, React, Tailwind, Flutter) and use that platform's own conventions. Don't bring web habits to iPhone, or iPhone habits to Android.
6. **Say what you changed, and why.** No silent changes. Anything opinionated (colours, fonts) is announced, with how to undo it.

## How to run

1. **Read** the screen's code, and its screenshot if given. Note the platform, the existing tokens, and any brand or voice file.
2. **Check** the 12 areas below, in order. For each, note pass or fail with the evidence (the file, the value).
3. **Fix** what failed, with the smallest change. Prefer changing a token over changing 20 call sites. Don't fix what passed.
4. **Report** with the template at the end: a table of changes, the AI-default note if any, what you left alone, and the next step.
5. **End with:** "Check it on your phone. The simulator and the preview can lie." 

### Options

- `audit`: run the checks and report, change nothing.
- `keep my colours`: skip check 8 and keep the palette. Still fix contrast (check 7).
- `keep my fonts`: skip font recommendations. Still fix font settings (check 6).

## Platforms

| | iOS | Android | Web |
|---|---|---|---|
| Units | pt | dp, and sp for text | px or rem |
| Interface font | SF Pro (the system font) | Roboto or the device's system font | A chosen sans, see Fonts |
| Type scale | Apple's text styles, with Dynamic Type | Material 3 type scale | The web scale below |
| Smallest text | 11 pt (Caption 2), body 17 pt | 11 sp (Label Small), body 14 to 16 sp | 12 px, body 16 px |
| Touch target | 44 × 44 pt | 48 × 48 dp | 44 × 44 px |
| Corners | Continuous corners, concentric when nested | Material 3 shape scale | One radius scale, concentric when nested |
| Colour | Semantic colours (label, secondaryLabel, systemBackground) | Material colour roles (primary, onSurface, surfaceContainer) | CSS custom properties, with light and dark values |
| Icons | SF Symbols, weight matched to the text | Material Symbols, one style | One icon set, one stroke weight |

---

## The 12 checks

### 1. Spacing rhythm
- Look for: one-off values (13, 19, 22), uneven gaps between siblings, the same space inside a group as between groups.
- Fix: snap every value to the scale. Space between groups is bigger than space inside them, usually double.
- Preset scale: 4, 8, 12, 16, 24, 32, 48, 64 (pt, dp or px).
- Design words: spacing scale, gap, proximity, whitespace.

### 2. Alignment
- Look for: text and images starting at different edges, content not lining up with the screen margins, icons sitting off centre in their circles or buttons.
- Fix: one shared leading edge per column. Match the platform's margins (iOS layout margins, 16 dp on Android, a fixed page padding on the web). Nudge play triangles, arrows and lone icons for optical alignment, usually 1 to 2 pt.
- Design words: alignment, optical alignment, layout margins, baseline.

### 3. Hierarchy
- Look for: everything the same size and weight, two things competing to be read first, more than three levels of text.
- Fix: one clear first thing per screen, set by size first, then weight, then colour. Three levels at most: primary, secondary, tertiary. Secondary text uses a secondary colour, not a smaller grey that fails contrast.
- Design words: hierarchy, visual weight.

### 4. Sizing
- Look for: text below the platform's minimum, tap targets under the minimum, icons a different size from the text beside them, a primary button smaller than a secondary one.
- Fix: raise text to the minimum. Grow the tap area (the hit target), not the icon. Size icons to the text: about the text's cap height to its full line height.
- Design words: point size, hit target.

### 5. Font combination
- Look for: three or more typefaces, two similar sans serifs fighting, a decorative font used for body text.
- Fix: one typeface, or two at most: one for the interface, plus a display face for big headings if the app wants personality. On iOS and Android, the system font for the interface is the right default. See Fonts below.
- Design words: typeface, weight.

### 6. Font settings
- Look for: fixed sizes that ignore the user's text size setting, tight or loose line height, wide tracking on big titles, numbers that jiggle, light weights at small sizes.
- Fix:
  - Line height: body 1.4 to 1.6, headings 1.1 to 1.25, big display 1.0 to 1.1.
  - Tracking: tighten big text a little (about −1% to −3% at 32 px and up), loosen small all-caps labels (+4% to +8%). Leave body text alone.
  - Tabular numbers on anything that counts, ticks or lines up in columns.
  - No Ultralight, Thin or Light below 20 pt.
  - iOS: text styles so Dynamic Type works. Android: sp units. Web: rem units, `text-wrap: balance` on headings and `pretty` on paragraphs.
- Design words: line height, tracking, tabular numbers, Dynamic Type, text style.

### 7. Contrast
- Look for: grey text on white, white text on photos or bright gradients, placeholder-pale secondary text, text on glass.
- Fix: at least 4.5:1 for body text, 3:1 for large text (24 px and up, or 18.5 px bold) and for icons and control edges. Fix the colour itself; add a dimming layer or a material behind text on photos.
- Design words: contrast, dimming layer, semantic colour.

### 8. AI-default colour
- Look for: one of the three AI-default looks below, three or more of its tells together, with no brand stated in the project.
- Fix: replace the palette as described below, and say so.
- Design words: accent colour, palette, neutrals.

### 9. Radius
- Look for: five different corner radii, the same radius on everything, an inner shape with the same radius as the shape around it, sharp and round corners mixed for no reason.
- Fix: one radius scale, used by role. Nested shapes are concentric: the inner radius is the outer radius minus the padding between them (never below 4). iOS uses continuous corners.
- Preset scale (web): 6 for small controls, 10 for inputs and buttons, 16 for cards, 24 for sheets and big panels, full for pills. Android: Material 3 shapes (4, 8, 12, 16, 28, full).
- Design words: corner radius, concentric corners, continuous corners, capsule.

### 10. Depth
- Look for: a border and a shadow on the same card, shadows on everything, cards inside cards, heavy dark shadows.
- Fix: one way to separate things per level: background colour, or a hairline, or a shadow, not all three. One soft shadow, only on things that float (sheets, menus, a floating button). Flatten cards inside cards into one card with sections.
- Preset shadow (web, light mode): `0 1px 2px rgb(0 0 0 / .06), 0 8px 24px -12px rgb(0 0 0 / .18)`. In dark mode, use a lighter surface instead of a shadow.
- Design words: shadow, layering, card.

### 11. Consistency
- Look for: the same button styled two ways, two icon sets or stroke weights, more than one accent colour doing the "tap here" job, the same kind of row looking different on two screens.
- Fix: one style per component, one icon set and weight, one accent. Pull the repeated values into tokens.
- Design words: accent colour, SF Symbols, states.

### 12. Light and dark mode
- Look for: hard-coded black text and white backgrounds, colours that vanish in the other mode, pure black (#000) dark backgrounds with pure white text.
- Fix: semantic colours or tokens with a light and a dark value. Dark mode backgrounds a step above pure black, text a step below pure white. Check every fix in both modes.
- Design words: dark mode, semantic colour.

---

## AI-default looks

AI tools reach for the same few palettes. Each one looks fine alone and says "generated" the moment people have seen it ten times. Flag a look only when **three or more of its tells appear together** and the project states no brand. One tell alone is not a problem: a warm off-white background or Inter on its own is fine.

### Cream and terracotta
- A warm off-white page (around #F4F1EA to #FAF7F2)
- A terracotta or burnt orange accent (around #D97757, #E8793A, #C2410C)
- Slate navy text (around #1E293B) instead of a true dark ink
- Pastel mint and peach tinted panels
- Soft blurred glow blobs (radial gradients) behind the hero
- A serif italic or quirky grotesque headline (Instrument Serif, Bricolage Grotesque, Fraunces) over Inter body text
- A pill badge with a dot above the headline, a friendly mascot

### Indigo and slate
- Indigo, violet or purple accents (#6366F1, #8B5CF6, #A855F7)
- Purple-to-blue or cyan-to-purple gradients, gradient text
- A slate-900 dark background (#0F172A) with neon accents and glows
- Glass panels on everything
- Space Grotesk or default Inter

### The unstyled component kit
- Zinc and neutral greys (#09090B, #71717A, #E4E4E7) with a black primary button
- The same medium radius on every element
- A 1 px border on every card and input
- Default Inter or Geist with no size or tracking changes
- The same outline icon set at the same size everywhere

### Layout tells (any look)
- Everything centred
- Three feature cards, each with an icon in a rounded square
- An emoji or a sparkle icon as every bullet
- Identical card grids where a list would read better

### What to replace them with
1. **Pick the accent from what the app is about.** A plant app gets a moss or leaf green, a weather app the colour of its sky, a reading app ink and paper. If `voiceandtone.md` names a feeling, let it lean the choice (warm or cool, bright or deep).
2. **Avoid the hues of the look you're replacing.** No terracotta for the cream look, no indigo or violet for the slate look.
3. **One accent**, used only for actions and highlights. A darker shade of it for accent-coloured text, so it passes 4.5:1.
4. **Neutrals tinted a little towards the accent**, not straight from a default grey ramp. A true dark ink for text (around #111 to #1C1C1C), not slate navy.
5. **Remove the decoration that came with the look:** glow blobs, gradient text, glass on content, pastel panels that don't group anything.
6. **Announce it:** "Your terracotta (#E8793A) and cream background are a common AI-default look. I swapped the accent for moss green (#3F7D4E) and moved the background to a plain off-white. Say 'keep my colours' to undo."

---

## Fonts

### Native apps: system first
- **iOS:** SF Pro for the interface, with text styles. New York (serif) or SF Pro Rounded are built in if the app wants warmth. A custom font is for big headings or a brand moment. If you add one, bundle it, register it in Info.plist (UIAppFonts), and keep Dynamic Type with `.custom(_:size:relativeTo:)`.
- **Android:** Roboto or the device font with the Material 3 type scale. A custom font goes in `res/font`, or use downloadable Google Fonts.

### Web: pick by feeling
All of these are free for commercial use (SIL Open Font License on Google Fonts, or Fontshare's free licence). Check the licence before you ship.

| Feeling | Interface font | Display font for big headings (optional) |
|---|---|---|
| Friendly, warm | Plus Jakarta Sans, Figtree, DM Sans | Gabarito, Bricolage Grotesque |
| Precise, technical | Inter, Geist, IBM Plex Sans | Inter Display (Inter's optical size), Geist |
| Editorial, bookish | Public Sans, Source Sans 3 | Newsreader, Fraunces |
| Bold, product | Manrope, Onest, Schibsted Grotesk | Satoshi (Fontshare), Cabinet Grotesk (Fontshare) |
| Playful, soft | Nunito, Quicksand | SF Pro Rounded (Apple), Gabarito |
| Code and numbers | Geist Mono, JetBrains Mono, IBM Plex Mono | |

### Pairings that work
- Plus Jakarta Sans alone, three weights. The easiest upgrade from default Inter.
- Inter for the interface, Inter Display or the optical size axis for headings.
- DM Sans for the interface, Fraunces for big headings.
- Geist for the interface, Geist Mono for numbers and labels.
- IBM Plex Sans with IBM Plex Mono.
- Figtree for the interface, Gabarito for headings.

### Inter, used on purpose
Inter is excellent, and also the default of nearly every AI-built screen. If the project uses it, keep it and make it look chosen:
- Use the optical size axis (or Inter Display) for text at 32 px and up, with tighter tracking.
- Three weights at most, for example 400, 500 and 650.
- Tabular numbers wherever numbers change or line up.
- Pair it with one display face or a mono for character, or switch to Plus Jakarta Sans or Geist if the screen still looks generic.

### Loading fonts on the web
- Two families at most, variable fonts where available, only the weights you use.
- `font-display: swap`, and self-host or preconnect so text never waits.
- Set fallbacks with similar metrics so the page doesn't jump when the font arrives.

---

## Presets (only when the project has no system)

**Spacing:** 4, 8, 12, 16, 24, 32, 48, 64.

**Type scale, web (px, line height):** 12/16, 14/20, 16/24 body, 18/28, 20/28, 24/32, 30/36, 36/40, 48/52, 60/64.

**Type, iOS (text styles, default pt):** Large Title 34, Title 1 28, Title 2 22, Title 3 20, Headline 17 semibold, Body 17, Callout 16, Subheadline 15, Footnote 13, Caption 1 12, Caption 2 11.

**Type, Android (Material 3, sp):** Display 57/45/36, Headline 32/28/24, Title 22/16/14, Body 16/14/12, Label 14/12/11.

**Radius, web:** 6, 10, 16, 24, full. **Android:** 4, 8, 12, 16, 28, full. **iOS:** continuous, 10 to 12 for controls, 16 to 22 for cards, concentric inside.

**Colour structure:** one accent (plus a darker shade for text), a neutral ramp of 8 to 10 steps tinted towards the accent, and success, warning and error colours. Every colour has a light and a dark value.

---

## Report template

```
**Tidied: Home screen** (SwiftUI)

| | Before | After | Why |
|---|---|---|---|
| Spacing | 13, 18, 22 pt gaps | 16 inside groups, 32 between | One spacing scale, clearer groups |
| Hierarchy | Title and date both Body | Title Headline, date Footnote in secondaryLabel | One clear first thing to read |
| Contrast | Date #A0A0A0 on white (2.6:1) | secondaryLabel (passes 4.5:1) | Readable, and adapts to dark mode |
| Radius | Card 16, button 16 inside 8 pt padding | Card 16, button 8 | Concentric corners |

**AI-default look:** Indigo and slate (indigo accent, purple gradient header, glass cards). Swapped the accent for moss green and removed the gradient. Say "keep my colours" to undo.

**Left alone:** the layout, the copy, the animations.

Check it on your phone. The simulator and the preview can lie.
```

---

## Sources

- Apple HIG, Typography: https://developer.apple.com/design/human-interface-guidelines/typography
- Apple HIG, Layout: https://developer.apple.com/design/human-interface-guidelines/layout
- Apple HIG, Color: https://developer.apple.com/design/human-interface-guidelines/color
- Apple HIG, Accessibility: https://developer.apple.com/design/human-interface-guidelines/accessibility
- Material Design 3, Typography: https://m3.material.io/styles/typography/type-scale-tokens
- Material Design 3, Shape: https://m3.material.io/styles/shape/corner-radius-scale
- Material Design 3, Accessible design: https://m3.material.io/foundations/designing/structure
- WCAG 2.2, Contrast (minimum): https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html
- Google Fonts: https://fonts.google.com
- Fontshare: https://www.fontshare.com
- Inter, by Rasmus Andersson: https://rsms.me/inter/
- Emil Kowalski's skills, for motion: https://aiforui.dev
