---
name: landing-page
description: Scaffold a new static website or landing page using plain HTML, CSS, and JavaScript (no build step). Use when the user asks to create, scaffold, or start a new website, landing page, or static site.
---

# Landing Page Skill

Scaffolds a static website using plain HTML, CSS, and JavaScript — no framework, no build step, no bundler. Output should run by opening `index.html` directly in a browser or serving the folder as-is.

## When to use

Invoke this skill when the user asks to create, scaffold, or start a new website or landing page, and hasn't asked for a specific framework (React, Next.js, etc.). If they ask for a framework instead, don't use this skill — build with that framework directly.

## Steps

1. **Always ask for project details before scaffolding anything.** Never guess placeholder content. Use AskUserQuestion (or plain questions if that tool isn't available) to gather, at minimum:
   - What the site/business is for (name, purpose, industry)
   - Target audience or goal of the page (e.g. sell a product, collect leads, portfolio, info only)
   - Sections/pages needed (e.g. hero, about, services, testimonials, contact, pricing)
   - Any branding constraints (colors, fonts, existing logo/assets, tone/voice)
   - Key calls-to-action (e.g. "Book a call", "Sign up", "Buy now") and where they should link
   Don't ask about tech stack (it's always plain HTML/CSS/JS) or file layout (defined below) — those are fixed by this skill.
2. **Pick a design direction before writing any code.** Based on the industry/tone gathered in step 1, choose and briefly state:
   - A **named UI style** to commit to (e.g. minimalism, bento grid, soft neumorphism, glassmorphism, editorial/brutalist, warm organic) — pick one that fits the industry and audience rather than blending several.
   - A **color palette** (3–5 colors: primary, accent, neutral, background, text) that fits the chosen style and brand constraints.
   - A **font pairing** (one display/heading font + one body font) that fits the tone — corporate/trustworthy, playful, luxury, technical, etc.
   State the choice in a sentence before scaffolding so it stays consistent across every file, instead of drifting section to section.
3. **Create the standard structure** in the project root (or a subfolder if the user names one):
   ```
   index.html
   /css/style.css
   /js/main.js
   /assets/            (images, fonts, etc. — only if needed)
   ```
4. **Write semantic, accessible HTML** in `index.html`: proper landmarks (`header`, `main`, `nav`, `footer`, `section`), meaningful `alt` text, a real `<title>` and meta description. Link `css/style.css` and `js/main.js` from it.
5. **Write CSS in `css/style.css`** implementing the design direction from step 2 to a high visual bar — this should look like a polished, modern, professionally designed site, not a generic template. Apply:
   - The chosen type scale and font pairing — never default browser serif/sans with no scale.
   - The chosen color palette expressed as CSS custom properties (primary/secondary/accent/neutral/background), with real contrast and a considered light/dark balance.
   - Generous, consistent spacing (a spacing scale, not ad-hoc pixel values), clear visual hierarchy, and whitespace that gives sections room to breathe.
   - Subtle polish consistent with the chosen style: smooth hover/focus transitions, rounded corners or shadows used consistently (not everywhere), a hero section with real visual weight.
   - Mobile-first responsive layout (flexbox/grid) that holds up at mobile, tablet, and desktop widths.
   - No external CSS framework unless the user asks for one.
6. **Write JS in `js/main.js`** only for actual interactivity the page needs (nav toggle, form handling, smooth scroll, subtle scroll-triggered reveals). Don't add JS for things CSS can do alone.
7. **No build tooling** — no `package.json`, no bundler config, no npm install step — unless the user explicitly asks for one later.
8. **Self-review against interface guidelines** before calling it done. Fetch the current rules from `https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md` and check the page against the ones that apply to a static HTML/CSS/JS site (translate any Tailwind-specific class names in that doc to plain-CSS equivalents — the underlying rule is what matters, not the utility class). At minimum, verify:
   - **Accessibility**: real `<button>`/`<a>` elements (not `<div onclick>`), visible `:focus-visible` outlines on every interactive element, `aria-label` on icon-only buttons, `alt` text on all images, labels tied to every form input.
   - **Typography**: a real type scale, `text-wrap: balance` (or similar) on headings so they don't widow, curly quotes/proper ellipsis in copy, no orphaned single words in headlines.
   - **Forms** (if any): correct `type`/`inputmode`/`autocomplete` on fields, clickable `<label>`s, spellcheck disabled on fields like emails.
   - **Animation**: only animate `transform`/`opacity`, list transitioned properties explicitly (never `transition: all`), wrap non-essential motion in `@media (prefers-reduced-motion: reduce)`.
   - **Color/contrast**: hover/active/focus states visibly increase contrast, not just shift hue slightly; set `color-scheme` if dark mode is supported.
   - **Performance/layout**: explicit `width`/`height` (or `aspect-ratio`) on images to prevent layout shift; long text truncates gracefully instead of overflowing.
9. **Verify it works**: open `index.html` in a browser (or note how to) and confirm the page renders cleanly at mobile and desktop widths and any interactive elements function, per the project's UI-testing expectations.

## Design reference: 21st.dev

21st.dev (https://21st.dev) is a gallery of modern UI component designs. Its MCP server ("Magic MCP") generates React/Tailwind/shadcn component code — it is **not** connected in this environment and wouldn't fit this skill's plain HTML/CSS/JS output even if it were, so don't attempt to call it as a live tool.

Instead, use 21st.dev as a **visual reference only**: when picking layout patterns, hero styles, or section designs, model the polish and composition you see in well-regarded 21st.dev components (spacing, type hierarchy, color use, hover states), then hand-write equivalent plain HTML/CSS/JS — don't copy React/JSX or Tailwind class strings verbatim.

## Conventions

- Keep the three files (`index.html`, `style.css`, `main.js`) as the core skeleton for every page added; additional pages follow the same pattern (`about.html`, `contact.html`, ...) each linking the shared `css/style.css` and `js/main.js`.
- Prefer real content over lorem ipsum placeholders when the user has described what the site is for.
- Don't add comments explaining what HTML/CSS/JS does — well-named classes and semantic tags already communicate that.
