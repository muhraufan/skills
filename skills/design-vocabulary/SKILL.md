---
name: design-vocabulary
description: Reverse lookup for app design words. Turns a loose description or a screenshot of what feels off ("the cards feel cramped and the title gets lost", "the countdown numbers wiggle", "that little bar at the top of the sheet") into the exact term, how it differs from the term people mix it up with, any anti-pattern to avoid, and a ready-to-paste prompt with real values. Covers spacing, type, colour, layout, components, iOS surfaces and Liquid Glass, haptics, and the core of iOS motion. Use when someone asks "what's it called when…", describes what they see without the word for it, or wants a vague prompt made specific. For naming what you see, not for designing or building it.
---

# design-vocabulary

Helps you find the exact design word, so you ask your AI for what you actually want.

Made for The Weekend Project (https://theweekendproject.club), lesson 3.2, and free for everyone. The idea follows Emil Kowalski's animation-vocabulary skill (https://aiforui.dev/skills/animation-vocabulary). For motion beyond the core here, this skill points you to his.

## What it does

- Maps a loose description of what you see to its exact term, like "the text is hard to read on top of the photo" to contrast, plus a dimming layer or a material behind it
- Names what's in a screenshot: paste one, say which part bugs you, and get the words for it
- Tells close terms apart, like padding versus margin, tracking versus kerning, or regular glass versus clear glass
- Covers spacing, type, colour, layout, components, iOS surfaces and materials, haptics, and the core of iOS motion
- Names the anti-patterns too, like scale from zero, haptics on every tap, low contrast text on glass, and tap targets under 44 pt

## When to use it

When you can see what's off on your screen but don't know what it's called. Describe it the way you'd tell a friend, or paste a screenshot. The right word gets your AI building the right thing on the first try.

## Example prompts

You don't need special wording. Say it like you'd say it to a teammate.

- /design-vocabulary what's it called when the text is hard to read on top of a photo?
- /design-vocabulary the cards feel cramped and the title gets lost
- /design-vocabulary the numbers in my countdown keep wiggling every second
- /design-vocabulary that little bar at the top of a sheet that tells you you can drag it
- /design-vocabulary [screenshot] the bottom of this screen feels off but I can't say why

## How to answer

When someone describes something loosely, or shares a screenshot:

1. Lead with the term. Map what they describe to 1 to 3 exact terms from this file, in bold. Pick the fewest that cover it.
2. Explain each term in one line, in plain words.
3. Name the closest term people mix it up with, and say how the two differ.
4. If the description points at a known anti-pattern, flag it and say what to do.
5. End with one ready-to-paste prompt that uses the exact terms, with real values where they help (pt, ms, %).

Keep it short: about 120 words before the prompt. Use the terms and values from this file. If a term isn't in this file, say so and give your best guess, marked as a guess.

With a screenshot, say which part of it you mean ("the gap under the title", "the three buttons at the bottom") before you name it.

Answer in the language the person writes in. Keep the terms and the prompt in English, since that's what AI tools and Apple's docs use.

For motion beyond the core terms here, send the person to Emil Kowalski's animation-vocabulary skill.

When the skill is opened with nothing else, reply only: "Tell me what you see, the way you'd tell a friend, or paste a screenshot. I'll give you the word for it and a prompt to paste."

### Platform

This file is written for iPhone, with Apple's names and sizes in points (pt). If the person builds for Android or the web, keep the idea and translate: pt to dp on Android or px on the web, a sheet to a bottom sheet, SF Symbols to the icon set they use, and haptics to vibration on Android (the web can't vibrate on iPhone). Say when a term is Apple-only, like Liquid Glass or Dynamic Island.

### Example answer

For "the cards feel cramped and the title gets lost":

> That's three things: **padding** (space inside the card, between its edge and the content), **line height** (the vertical space each line of text takes), and **type hierarchy** (the order the eye reads things, set by size, weight and colour).
> Close to margin: margin is the space outside the card, between cards. Padding is the space inside it.
> Prompt: "Give each card 16 pt of padding, raise the body line height a step, and fix the type hierarchy: make the title Headline Semibold and the details Subheadline in secondaryLabel."

---

## Spacing

### Padding
- Means: space inside an element, between its edge and its content.
- People describe it as: "the text is touching the edge", "the card feels cramped", "needs more room inside"
- Close to Margin: margin is the space outside an element, padding is the space inside it.
- Prompt: "Give the plant card 16 pt of padding on all sides so the name stops touching the edge."

### Margin
- Means: space outside an element that pushes it away from its neighbours.
- People describe it as: "the sections are glued together", "push this down a bit"
- Close to Padding: padding lives inside the element, margin sits around it.
- Prompt: "Add a 24 pt top margin above the Watering section header."

### Gap
- Means: the space between items in a row, column or grid.
- People describe it as: "the chips are too close to each other", "even space between the buttons"
- Close to Margin: a gap is set once on the row or grid and applies between every item.
- Prompt: "Set an 8 pt gap between the three filter chips."

### Spacing scale
- Means: a fixed set of spacing values you reuse everywhere, often steps of 4 or 8.
- People describe it as: "the spacing feels random", "nothing lines up"
- Close to 8 pt grid: the grid is the habit of using multiples of 8, the scale is your actual list of allowed values.
- Avoid: one-off values like 13 pt or 19 pt scattered around. Snap them to the scale.
- Prompt: "Use only our spacing scale (4, 8, 12, 16, 24, 32) and swap any odd values for the closest step."

### 8 pt grid
- Means: the habit of making sizes and spacing multiples of 8, so everything lines up.
- People describe it as: "make everything line up", "the sizes feel random"
- Close to Spacing scale: the grid is the rule of thumb, the scale is the list of values you actually use.
- Prompt: "Snap every margin on the Today screen to the 8 pt grid."

### Safe area
- Means: the part of the screen clear of the Dynamic Island, status bar and home indicator.
- People describe it as: "my button is under the notch", "stuff is hiding behind the clock"
- Close to Layout margins: the safe area keeps you clear of hardware and system bars, layout margins are the extra side space iOS adds inside it.
- Avoid: putting buttons or text outside the safe area. Backgrounds can run to the edges, controls stay inside.
- Prompt: "Keep the Water button inside the safe area, and let the sky background run behind it to the edges."

### Layout margins
- Means: the default side margins iOS gives content inside a view.
- People describe it as: "my header doesn't line up with the list", "the sides look uneven"
- Close to Safe area: the safe area is about hardware, layout margins are about consistent side spacing.
- Prompt: "Line the section headers up with the system layout margins so they match the list rows."

### Whitespace
- Means: empty space used on purpose to group things and give the eye a rest.
- People describe it as: "too busy", "everything is fighting for attention", "it needs room"
- Close to Breathing room: breathing room is the casual word for whitespace around one important thing.
- Prompt: "Add more whitespace between the hero photo and the care tips, the screen feels cramped."

### Breathing room
- Means: the casual word for enough whitespace around one important thing.
- People describe it as: "let it breathe", "it's squeezed in"
- Close to Whitespace: whitespace is the space across the whole screen, breathing room is the space around one thing.
- Prompt: "The prayer time needs more breathing room, double the space above and below it."

### Density
- Means: how much content fits in a given space, compact or roomy.
- People describe it as: "I want to see more rows at once", "it feels too spread out"
- Close to Whitespace: whitespace is the empty space itself, density is the overall feel of how packed the screen is.
- Prompt: "Make the plant list more compact: tighter rows, smaller thumbnails, same font size."

### Proximity
- Means: things placed close together read as one group.
- People describe it as: "the date looks like it belongs to the wrong item", "these don't feel related"
- Close to Gap: gap is a number, proximity is the grouping effect that number creates.
- Prompt: "Move the date closer to the reminder title so they read as one unit."

### Hit target
- Means: the tappable area of a control, which can be bigger than what you see.
- People describe it as: "hard to tap", "I keep missing the X", "my thumb hits the wrong thing"
- Close to Padding: padding changes how it looks, the hit target only changes where you can tap.
- Avoid: hit targets under 44 by 44 pt on iPhone.
- Prompt: "Make the close X a 44 by 44 pt hit target even though the icon is 17 pt."

### Optical alignment
- Means: nudging things so they look aligned to the eye, even when the maths says they already are.
- People describe it as: "it's centred but looks off", "the icon looks a bit to the left"
- Close to Alignment: alignment follows the numbers, optical alignment follows your eye.
- Prompt: "The play triangle looks off centre, shift it 1 pt right for optical alignment."

### Content inset
- Means: extra space at the start or end of a scroll view so content clears floating bars.
- People describe it as: "the last item hides behind the tab bar", "I can't scroll to the bottom row"
- Close to Padding: padding sits inside one element, a content inset is extra scroll room for the whole list.
- Prompt: "Add a bottom content inset so the last plant scrolls fully above the tab bar."

## Type

### Typeface
- Means: the design of the letters, like SF Pro or New York.
- People describe it as: "a different font", "something more classy for the title"
- Close to Weight: weight is how thick one typeface is drawn, the typeface is the whole design.
- Avoid: more than two typefaces in one app.
- Prompt: "Use New York for the plant's name and SF Pro for everything else."

### SF Pro
- Means: Apple's system typeface for iPhone, the one you get by default.
- People describe it as: "the normal iPhone font", "the default font"
- Close to SF Pro Rounded: same letters, without the rounded stroke ends.
- Prompt: "Stick to SF Pro across the app, no custom fonts."

### SF Pro Rounded
- Means: the rounded version of Apple's system typeface, friendlier and more playful.
- People describe it as: "make the numbers feel cute", "rounder letters"
- Close to SF Pro: same letters, with rounded stroke ends.
- Prompt: "Switch the big countdown numbers to SF Pro Rounded."

### Weight
- Means: how thick the strokes are, from Ultralight to Black.
- People describe it as: "make it bolder", "the text looks thin"
- Close to Point size: size makes text bigger, weight makes it heavier.
- Avoid: too many weights on one screen (two or three is plenty), and Ultralight, Thin or Light at small sizes, where they get hard to read.
- Prompt: "Make the prayer name Semibold and the time Regular."

### Point size
- Means: how big text is, measured in points (pt).
- People describe it as: "make it bigger", "the text is tiny"
- Close to Text style: a point size is one fixed number, a text style is a named role that also follows Dynamic Type.
- Prompt: "Bump the plant name from 20 to 28 pt."

### Text style
- Means: Apple's named sizes like Large Title, Title, Headline, Body and Caption.
- People describe it as: "use the normal iOS sizes", "make it match other apps"
- Close to Point size: a point size is one fixed number, a text style is a named role that also scales with Dynamic Type.
- Prompt: "Use the Headline text style for card titles and Footnote for the last watered date."

### Dynamic Type
- Means: the iOS setting that lets people pick their text size, which your text should follow.
- People describe it as: "my mum has big text on and the app breaks", "text doesn't get bigger"
- Close to Text style: text styles are how your app gets Dynamic Type for free.
- Avoid: fixed point sizes everywhere, which ignore the setting.
- Prompt: "Support Dynamic Type on every screen and check the layout at the largest accessibility size."

### Hierarchy
- Means: the order of importance the eye follows, set by size, weight and colour.
- People describe it as: "the title gets lost", "I don't know where to look first", "everything looks the same"
- Close to Contrast: contrast is how much one thing stands out from its background, hierarchy is how things rank against each other.
- Prompt: "Fix the type hierarchy: the next prayer should be the first thing I read, the other times come second."

### Visual weight
- Means: how strongly something pulls the eye, from its size, colour, contrast and how much ink it uses.
- People describe it as: "this icon is too loud", "the button is shouting", "the layout feels lopsided"
- Close to Hierarchy: visual weight is how heavy one thing feels, hierarchy is the order all of them make together.
- Prompt: "The Delete button has too much visual weight, make it a plain text button so Save leads."

### Line height
- Means: the vertical space each line of text takes up. People also say leading.
- People describe it as: "the lines are squished together", "the paragraph is hard to read"
- Close to Tracking: tracking is space between letters, line height is space between lines.
- Prompt: "Increase the line height on the care tips so the paragraphs are easier to read."

### Tracking
- Means: even spacing added or removed across a whole word or line.
- People describe it as: "the letters look too spread out", "the big title feels loose"
- Close to Kerning: kerning fixes one pair of letters, tracking changes the whole line.
- Prompt: "Tighten the tracking on the large title by about 1 pt."

### Kerning
- Means: spacing between one specific pair of letters.
- People describe it as: "there's a weird gap between these two letters"
- Close to Tracking: tracking moves every letter, kerning moves one pair.
- Prompt: "The 'Wa' in Water looks gappy, fix the kerning there."

### Tabular numbers
- Means: digits that all share one width, so numbers don't jiggle when they change.
- People describe it as: "the timer wiggles", "the numbers jump left and right"
- Close to Monospaced font: a monospaced font makes every character the same width, tabular numbers only do it for digits and keep the rest of the font as is.
- Prompt: "Use tabular numbers on the countdown so it stops wobbling every second."

### All caps
- Means: text set entirely in capital letters, usually small and with extra tracking.
- People describe it as: "the little uppercase labels", "section titles in capitals"
- Close to Tracking: all caps changes the letters, and it almost always needs a little extra tracking to read well.
- Avoid: all caps for anything longer than a short label.
- Prompt: "Make the section labels all caps, Caption 2, with a bit of extra tracking."

### Truncation
- Means: cutting off text that doesn't fit, usually with an ellipsis.
- People describe it as: "the long name breaks the layout", "add the three dots"
- Close to Line limit: a line limit sets how many lines are allowed, truncation is what happens to the text past that.
- Prompt: "Truncate long plant names to one line with an ellipsis at the end."

### Line length
- Means: how many characters fit on one line. Around 45 to 75 reads well.
- People describe it as: "the text goes all the way across on iPad", "my eyes get lost going to the next line"
- Close to Margin: margins can shorten lines, line length is the result you're aiming for.
- Prompt: "Cap the line length of the article text so lines don't stretch across the iPad."

### Baseline
- Means: the invisible line letters sit on.
- People describe it as: "the small AM looks like it's floating", "two sizes of text don't line up"
- Close to Centre alignment: centring mixed sizes looks off, baseline alignment makes them sit on the same line.
- Prompt: "Align the time and the AM label on their baseline."

## Colour

### Hue
- Means: the colour itself, like red, green or blue.
- People describe it as: "a different green", "more blue-ish"
- Close to Saturation: hue picks which colour, saturation sets how strong it is.
- Prompt: "Shift the accent hue a little towards teal."

### Saturation
- Means: how intense or washed out a colour is.
- People describe it as: "the green is too loud", "the colour looks dull"
- Close to Brightness: brightness is light versus dark, saturation is intense versus grey.
- Prompt: "Lower the saturation of the leaf green, it's too loud next to the photos."

### Brightness
- Means: how light or dark a colour is.
- People describe it as: "make it lighter", "the card is too dark"
- Close to Opacity: lower brightness makes a colour darker, lower opacity lets the background show through.
- Prompt: "Raise the brightness of the card background in dark mode by a step."

### Warm and cool
- Means: colours leaning towards orange and red (warm), or towards blue (cool).
- People describe it as: "it feels cold", "make it feel cosier"
- Close to Hue: warm and cool describe which way a colour leans, hue is the exact colour.
- Prompt: "Make the evening screens cooler and the morning screens warmer."

### Accent colour
- Means: the one colour you use for actions and highlights. Apple calls it tint.
- People describe it as: "the main colour of the app", "make all the buttons green"
- Close to Palette: the palette is every colour you use, the accent is the one that means "tap here".
- Prompt: "Set the app's tint to our moss green so buttons and toggles pick it up."

### Semantic colour
- Means: a colour named by its job, like label or secondaryLabel, that adapts to light and dark mode.
- People describe it as: "the text disappears in dark mode", "colours look wrong when I switch to dark"
- Close to a fixed hex colour: a hex value stays the same in every mode, a semantic colour switches for you.
- Avoid: hard-coded black text and white backgrounds that stay put when dark mode turns on.
- Prompt: "Use semantic colours: label for titles, secondaryLabel for dates, separator for lines."

### Contrast
- Means: how much text stands out from its background.
- People describe it as: "hard to read on top of the photo", "the grey text is too faint"
- Close to Hierarchy: contrast is text against its background, hierarchy is text against other text.
- Avoid: body text under 4.5:1 contrast, and low contrast text on glass or over photos.
- Prompt: "Check contrast on the white text over the sky. It needs to reach at least 4.5:1."

### Dark mode
- Means: the dark appearance iOS can switch to.
- People describe it as: "the app is blinding at night", "make a night version"
- Close to a night theme: a custom night theme is your own design choice, dark mode follows the system setting.
- Avoid: testing only in light mode.
- Prompt: "Design a proper dark mode for the Today screen using system backgrounds, and check every screen in both modes."

### Opacity
- Means: how see-through something is, from 0 to 100%.
- People describe it as: "make it a bit see-through", "fade the inactive ones"
- Close to Brightness: lower brightness makes a colour darker, lower opacity lets the background show through.
- Prompt: "Drop the inactive tab icons to 40% opacity."

### Gradient
- Means: a blend from one colour to another across a shape.
- People describe it as: "the colour fades from orange to blue", "like a sunset background"
- Close to Dimming layer: a dimming layer is one see-through colour over content, a gradient blends two or more colours.
- Prompt: "Fill the background with a vertical gradient from dawn orange to night blue."

### Palette
- Means: the full set of colours an app uses.
- People describe it as: "too many colours", "the app feels messy"
- Close to Accent colour: the accent is one colour, the palette is all of them.
- Prompt: "Limit the palette to two greens, one warm neutral and the system greys."

### Neutrals
- Means: the greys, whites and off whites that do most of the work.
- People describe it as: "the app feels cold", "the greys look too blue"
- Close to Semantic colour: neutrals are a set of colours, semantic colours are how you name and use them.
- Prompt: "Warm up the neutrals slightly so the app feels less clinical."

### Display P3
- Means: the wider colour range iPhone screens can show.
- People describe it as: "my orange looks dull on the phone", "the colours look better in Figma"
- Close to sRGB: sRGB is the smaller, older colour range most exports default to.
- Prompt: "Export the sky gradient in Display P3 so the oranges don't look dull."

## Layout

### Alignment
- Means: lining things up along a shared edge or centre.
- People describe it as: "things look messy", "the text and the photo start in different places"
- Close to Optical alignment: alignment follows the numbers, optical alignment follows the eye.
- Prompt: "Left align everything on the card to the same edge as the photo."

### Leading and trailing
- Means: the start and end side of a line, which flips for right to left languages.
- People describe it as: "the arrow is on the wrong side in Arabic"
- Close to Left and right: left and right stay put, leading and trailing flip with the language.
- Prompt: "Put the chevron on the trailing edge so it flips correctly in Arabic."

### Grid
- Means: columns and rows that elements snap to.
- People describe it as: "show them in tiles", "two per row"
- Close to Stack: a stack is one line of items, a grid has rows and columns.
- Prompt: "Show the plants in a two column grid with square photos."

### Stack
- Means: elements placed in a vertical or horizontal line. SwiftUI calls them VStack and HStack.
- People describe it as: "put the icon next to the text", "line these up one under the other"
- Close to Grid: a stack is one line of items, a grid has rows and columns.
- Prompt: "Put the icon and label in a horizontal stack with 6 pt between them."

### Aspect ratio
- Means: the width to height relationship of a shape, like 1:1 or 4:5.
- People describe it as: "the photos are all different shapes", "make them square"
- Close to Truncation: both deal with things that don't fit, aspect ratio crops images, truncation cuts text.
- Prompt: "Crop plant photos to a 4:5 aspect ratio everywhere."

### Full bleed
- Means: content that runs right to the screen edges.
- People describe it as: "edge to edge", "make the photo fill the whole width"
- Close to Safe area: full bleed ignores it for the background, while text and buttons still respect it.
- Prompt: "Make the hero photo full bleed, edge to edge, behind the status bar."

### Hero
- Means: the big, main visual at the top of a screen.
- People describe it as: "the big thing at the top", "make the main number huge"
- Close to Header: a header labels a section, a hero is the main visual of the whole screen.
- Prompt: "Turn the next prayer into a hero with the time in a huge number."

### Card
- Means: a contained block grouping related info, usually with rounded corners.
- People describe it as: "put each one in a box", "group this stuff together"
- Close to Inset grouped list: a list groups rows inside one rounded block, cards are separate blocks.
- Prompt: "Group each plant's photo, name and next watering into a card."

### Inset grouped list
- Means: the iOS list style where rows sit in rounded groups, inset from the screen edges, like Settings.
- People describe it as: "make it look like the Settings app", "rounded sections of rows"
- Close to Card: an inset grouped list holds many rows in one rounded block, cards are separate blocks.
- Prompt: "Use an inset grouped list for Settings, with Reminders and Appearance as two groups."

### Navigation bar
- Means: the bar at the top with the title and back button.
- People describe it as: "the top bar", "the title that shrinks when I scroll"
- Close to Toolbar: the navigation bar holds the title and back button, a toolbar holds actions.
- Prompt: "Use a large title in the navigation bar that shrinks on scroll."

### Toolbar
- Means: a bar of actions for the current screen, at the top or bottom.
- People describe it as: "the buttons at the top right", "where do Edit and Share go?"
- Close to Tab bar: toolbar buttons act on the current screen, tabs switch between sections.
- Prompt: "Move Edit and Share into the toolbar at the top right."

### Tab bar
- Means: the bar at the bottom for switching between main sections.
- People describe it as: "the buttons at the bottom", "the main menu"
- Close to Toolbar: tabs switch sections, toolbar buttons act on the current screen.
- Avoid: using tabs for actions like Add or Share.
- Prompt: "Add a tab bar with three tabs: Today, Plants, Settings."

### Sticky header
- Means: a header that stays pinned while content scrolls under it.
- People describe it as: "keep the month title stuck at the top while I scroll"
- Close to Navigation bar: the navigation bar is always there, a sticky header belongs to one section of the list.
- Prompt: "Make the month headers sticky in the watering history."

### Layering
- Means: which element sits on top of which. Devs call it z order.
- People describe it as: "the button is hiding behind the list", "this should be on top"
- Close to Shadow: a shadow makes something look lifted, layering decides what's actually on top.
- Prompt: "Put the floating button on the top layer, above the list and the tab bar."

### Empty state
- Means: what a screen shows when there's no content yet.
- People describe it as: "the screen is just blank at first", "what do new users see?"
- Close to Onboarding: onboarding explains the app once, an empty state shows up whenever a screen has nothing in it.
- Avoid: a blank screen with no next step.
- Prompt: "Design an empty state for Plants with an illustration and an Add your first plant button."

### Loading state
- Means: what a screen shows while content is on its way. A skeleton is a grey outline of the layout that fills in.
- People describe it as: "it's blank for a second", "the spinner feels slow", "everything jumps when it loads"
- Close to Empty state: a loading state means content is coming, an empty state means there's nothing there.
- Avoid: a full screen spinner when you already know the layout. Show a skeleton in its shape.
- Prompt: "Show a skeleton of three plant cards while the list loads, then fade the real cards in."

## Components

### States
- Means: the looks one control has: default, pressed, selected, disabled, and focused.
- People describe it as: "it doesn't look tappable when it's off", "I can't tell which one is picked"
- Close to Affordance: affordance is whether something looks tappable at all, states show what it's doing right now.
- Avoid: a disabled button that looks the same as an enabled one.
- Prompt: "Design all states for the Water button: default, pressed at 0.97 scale, and disabled at 40% opacity."

### Affordance
- Means: how well something shows what you can do with it, like a button looking pressable.
- People describe it as: "people don't know it's a button", "nobody finds the swipe"
- Close to States: affordance tells you it's tappable, states tell you what it's doing.
- Prompt: "The Add row doesn't look tappable, give it the accent colour and a plus icon."

### Sheet
- Means: a panel that slides up from the bottom over the current screen.
- People describe it as: "the thing that slides up from the bottom", "a bottom drawer"
- Close to Popover: a sheet comes from the bottom edge, a popover points at the thing you tapped.
- Prompt: "Open plant details in a sheet that slides up over the list."

### Detent
- Means: a height a sheet can rest at, like medium or large.
- People describe it as: "make it stop halfway", "the sheet should snap to half"
- Close to Sheet: the sheet is the panel, detents are the heights it snaps to.
- Prompt: "Give the sheet two detents, medium and large, and open it at medium."

### Grabber
- Means: the small bar at the top of a sheet that shows you can drag it.
- People describe it as: "that little line at the top of the sheet"
- Close to Home indicator: the home indicator is the system bar at the bottom of the screen, the grabber belongs to your sheet.
- Prompt: "Show the grabber on the details sheet so people know it resizes."

### Popover
- Means: a small floating panel pointing at the thing you tapped.
- People describe it as: "a little bubble next to the button", "a tooltip with more text"
- Close to Menu: a menu is a list of actions, a popover can hold any content.
- Prompt: "Show the watering tip in a popover anchored to the info button."

### Menu
- Means: a list of actions that pops out of a button.
- People describe it as: "the three dots options", "a dropdown"
- Close to Alert: a menu offers choices you can ignore, an alert stops you and asks.
- Prompt: "Turn the ... button into a menu with Rename, Move and Delete."

### Alert
- Means: a small box in the middle that asks for a decision.
- People describe it as: "are you sure?", "a popup that asks before deleting"
- Close to Toast: a toast tells you something and leaves by itself, an alert waits for your answer.
- Avoid: alerts for good news. Save them for decisions that matter.
- Prompt: "Confirm Delete Plant with an alert, with Delete in red."

### Toast
- Means: a short message that slides in, stays a moment, and leaves. A casual name, Apple doesn't use it.
- People describe it as: "a little message that says saved", "a banner that goes away by itself"
- Close to Alert: an alert needs a tap, a toast leaves on its own.
- Prompt: "After saving, show a toast saying Watered 🌱 at the top for 2 seconds."

### Corner radius
- Means: how round the corners of a shape are.
- People describe it as: "rounder corners", "the corners look sharp"
- Close to Continuous corners: corner radius is how big the curve is, continuous corners change how smooth it is.
- Prompt: "Set the card corner radius to 20 pt."

### Continuous corners
- Means: Apple's smoother rounded corners, sometimes called a squircle.
- People describe it as: "the corners look like the app icon", "smoother curve"
- Close to Corner radius: same size, a smoother curve into the straight edge.
- Prompt: "Use continuous corners on all cards so they match the app icon shape."

### Concentric corners
- Means: inner corners rounded so they follow the outer shape at the same distance. In SwiftUI on iOS 26, that's ConcentricRectangle.
- People describe it as: "the button corners look wrong inside the card", "the curves don't match"
- Close to Corner radius: concentric means the inner radius equals the outer radius minus the padding between them.
- Avoid: the same radius inside and outside, which makes the gap look thicker at the corners.
- Prompt: "Make the button corners concentric with the card around it, using ConcentricRectangle."

### Capsule
- Means: a shape with fully round ends, like a pill.
- People describe it as: "pill shaped", "fully round sides"
- Close to Corner radius: a capsule is the corner radius at half the height.
- Prompt: "Make the filter chips capsules."

### Segmented control
- Means: a row of connected buttons for picking one option.
- People describe it as: "the Day, Week, Month switch", "a toggle with three options"
- Close to Tab bar: a segmented control switches views inside one screen, a tab bar switches whole sections.
- Prompt: "Use a segmented control for Day, Week, Month at the top of the chart."

### SF Symbols
- Means: Apple's icon library that matches SF Pro in weight and size.
- People describe it as: "the normal Apple icons", "the icon looks too thick next to the text"
- Close to Rendering mode: SF Symbols is the library, rendering mode is how a symbol gets coloured.
- Prompt: "Use the SF Symbol drop.fill for watering and match its weight to the label."

### Rendering mode
- Means: how an SF Symbol is coloured: monochrome, hierarchical, palette or multicolour.
- People describe it as: "I want the cloud lighter than the sun", "a two-colour icon"
- Close to Palette: in rendering, palette means picking each layer's colour yourself. Hierarchical uses one colour at different strengths.
- Prompt: "Use hierarchical rendering on the weather icons so the cloud is lighter than the sun."

### Shadow
- Means: a darker area under an element that makes it look lifted.
- People describe it as: "make it pop off the page", "it looks flat"
- Close to Layering: layering decides what's on top, a shadow shows it.
- Avoid: big dark shadows on everything. One faint shadow on the thing that floats is plenty.
- Prompt: "Add a faint shadow under the floating button, 8 pt blur, 10% black."

## iOS surfaces and materials

### Liquid Glass
- Means: Apple's see-through material for controls and navigation that floats above your content (iOS 26).
- People describe it as: "the new glassy look", "that bubble glass on the buttons"
- Close to Materials: Liquid Glass is for the control layer on top, materials are for the content layer.
- Avoid: glass on glass, and glass on the content itself. Keep it for controls and navigation.
- Prompt: "Use Liquid Glass for the floating tab bar and keep the content layer solid."

### Regular glass
- Means: the default Liquid Glass variant, blurred enough to keep text readable anywhere.
- People describe it as: "glass but I can still read the text"
- Close to Clear glass: regular blurs more and works over anything, clear shows more of what's behind.
- Prompt: "Use regular glass for the filter bar since it sits over busy photos with text on it."

### Clear glass
- Means: the more see-through Liquid Glass variant, meant for controls over photos or video, with a dimming layer when needed.
- People describe it as: "really see-through glass", "glass over the camera view"
- Close to Regular glass: clear shows more of the content behind, so it needs bold content on top and often a dimming layer.
- Avoid: clear glass with small text over busy or bright backgrounds.
- Prompt: "Make the camera controls clear glass and add a dimming layer behind them on bright shots."

### Materials
- Means: Apple's standard blur levels for the content layer: ultra thin, thin, regular, thick.
- People describe it as: "a frosted background behind the caption", "blur behind the text"
- Close to Liquid Glass: materials sit in the content layer, Liquid Glass floats above it.
- Prompt: "Put the caption on a thin material so the photo still shows through."

### Vibrancy
- Means: Apple's effect that lets text and icons on a material pick up colour from behind it.
- People describe it as: "the text should blend with the blur", "the grey text looks pasted on"
- Close to Opacity: opacity just fades the text, vibrancy pulls colour from what's behind.
- Prompt: "Use vibrancy for the labels on the blurred header so they blend with the photo."

### Scroll edge effect
- Means: the blur and fade iOS adds where content scrolls under a bar (iOS 26).
- People describe it as: "the list should fade under the top bar", "the text clashes with the buttons when I scroll"
- Close to Sticky header: a sticky header is content that stays pinned, the scroll edge effect is how content fades under bars.
- Prompt: "Turn on the scroll edge effect so the list fades under the top bar."

### Dimming layer
- Means: a dark see-through layer behind something to make it stand out. Also called a scrim.
- People describe it as: "darken the background", "the white text is hard to read on the photo"
- Close to Gradient: a scrim can be a gradient too. What makes it a scrim is its job: readability.
- Prompt: "Add a 35% black dimming layer behind the sheet when it's at large."

### Dynamic Island
- Means: the pill shaped cutout at the top of newer iPhones that can show live info.
- People describe it as: "the notch", "the black pill at the top"
- Close to Safe area: the safe area already keeps your layout clear of the island.
- Prompt: "Keep the clock away from the Dynamic Island and show the countdown as a Live Activity there."

### Live Activity
- Means: live info from your app on the Lock Screen and in the Dynamic Island, like a countdown or a delivery.
- People describe it as: "show the timer on the lock screen", "put it in the pill at the top"
- Close to Widget: a widget sits on the Home Screen and refreshes now and then, a Live Activity follows one event as it happens.
- Prompt: "Show the time to the next prayer as a Live Activity, in the Dynamic Island and on the Lock Screen."

### Home indicator
- Means: the thin bar at the bottom of the screen for going home.
- People describe it as: "the line at the bottom", "my button is too close to the bottom"
- Close to Grabber: the grabber belongs to your sheet, the home indicator belongs to iOS.
- Prompt: "Leave room above the home indicator so the bottom button doesn't crowd it."

## Haptics

### Haptic
- Means: a small vibration you feel as feedback.
- People describe it as: "make it buzz", "I want to feel it when it saves"
- Close to Sound: a haptic is felt, and it works with the phone on silent.
- Avoid: haptics on every tap. Use them where feedback actually means something.
- Prompt: "Add a haptic when a plant is marked as watered."

### Impact
- Means: a tap that feels like something landing or snapping into place.
- People describe it as: "a click when it snaps", "a thud when it drops in"
- Close to Selection: selection is a tiny tick while scrolling values, impact is a bigger hit when something lands.
- Prompt: "Play an impact haptic when the card snaps into its slot."

### Impact styles
- Means: Apple's five impact feels: light, medium, heavy, rigid and soft. Light to heavy is strength. Rigid feels hard and crisp, soft feels squishy and rounded.
- People describe it as: "a bigger buzz", "more of a click", "less clicky, more squishy"
- Close to Intensity: intensity scales any one style up or down, the styles are different feels.
- Prompt: "Use a light impact for each drag step, a rigid one when it locks, and a soft one when the bubble lands."

### Selection
- Means: a tiny tick for moving through a list of values.
- People describe it as: "the clicky feel when you spin the time picker"
- Close to Impact: impact is for landing, selection is for each step.
- Prompt: "Play a selection haptic on each step of the hour picker."

### Notification
- Means: a pattern that reports an outcome: success, warning or error.
- People describe it as: "a buzz that says it worked", "a buzz that says something went wrong"
- Close to Impact: impact is one physical hit, notification patterns tell you how something turned out.
- Avoid: success haptics on things that didn't really finish yet.
- Prompt: "Play a success notification haptic after the reminder saves, and error when sync fails, together with the red banner."

### Detent haptic
- Means: a haptic when something reaches a set stop, like a sheet height or a slider mark.
- People describe it as: "let me feel when the sheet clicks into place"
- Close to Threshold: a detent is a resting stop, a threshold is a point of no return.
- Prompt: "Add a light impact each time the sheet reaches a detent."

### Threshold
- Means: the point in a gesture where an action will happen if you let go.
- People describe it as: "let me feel when I've swiped far enough to delete"
- Close to Detent haptic: a detent is a resting stop, a threshold is a point of no return.
- Prompt: "Play a medium impact when the swipe passes the delete threshold."

### Transient and continuous
- Means: transient is one short tap of vibration, continuous lasts for a while. Both come from Core Haptics.
- People describe it as: "a quick tick", "a long buzz"
- Close to Impact: impact is a ready-made transient, Core Haptics lets you build your own.
- Avoid: long buzzes for everyday feedback.
- Prompt: "Keep all haptics transient, and use a short continuous haptic only for the last 3 seconds of the timer."

### Intensity and sharpness
- Means: in Core Haptics, intensity is how strong a haptic feels, sharpness is how crisp or dull it feels.
- People describe it as: "too strong", "make it feel more like a click"
- Close to Impact styles: the styles are presets, intensity and sharpness are the two dials behind custom haptics.
- Prompt: "Lower the intensity of the scroll haptic and make the lock haptic sharper so it feels like a click."

### Core Haptics
- Means: Apple's framework for designing your own haptic patterns, beat by beat.
- People describe it as: "a custom vibration", "a buzz that builds up"
- Close to Sensory feedback: sensory feedback plays Apple's built-in haptics, Core Haptics builds custom patterns.
- Prompt: "Build a Core Haptics pattern that ramps up as the sun rises."

### Sensory feedback
- Means: SwiftUI's modifier for playing haptics when a value changes.
- People describe it as: "the SwiftUI way to add a buzz"
- Close to Core Haptics: sensory feedback plays Apple's built-in haptics, Core Haptics builds custom patterns.
- Prompt: "Use .sensoryFeedback(.selection, trigger: selectedDay) on the day picker."

### Haptics toggle
- Means: a setting to switch haptics off. Apple says they should be optional.
- People describe it as: "some people hate the buzzing"
- Close to System setting: iOS has a system switch too, your toggle lets people turn off just your app's haptics.
- Prompt: "Add a Haptics toggle in Settings and respect it everywhere."

## Motion (the core for iOS)

The motion words you'll use most when building for iPhone. For the rest, and for the web, use Emil Kowalski's animation-vocabulary skill, linked below.

### Easing
- Means: the way speed changes over an animation. Emil calls it the most important part.
- People describe it as: "it feels robotic", "it feels sluggish"
- Close to Duration: duration is how long it takes, easing is how the speed changes along the way.
- Avoid: ease-in for things entering the screen. It starts slow and feels laggy. Use ease-out.
- Prompt: "The easing on the card feels flat, give it a stronger ease-out curve."

### Ease-out
- Means: starts fast and slows at the end. Right for things entering or leaving.
- People describe it as: "it should feel instant", "snappy but smooth"
- Close to Ease-in: ease-in starts slow, so the start of the motion feels late.
- Prompt: "Use ease-out when the toast slides in so it feels instant."

### Ease-in-out
- Means: slow start, fast middle, slow end. Good for things moving across the screen.
- People describe it as: "it should glide from one place to another"
- Close to Ease-out: ease-out is for arriving and leaving, ease-in-out is for moving while already on screen.
- Prompt: "Use ease-in-out when the sun moves along its arc."

### Linear
- Means: the same speed the whole way. Fits constant motion like progress bars.
- People describe it as: "it should move at a steady speed"
- Close to Easing: linear is the one curve with no easing at all, which looks robotic on most UI.
- Prompt: "Make the loading bar linear."

### Duration
- Means: how long an animation lasts. Most UI motion stays under 300 ms.
- People describe it as: "it takes forever to open", "too slow"
- Close to Easing: a long duration with good easing still feels slow.
- Avoid: long animations on things people do many times a day.
- Prompt: "Cut the menu open duration to 200 ms."

### Spring
- Means: motion modelled on a real spring. It's the default in SwiftUI and can be interrupted midway.
- People describe it as: "make it feel physical", "it should follow my finger and settle"
- Close to Bounce: every spring has a bounce setting, and 0 means no overshoot at all.
- Prompt: "Animate the sheet with a spring so it follows my finger and settles naturally."

### Bounce
- Means: how much a spring overshoots before it settles. 0 means none.
- People describe it as: "make it a bit bouncy", "it wobbles too much"
- Close to Spring: the spring is the motion, bounce is one of its settings.
- Avoid: bounce on everyday controls. Save it for small celebrations.
- Prompt: "Use a spring with duration 0.4 and bounce 0.15 for the like button."

### Snappy, smooth, bouncy
- Means: SwiftUI's ready-made springs: a small bounce, no bounce, and more bounce.
- People describe it as: "use the normal iOS feel"
- Close to Bounce: the presets are bounce values picked for you.
- Prompt: "Use .snappy for taps, .smooth for screen changes and .bouncy only for the Watered celebration."

### Interruptible
- Means: an animation you can grab or reverse midway without a jump.
- People describe it as: "it jumps when I tap again", "I can't catch it while it's closing"
- Close to Spring: springs are interruptible by nature, fixed animations usually restart.
- Prompt: "Make the drawer interruptible so I can drag it back while it's closing."

### Transition
- Means: how an element appears or disappears.
- People describe it as: "it just pops in", "make it fade in"
- Close to Morph: a transition brings one thing in or out, a morph turns one thing into another.
- Avoid: scale from zero. Start a scale-in around 0.9 to 0.95, together with a fade.
- Prompt: "Use a fade plus a scale from 0.95 transition when a new plant card appears."

### Morph
- Means: one shape smoothly turning into another. SwiftUI calls it matched geometry.
- People describe it as: "the photo grows into the full screen", "the button turns into the panel"
- Close to Transition: a transition swaps things in and out, a morph keeps it feeling like one thing.
- Prompt: "Morph the plant thumbnail into the hero photo when the details open."

### Stagger
- Means: items animating one after another with a small delay.
- People describe it as: "the rows come in one by one", "a cascade"
- Close to Transition: the transition is how each item enters, stagger is the timing between them.
- Prompt: "Stagger the list rows by 30 ms when the screen loads."

### Scale on press
- Means: a button shrinks a little while you hold it.
- People describe it as: "the button should feel pressable", "it doesn't feel like I tapped it"
- Close to Bounce: scale on press happens while you hold, a bounce happens after.
- Prompt: "Scale buttons to 0.97 on press so they feel tappable."

### Anchor point
- Means: the point an element scales or rotates from.
- People describe it as: "the menu grows from the middle instead of from the button"
- Close to Transition: the transition is the motion, the anchor point is where it grows from.
- Prompt: "Scale the menu from its top right anchor point, where the button is."

### Rubber banding
- Means: the stretchy resistance when you drag past the end.
- People describe it as: "it should stretch a bit when I pull too far"
- Close to Bounce: bounce is overshoot after a release, rubber banding is resistance while you drag.
- Prompt: "Add rubber banding when dragging the sheet above its top detent."

### Symbol effect
- Means: built-in SF Symbol animations like bounce, pulse and replace.
- People describe it as: "animate the icon when it changes", "make the bell wiggle"
- Close to Transition: a transition moves the whole view, a symbol effect animates the icon itself.
- Prompt: "Use the replace symbol effect when the bell switches to bell.slash."

### Reduce Motion
- Means: the iOS setting asking for less movement, which your app should respect.
- People describe it as: "some people get motion sick", "turn off the swooshy stuff"
- Close to Turning animations off: Reduce Motion swaps big movement for fades, so feedback still happens.
- Prompt: "When Reduce Motion is on, swap the slide transitions for cross fades."

**More motion words**
For origin-aware animation, pop in, layout animations, gestures, clip-path, web motion and the rest, use Emil Kowalski's **animation-vocabulary** skill: https://aiforui.dev/skills/animation-vocabulary. This design-vocabulary skill follows his idea, so the two work as a pair. Credit to Emil. 🙌

---

## Anti-patterns, quick list

- **Scale from zero.** Things look like they came from nowhere. Start around 0.9 to 0.95 with a fade. (Emil Kowalski)
- **Ease-in on entering elements.** Feels laggy. Use ease-out.
- **Tap targets under 44 by 44 pt.** People miss them. Grow the hit target, the icon can stay small.
- **Low contrast text on glass or photos.** Aim for at least 4.5:1, use regular glass, a material or a dimming layer behind it.
- **Glass on glass.** Stacking Liquid Glass on Liquid Glass gets muddy. Keep glass for the control layer.
- **Judging glass in the simulator.** It can render differently from a real iPhone. Check on your phone (lesson 3.3).
- **Hard-coded colours in dark mode.** Black text and white backgrounds that don't switch. Use semantic colours.
- **Too many font weights or typefaces.** Two or three weights and one or two typefaces per app.
- **Light font weights at small sizes.** Ultralight, Thin and Light get hard to read small.
- **Fixed text sizes.** They ignore Dynamic Type. Use text styles.
- **A disabled state that looks enabled.** People tap and nothing happens. Make it clearly faded.
- **A full screen spinner for a known layout.** Show a skeleton in the layout's shape.
- **Haptics on every tap.** They stop meaning anything. Save them for moments that matter, and let people switch them off.
- **Controls outside the safe area.** They end up under the Dynamic Island or the home indicator.
- **Same corner radius inside and outside.** Nested shapes look off. Make them concentric.
- **Alerts for good news.** Use a toast or a haptic, keep alerts for decisions.
- **Tabs used as actions.** Tabs switch sections. Put actions like Add in a toolbar.

## Sources

- Apple HIG, Playing haptics: https://developer.apple.com/design/human-interface-guidelines/playing-haptics
- Apple UIKit docs, UIImpactFeedbackGenerator.FeedbackStyle (light, medium, heavy, soft, rigid): https://developer.apple.com/documentation/uikit/uiimpactfeedbackgenerator/feedbackstyle
- Apple HIG, Materials: https://developer.apple.com/design/human-interface-guidelines/materials
- Apple, Meet Liquid Glass (WWDC25): https://developer.apple.com/videos/play/wwdc2025/219/
- Apple SwiftUI docs, ConcentricRectangle: https://developer.apple.com/documentation/swiftui/concentricrectangle
- Apple HIG, Typography: https://developer.apple.com/design/human-interface-guidelines/typography
- Apple HIG, Accessibility (hit targets, contrast): https://developer.apple.com/design/human-interface-guidelines/accessibility
- Apple HIG, Layout: https://developer.apple.com/design/human-interface-guidelines/layout
- Apple HIG, Color and Dark Mode: https://developer.apple.com/design/human-interface-guidelines/color
- Apple HIG, Sheets: https://developer.apple.com/design/human-interface-guidelines/sheets
- Apple HIG, SF Symbols: https://developer.apple.com/design/human-interface-guidelines/sf-symbols
- Apple HIG, Live Activities: https://developer.apple.com/design/human-interface-guidelines/live-activities
- Apple SwiftUI docs, Spring: https://developer.apple.com/documentation/swiftui/spring
- Apple, Animate with springs (WWDC23): https://developer.apple.com/videos/play/wwdc2023/10158/
- Emil Kowalski, animation-vocabulary skill: https://aiforui.dev/skills/animation-vocabulary
- Emil Kowalski, 7 Practical Animation Tips: https://emilkowal.ski/ui/7-practical-animation-tips
- Emil Kowalski, Great Animations: https://emilkowal.ski/ui/great-animations
- Josh Puckett, Interface Craft: https://www.interfacecraft.dev/
