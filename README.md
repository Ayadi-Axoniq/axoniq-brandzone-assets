# Axoniq BrandZone assets

Binary assets for the Axoniq BrandZone site (logos, avatars, backdrops, illustrations and
brand-book reference images). They live in this repository so the site itself stays small and
so the files can be served from a free CDN instead of the site's hosting bandwidth.

Public URL pattern (GitHub raw, CORS enabled, 5 minute cache):

```
https://raw.githubusercontent.com/Ayadi-Axoniq/axoniq-brandzone-assets/main/<path>
```

Example: `https://raw.githubusercontent.com/Ayadi-Axoniq/axoniq-brandzone-assets/main/logos/svg/axoniq-framework-horizontal-original.svg`

Better: enable GitHub Pages on this repository (branch `main`, folder `/`) and the same paths are
served from `https://ayadi-axoniq.github.io/axoniq-brandzone-assets/<path>` through GitHub's CDN
with long-lived caching. One command does it:

```
GH_TOKEN=$(gh auth token --user Ayadi-Axoniq) gh api repos/Ayadi-Axoniq/axoniq-brandzone-assets/pages -X POST -f build_type=legacy -F 'source[branch]=main' -F 'source[path]=/'
```

Then change `ASSET_BASE` in the site's `src/data/assets.ts` to the Pages URL.

jsDelivr (`cdn.jsdelivr.net/gh/...`) does not work for this repository: it refuses GitHub
repositories larger than 50 MB.

## Layout

| Folder | Contents | Source |
|---|---|---|
| `logos/svg/` | 122 logo files, `axoniq-<product>-<layout>-<color>.svg`, plus `manifest.json` | Figma, Brandzone file, "Logos" component set |
| `logos/png/1x/`, `logos/png/4x/` | The same 122 logos as transparent PNG, at the Figma frame size and at 4x for print | Rendered from the SVGs |
| `logos/axoniq-logos.zip` | Every logo as SVG, PNG and PNG 4x, with a README | Built from the folders above |
| `avatars/1024/`, `avatars/512/` | Brand avatars (main and full variants) as PNG | Figma, Brandzone file, Avatars page |
| `backdrops/general/` | General backdrops: the seven riso fields from the Conference 2026 print collateral, `portrait/` 2160x4320, `landscape/` 3840x2160, `web/` previews | Backgrounds, Conference Banners page shader |
| `backdrops/contextual/` | Contextual backdrops: the 60 blog drawings, `full/` 1920x1080 on dark stock, `web/` previews | Backgrounds, framer/ConceptShader.tsx |
| `backdrops/retired/` | The gradient-mesh backdrops retired in October 2026. Do not use in new work | Figma, Brandzone file, Backdrops page |
| `illustrations/isometric/` | Isometric line-art scenes (Gemini), PNG originals and 1400 wide JPEG previews | Figma, Graphics file, Gemini page |
| `illustrations/concepts/` | The six concept illustrations (riso two-ink), light and dark, 3840x2160 JPEG and 1600 wide previews | Backgrounds project, Concepts Final |
| `guides/` | Brand-book slide panels and cropped tiles used as reference figures | Figma, Brandzone file, Book page |

Naming: products are `company`, `platform`, `framework`, `server`, `insights`, `discuss`, `academy`.
Layouts are `icon`, `horizontal`, `vertical-left`, `vertical-center`, `vertical-right`.
Colors are `original`, `original-alt` (full color for dark backgrounds), `white`, `black`.

## Updating

Logos come from Figma; backdrop stills and logo PNGs are rendered with headless Chromium from the
BrandZone site's `/render` route and the SVGs. Replace the files, commit and push. Raw GitHub caches
for about five minutes.
