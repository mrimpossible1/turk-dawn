# Turk Labs · Dawn theme customization

This is a fork of [Shopify/dawn](https://github.com/Shopify/dawn) styled as the **Turk Labs Research Division** brand — vintage manual + clinical research aesthetic.

> Born in the Lab. Forged in Iron.

## What's been changed

All Turk Labs additions are prefixed `tl-` so they're easy to spot vs. upstream Dawn.

### Added files
- `assets/turklabs.css` — the brand override stylesheet (loaded after `base.css`)
- `snippets/tl-defs.liquid` — shared SVG `<defs>` (paper grain, distressed-edge filter, hatch pattern)
- `snippets/tl-hex-seal.liquid` — hex research seal (LAB · MMXXVI · N°47, star + barbell)
- `snippets/tl-circle-stamp.liquid` — round QC stamp
- `snippets/tl-rect-stamp.liquid` — rectangular "TESTED · APPROVED" stamp
- `snippets/tl-lab-tag.liquid` — boxed lab-report price tag (drop into product cards/PDP)
- `snippets/tl-anatomy-plate.liquid` — anatomical figure plate (hero element)

### Modified files
- `layout/theme.liquid` — loads `turklabs.css` + Google Fonts (Oswald, Roboto Slab, JetBrains Mono); renders `tl-defs` once at body open
- `config/settings_data.json` — overrides default colors, fonts, button radius, layout density
- `sections/footer.liquid` — adds tagline row at the bottom (`© TURK LABS · ★ RESEARCH DIVISION · BORN IN THE LAB · FORGED IN IRON`)

### Untouched
- `sections/announcement-bar.liquid` — kept stock; styling driven entirely from `turklabs.css` (so Dawn's localization, social, single/multi-block features all keep working). The "★" prefix and "★ BORN IN THE LAB · FORGED IN IRON" suffix are appended via `::before` / `::after`.
- `sections/header.liquid` — kept stock; styled via CSS only (logo treatment, mono nav, ★ separator between menu items).

## Using the snippets in your theme

In any section or template:

```liquid
{% render 'tl-hex-seal', size: 110 %}
{% render 'tl-circle-stamp', label: 'QUALITY CONTROL', size: 90 %}
{% render 'tl-rect-stamp', label: 'TESTED' %}
{% render 'tl-lab-tag', title: 'TURKESTERONE', subtitle: '500MG · 60 CAPSULES', price: '$49.99', sale_price: '$39.99' %}
{% render 'tl-anatomy-plate', figure: 'torso' %}
```

## Connecting to Shopify

1. **Online Store → Themes → Add theme → Connect from GitHub**
2. Pick `mrimpossible1/turk-dawn`, branch `main`
3. Pushes to `main` deploy automatically

## Pulling Dawn updates

```bash
git remote add upstream https://github.com/Shopify/dawn.git
git fetch upstream
git merge upstream/main
```

Conflicts will land in `layout/theme.liquid`, `sections/footer.liquid`, and `config/settings_data.json` — easy to resolve since the Turk Labs additions are clearly marked.

## Local preview

The HTML mockup at `system.html` (root of this project) shows the full design system applied to a Dawn-shaped page. Use it as the visual reference for what the theme will look like once installed.
