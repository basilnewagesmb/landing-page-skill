# landing-page skill

A [Claude Code](https://claude.com/claude-code) skill that scaffolds polished, modern static websites using plain HTML, CSS, and JavaScript — no framework, no build step, no bundler.

## What it does

When invoked, this skill:

1. Asks for project details (site purpose, audience, sections, branding, calls-to-action) instead of guessing content.
2. Picks a deliberate design direction — a named UI style, color palette, and font pairing — before writing any code.
3. Scaffolds a standard `index.html` / `css/style.css` / `js/main.js` structure with semantic, accessible markup.
4. Writes CSS to a high visual bar: real type scale, cohesive palette as CSS custom properties, consistent spacing, responsive layout.
5. Self-reviews the result against [Vercel's Web Interface Guidelines](https://github.com/vercel-labs/web-interface-guidelines) (accessibility, typography, forms, animation, contrast, performance), adapted to plain CSS.

The output runs by opening `index.html` directly in a browser — no `npm install`, no config.

## Install

Copy the skill folder into your project (or your personal skills directory):

```bash
# Project-scoped — only active in this repo
git clone https://github.com/basilnewagesmb/landing-page-skill.git
cp -r landing-page-skill/.claude/skills/landing-page <your-project>/.claude/skills/

# Personal — active in every Claude Code session
cp -r landing-page-skill/.claude/skills/landing-page ~/.claude/skills/
```

## Usage

In Claude Code, just ask to create, scaffold, or start a new website or landing page. The skill activates automatically based on its description and walks through the steps above.

## License

MIT — see [LICENSE](LICENSE).
