# fontfyi-embed

[![npm](https://img.shields.io/npm/v/fontfyi-embed)](https://www.npmjs.com/package/fontfyi-embed)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/fontfyi-embed)
[![Size](https://img.shields.io/badge/size-~11--21KB_gzipped-green)](https://bundlephobia.com/package/fontfyi-embed)

Embed **FontFYI** widgets — fonts, glossary terms, interactive tools, and inline elements — on any website. **9 widget types**, zero dependencies, Shadow DOM style isolation, 4 built-in themes (light, dark, sepia, auto), 2 styles (modern, minimal), and live data from the [FontFYI](https://fontfyi.com) database.

Every widget includes a "Powered by FontFYI" backlink directing readers to the full reference.

> **Try the interactive widget builder at [widget.fontfyi.com](https://widget.fontfyi.com)**

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-fontfyi="entity" data-slug="fonts" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

That's it. The widget fetches data from the FontFYI API and renders with full style isolation.

## Widget Types

| Type | Usage | Description |
|------|-------|-------------|
| `entity` | `<div data-fontfyi="entity" data-slug="..."></div>` | Entity detail card — color, font, emoji, symbol, or character |
| `glossary` | `<div data-fontfyi="glossary" data-slug="..."></div>` | Glossary term definition with cross-references |
| `guide` | `<div data-fontfyi="guide" data-slug="..."></div>` | Guide summary card with key takeaways |
| `compare` | `<div data-fontfyi="compare" data-slug="..."></div>` | Side-by-side entity comparison |
| `search` | `<div data-fontfyi="search" data-slug="..."></div>` | Search box linking to the full database |
| `preview` | `<div data-fontfyi="preview" data-slug="..."></div>` | Live font preview — loads actual Google Font |
| `stack` | `<div data-fontfyi="stack" data-slug="..."></div>` | CSS font-stack generator with system fallbacks |
| `font-name` | `<div data-fontfyi="font-name" data-slug="..."></div>` | Inline font name — renders in actual font |
| `tooltip` | `<div data-fontfyi="tooltip" data-slug="..."></div>` | Glossary tooltip — hover/click shows term definition inline |

## Widget Options

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-fontfyi` | entity, compare, glossary, guide, search, tooltip, [tools] | required | Widget type |
| `data-slug` | e.g. "fonts" | — | Entity slug from the FontFYI database |
| `data-theme` | light, dark, sepia, auto | light | Visual theme (`auto` follows OS preference) |
| `data-styleVariant` | modern, minimal | modern | Widget design style |
| `data-size` | default, compact, large | default | Widget size |
| `data-placeholder` | any string | "Search Fonts..." | Search box placeholder |

## Themes

```html
<!-- Light (default) -->
<div data-fontfyi="entity" data-slug="fonts" data-theme="light"></div>

<!-- Dark -->
<div data-fontfyi="entity" data-slug="fonts" data-theme="dark"></div>

<!-- Sepia -->
<div data-fontfyi="entity" data-slug="fonts" data-theme="sepia"></div>

<!-- Auto — follows OS dark/light preference -->
<div data-fontfyi="entity" data-slug="fonts" data-theme="auto"></div>
```

## Styles

```html
<!-- Modern (default) — clean lines, rounded corners, accent gradients -->
<div data-fontfyi="entity" data-slug="fonts" data-styleVariant="modern"></div>

<!-- Minimal — subtle borders, flat design, no gradients -->
<div data-fontfyi="entity" data-slug="fonts" data-styleVariant="minimal"></div>
```

## Web Components (Custom Elements)

As an alternative to `data-*` attributes, you can use native HTML custom elements:

```html
<!-- Custom element form -->
<fontfyi-entity slug="fonts" theme="light"></fontfyi-entity>
<fontfyi-compare slugs="fonts,other-slug"></fontfyi-compare>
<fontfyi-search placeholder="Search Fonts..."></fontfyi-search>

<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

Use `style-variant` (not `style`) to avoid conflicts with the HTML reserved `style` attribute.

## Examples

### Entity Card

```html
<div data-fontfyi="entity" data-slug="fonts" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

### Side-by-Side Comparison

```html
<div data-fontfyi="compare" data-slugs="fonts,other-slug"></div>
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

### Search Box

```html
<div data-fontfyi="search" data-placeholder="Search Fonts..."></div>
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

### Glossary Term

```html
<div data-fontfyi="glossary" data-slug="example-term" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1/dist/embed.min.js"></script>
```

### Specific version (production stability)

```html
<script src="https://cdn.jsdelivr.net/npm/fontfyi-embed@1.0.0/dist/embed.min.js"></script>
```

### npm (for bundlers)

```bash
npm install fontfyi-embed
```

```javascript
import 'fontfyi-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site
- **Zero dependencies**: No jQuery, React, or any external library
- **2 styles**: Modern (accent gradients) and Minimal (flat design)
- **4 themes**: Light, Dark, Sepia, Auto (OS preference detection)
- **CORS**: FontFYI API has CORS enabled for all origins
- **MutationObserver**: Works with dynamically added elements (SPAs)
- **IntersectionObserver**: Lazy loading — widgets only fetch when entering viewport (200px margin)
- **Rich Snippets**: DefinedTerm JSON-LD injected for glossary widgets
- **Bundle size**: ~11-21KB gzipped (per-site build — only includes tools available on FontFYI)

## Learn More About Fonts

Visit [fontfyi.com](https://fontfyi.com) — FontFYI is a comprehensive fonts reference with interactive tools, guides, and developer resources.

- **API docs**: [fontfyi.com/developers/](https://fontfyi.com/developers/)
- **Widget builder**: [widget.fontfyi.com](https://widget.fontfyi.com)
- **npm package**: [npmjs.com/package/fontfyi-embed](https://www.npmjs.com/package/fontfyi-embed)
- **GitHub**: [github.com/fyipedia/fontfyi-embed](https://github.com/fyipedia/fontfyi-embed)

## Creative FYI Family

Part of [FYIPedia](https://fyipedia.com) — open-source developer tools ecosystem. Creative FYI covers design, typography, characters, and visual encoding.

| Site | Domain | Focus | Package |
|------|--------|-------|---------|
| ColorFYI | [colorfyi.com](https://colorfyi.com) | Color conversion, WCAG contrast, harmonies — 16.7M hex colors | [npm](https://www.npmjs.com/package/colorfyi-embed) |
| **FontFYI** | [fontfyi.com](https://fontfyi.com) | Google Fonts metadata, CSS generation, font pairings | **[npm](https://www.npmjs.com/package/fontfyi-embed)** |
| EmojiFYI | [emojifyi.com](https://emojifyi.com) | 3,781 emojis, Unicode Emoji 16.0, 8 encodings | [npm](https://www.npmjs.com/package/emojifyi-embed) |
| SymbolFYI | [symbolfyi.com](https://symbolfyi.com) | Symbol encoding in 11 formats, Unicode properties | [npm](https://www.npmjs.com/package/symbolfyi-embed) |
| UnicodeFYI | [unicodefyi.com](https://unicodefyi.com) | Unicode characters, 17 encodings, text analysis | [npm](https://www.npmjs.com/package/unicodefyi-embed) |

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [FYIPedia](https://fyipedia.com).
