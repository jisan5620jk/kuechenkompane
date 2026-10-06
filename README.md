# Küchenkompane – Shopify Theme

Custom Shopify Online Store 2.0 theme for the Küchenkompane store, built on **Minimog – OS 2.0 (v5.5.0)** with store-specific sections for the Apex product line, B2B, sales campaigns and mystery boxes.

## Requirements

- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli) (`npm install -g @shopify/cli @shopify/theme`)
- Staff or collaborator access to the `fiew-kitchen` store

## Local development

```bash
# Log in and start a local preview with hot reload
shopify theme dev --store fiew-kitchen
```

The CLI prints a local preview URL (usually `http://127.0.0.1:9292`) and a theme editor link.

## Common commands

```bash
# Pull the latest theme files (including merchant changes in the editor)
shopify theme pull --store fiew-kitchen

# Push local changes to a theme (pick it from the list)
shopify theme push --store fiew-kitchen

# Push as a new unpublished theme for review
shopify theme push --store fiew-kitchen --unpublished

# Lint Liquid and theme files
shopify theme check
```

> Always `pull` before you start working. `config/settings_data.json` and the `templates/*.json` files are also changed from the Shopify theme editor, and pushing an old copy overwrites those changes.

## Project structure

| Folder       | Contents |
|--------------|----------|
| `assets/`    | CSS, JavaScript, images and fonts |
| `blocks/`    | Theme blocks (`_fertigung-*`, `_kk-*`, `_private-label-*`, `_prozess-step`) |
| `config/`    | `settings_schema.json` (theme settings) and `settings_data.json` (saved values) |
| `layout/`    | `theme.liquid`, the main page wrapper |
| `locales/`   | Translation files (`de.json`, `en.default.json`, …) |
| `sections/`  | Page sections that can be added in the theme editor |
| `snippets/`  | Reusable Liquid partials |
| `templates/` | JSON / Liquid templates for products, collections, pages, cart, blog and customer accounts |
| `.shopify/`  | Metafield definitions used by the CLI |

## Section naming

| Prefix | Used for |
|--------|----------|
| `apex-*` | Apex product line pages and components |
| `akta-*` | Custom collection / product grid sections |
| `b2b-*` | B2B landing page (`templates/page.b2b-page.json`) |
| `kk-*` | Küchenkompane sale, offer and landing page sections |
| `black-friday-*` | Black Friday campaign |
| `PDP-V1-*` | Product detail page (v1) feature sections |

## Templates

Products and collections use alternate templates for specific campaigns, for example:

- `product.apex-*` – Apex product pages (Damast, Messersets, bundles, cooperations)
- `product.mystery-box-*`, `collection.mystery-box-*` – Mystery box offers
- `product.three-product-*` – Three-product bundle layouts
- `collection.apex-sale*`, `collection.kk-warehouse-clearance` – Sale and clearance collections
- `page.b2b-page`, `page.widerruf`, `page.bonuspunkte` – Custom pages

Assign a template to a product, collection or page in the Shopify admin under **Theme template**.

## Workflow

1. `shopify theme pull` to get the latest files.
2. Make changes and test them with `shopify theme dev`.
3. Run `shopify theme check`.
4. Push to an unpublished theme and review it before publishing to the live theme.
5. Commit your changes to git.
