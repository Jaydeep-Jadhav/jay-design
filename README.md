# Jay's Portfolio — Site Package

Personal portfolio for Jay, Product Designer. Built on the Open Design token system with a custom accent layer.

## Structure

```
jay-portfolio/
├── index.html      Homepage: hero, case studies, AI teaser, writing, playground, about, contact
├── ai.html         Designing with AI: the delegated vs defended ledger, workflow, receipts, stack
├── onroute.html    Onroute case study: 4-platform self-service ecosystem
├── assets/
│   └── images/     (empty) Drop localized images here, see "Image localization" below
└── README.md
```

Every page is fully self-contained (HTML + CSS + JS in one file). No build step, no dependencies beyond Google Fonts. Drag the folder into Netlify, Vercel, GitHub Pages, or any static host and it works.

## Design system

Source: Open Design token spec (open-design.ai theme).

| Token group | Values |
|---|---|
| Font | Albert Sans (Google Fonts), base 16px |
| Text | primary `#262626`, secondary `#595959`, inverse `#ffffff` |
| Surfaces | page `#ffffff`, muted `#fafafa`, base `#000000` |
| Accent | `#62FD15` (decorative + dark surfaces only, never body text on white) |
| Case color | Onroute indigo `#323A93` (case-study-scoped, each case brings its own) |
| Radii | 6 / 13 / 18 / 50 / 999px |
| Motion | 140–900ms, ease `cubic-bezier(0.22, 1, 0.36, 1)` |

Signature decor elements: blueprint dot grid, top/left rulers, crop marks, 61.8% golden ratio guide, golden spiral (homepage), Figma-style selection frame with handles (homepage H1), floating multiplayer cursor chips.

Accessibility baked in: WCAG-conscious contrast, focus-visible outlines, skip links, keyboard-reachable interactive elements, 44px minimum touch targets, `prefers-reduced-motion` support, semantic landmarks and aria labels.

## Before you publish: checklist

- [ ] Replace `hello@example.com` with your real email (index.html, ai.html)
- [ ] Add real LinkedIn / Dribbble URLs (all three footers + contact section)
- [ ] Link your resume PDF (hero button + contact + footer on index.html)
- [ ] Replace Case Study 2 and Case Study 3 placeholder cards on index.html
- [ ] Point the Writing list items to real blog posts (or remove until ready)
- [ ] Point the Playground tiles to real experiments
- [ ] On ai.html, link the three "receipts" cards to their destinations
- [ ] Verify all Onroute metrics are ones you can defend in an interview

## Image localization (important)

`onroute.html` currently hotlinks UI screens from framerusercontent.com (your existing Framer site). This works while that site is up. Before taking Framer down:

1. Download each image (URLs are in the `<img>` tags in onroute.html)
2. Save them to `assets/images/` with clear names, e.g. `onroute-banner.png`, `onroute-customer.png`, `onroute-ops-1.png`
3. Update the `src` attributes to relative paths, e.g. `assets/images/onroute-banner.png`
4. Consider compressing to WebP (the source PNGs are very large, 4000px+ wide)

## Conventions for new pages

1. Copy an existing page as the starting point, tokens and nav/footer come along free
2. Keep green (`--accent`) site-level: kickers, highlights, hover states, dark-surface text
3. Give each case study its own scoped brand color variable (see `--onroute`)
4. Nav: set `aria-current="page"` on the active link
5. Reuse `.reveal` (load) and `.scroll-reveal` (scroll) animation classes
6. Never use `--accent` as text color on white backgrounds (contrast ~1.9:1, fails WCAG)
