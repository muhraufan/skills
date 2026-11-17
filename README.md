# Raufan's skills

Agent skills I wrote while designing and shipping my own apps with AI. Install them, and your AI works the way I do.

Made alongside [The Weekend Project](https://theweekendproject.club), my course on designing and shipping a delightful app with AI, one weekend at a time.

## Install

All of them:

```bash
npx skills@latest add muhraufan/skills
```

Just one:

```bash
npx skills@latest add muhraufan/skills --skill design-vocabulary
npx skills@latest add muhraufan/skills --skill tidy-ui
```

They work with Claude Code, Codex, Cursor and other agents that read `SKILL.md` files. No terminal? Copy the skill's `SKILL.md` into your AI tool's instructions.

## Skills

### design-vocabulary

Find the exact design word for what you see, so your AI builds what you meant on the first try.

Describe it the way you'd tell a friend, or paste a screenshot:

```
/design-vocabulary the cards feel cramped and the title gets lost
```

You get the exact term, how it differs from the word people mix it up with, anything to avoid, and a prompt to paste with real values. 116 terms across spacing, type, colour, layout, components, iOS surfaces and Liquid Glass, haptics, and the core of iOS motion.

### tidy-ui

Bring one screen up to a clean, honest minimum, even if you're not a designer.

```
/tidy-ui the home screen
```

It checks 12 basics (spacing rhythm, alignment, hierarchy, sizing, fonts, contrast, AI-default colours, radius, depth, consistency, light and dark mode), fixes what fails with the smallest change, and reports every change with its design word. It spots the default AI looks and swaps them, and recommends a good free font when the screen needs one. Works on iOS, Android and the web. Add `audit` to only list problems, or `keep my colours` to keep your palette.

Use it with design-vocabulary: that one names what's wrong, tidy-ui fixes it.

## Credits

design-vocabulary follows the idea of Emil Kowalski's [animation-vocabulary](https://aiforui.dev/skills/animation-vocabulary) skill, and points to it for motion. Use the two as a pair. 🙌

## License

MIT
