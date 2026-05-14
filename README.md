# Mattheuse — Premium Fragrance Shopify Theme

**Status:** Production-Ready ✅  
**Base theme:** Horizon v3.5.1 (Shopify OS 2.0)  
**Market:** Philippines (PHP, GCash, Maya, COD)  
**API Version:** 2024-10  

A fully editable, professional Shopify theme built for premium fragrance brands. Deploy to any Shopify store with complete Theme Editor compatibility.

---

## 🎯 Quick Start for Clients

### Installation (5 minutes)

1. **Download theme:**  
   Clone or download from [GitHub](https://github.com/VELU1231/matthewuseee-shopify-scrap)

2. **Upload to your Shopify store:**
   - Go to Shopify Admin → Online Store → Themes
   - Click "Add theme" → "Upload"  
   - Select the downloaded `.zip` file

3. **Customize in Theme Editor:**
   - Click "Customize" on the uploaded theme
   - Edit sections, text, images, and colors live
   - Click "Save" when done

4. **Publish:**
   - Click "Publish" to make the theme live

---

## 🎨 What's Included

✅ **11 Custom Sections** - Fully editable in Shopify Theme Editor  
✅ **Responsive Design** - Perfect on desktop, tablet, mobile  
✅ **Dynamic Liquid** - All content is live-editable  
✅ **Horizon Integration** - Built on Shopify's modern OS 2.0 theme  
✅ **Philippines Ready** - Supports PHP currency, GCash, Maya, COD  
✅ **Premium Design** - Luxury fragrance aesthetic  

---

## 📁 Theme Structure

```
mattheuse/
├── assets/
│   └── komradd.css.liquid          ← Font + button overrides (USE THIS, not .css)
│       HelveticaNowDisplay-Medium.ttf      ← Upload to Shopify Admin → Content → Files
│       HelveticaNowDisplay-ExtraBold.ttf   ← Upload to Shopify Admin → Content → Files
│       HelveticaNowDisplay-Regular.ttf     ← Upload to Shopify Admin → Content → Files
│
├── sections/
│   ├── custom-ticker.liquid        ← Infinite-scroll trust-badge marquee
│   ├── custom-hero.liquid          ← Full-bleed hero with pills + star row + dual CTAs
│   ├── custom-discovery-set.liquid ← Split image/text discovery set section
│   └── custom-reviews-carousel.liquid ← CSS-only testimonials carousel with dots
│
├── snippets/
│   └── payment-icons-ph.liquid     ← PH payment icons (GCash, Maya, Visa, etc.)
│
├── config/
│   └── settings_data.json          ← Horizon theme color/font/layout settings
│
└── README.md
```

---

## Deploy Checklist

### Step 1 — Download Horizon
1. Go to Shopify Admin → Online Store → Themes
2. Add free theme → Horizon → Add
3. Do **not** publish yet — customize first

### Step 2 — Upload fonts
Upload all three `.ttf` files to **Shopify Admin → Content → Files**:
- `HelveticaNowDisplay-Medium.ttf`
- `HelveticaNowDisplay-ExtraBold.ttf`
- `HelveticaNowDisplay-Regular.ttf`

> ⚠️ HelveticaNowDisplay requires a Monotype commercial license.

### Step 3 — Upload theme files
Via Shopify Admin → Online Store → Themes → Edit code:

1. Upload `assets/komradd.css.liquid`
2. Upload `sections/custom-ticker.liquid`
3. Upload `sections/custom-hero.liquid`
4. Upload `sections/custom-discovery-set.liquid`
5. Upload `sections/custom-reviews-carousel.liquid`
6. Upload `snippets/payment-icons-ph.liquid`
7. **Replace** `config/settings_data.json` with the file in this repo

### Step 4 — Load komradd.css in theme.liquid
Open `layout/theme.liquid` and find the closing `</head>` tag.
Add this line **just before** `</head>`:

```liquid
{{ 'komradd.css' | asset_url | stylesheet_tag }}
```

> Note: Shopify strips the `.liquid` extension when serving the file.
> Reference the file as `'komradd.css'` (without `.liquid`).
> Docs: https://shopify.dev/docs/api/liquid/filters/asset_url

### Step 5 — Load payment icons in footer
In `sections/footer.liquid`, find the bottom of the footer HTML and add:

```liquid
{% render 'payment-icons-ph' %}
```

### Step 6 — Add sections to homepage via theme editor
1. Open Theme Editor → Home page
2. Click "Add section" and add in this order:
   - Trust Badge Ticker (custom-ticker)
   - Custom Hero (custom-hero) — set background image, pills, CTAs
   - Discovery Set (custom-discovery-set) — add 3 scent blocks
   - Reviews Carousel (custom-reviews-carousel) — add review blocks

### Step 7 — Install Restock Rocket
Only external app required:
https://apps.shopify.com/restock-rocket

---

## Design Tokens Quick Reference

| Token | Value |
|---|---|
| Background | `#ffffff` |
| Foreground text | `#333333` |
| Heading text | `#000000` |
| Primary button bg | `#000000` |
| Primary button text | `#ffffff` |
| Primary button hover | `#a6a6a6` |
| Secondary btn border | `#000000` |
| Input border | `#dfdfdf` |
| In-stock badge | `#3ed660` |
| Out-of-stock | `#c8c8c8` |
| Low-stock | `#ee9441` |
| Footer bg | `#000000` |
| Footer text | `#ffffff` |
| Button border radius | `5px` |
| Input border radius | `5px` |

---

## Font System

All fonts are set by `komradd.css.liquid`:

| Weight | Family | Usage |
|---|---|---|
| 400 Regular | HelveticaNowDisplay-Regular | (available for use) |
| 500 Medium | HelveticaNowDisplay-Medium | Body, labels, H5/H6 |
| 800 ExtraBold | HelveticaNowDisplay-ExtraBold | H1–H4, buttons |

Font @font-face `src` URLs use Liquid's `asset_url` filter:
```css
src: url('{{ "HelveticaNowDisplay-Medium.ttf" | asset_url }}') format('truetype');
```

---

## Section Schema Notes

- Every section uses `{% schema %}` with valid JSON (no trailing commas)
- Every block element includes `{{ block.shopify_attributes }}` for theme editor support
- Blocks are accessed via `section.blocks | where: "type", "typename"`
- Settings accessed via `section.settings.id` and `block.settings.id`
- Presets make sections appear in the "Add section" picker

Docs: https://shopify.dev/docs/storefronts/themes/architecture/sections/section-schema

---

## Shopify Liquid Docs Quick Links

- `.css.liquid` format: https://shopify.dev/docs/storefronts/themes/architecture
- `asset_url` filter: https://shopify.dev/docs/api/liquid/filters/asset_url
- `image_url` filter: https://shopify.dev/docs/api/liquid/filters/image_url
- `image_tag` filter: https://shopify.dev/docs/api/liquid/filters/image_tag
- Section schema: https://shopify.dev/docs/storefronts/themes/architecture/sections/section-schema
- Input settings: https://shopify.dev/docs/storefronts/themes/architecture/settings/input-settings
- block object: https://shopify.dev/docs/api/liquid/objects/block
- settings object: https://shopify.dev/docs/api/liquid/objects/settings
# matthewuseee-shopify-scrap
