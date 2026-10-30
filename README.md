# Axoniq BrandZone assets

Binary assets for the Axoniq BrandZone site (logos, avatars, backdrops, illustrations and
brand-book reference images). They live in this repository so the site itself stays small and
so the files can be served from a free CDN instead of the site's hosting bandwidth.

Public URL pattern (jsDelivr in front of GitHub, cached worldwide):

```
https://cdn.jsdelivr.net/gh/Ayadi-Axoniq/axoniq-brandzone-assets@main/<path>
```

Example: `https://cdn.jsdelivr.net/gh/Ayadi-Axoniq/axoniq-brandzone-assets@main/logos/svg/axoniq-framework-horizontal-original.svg`

jsDelivr caches a branch reference for up to 12 hours. After replacing a file, either wait, or
purge it at `https://purge.jsdelivr.net/gh/Ayadi-Axoniq/axoniq-brandzone-assets@main/<path>`.

## Layout

| Folder | Contents | Source |
|---|---|---|
| `logos/svg/` | 122 logo files, `axoniq-<product>-<layout>-<color>.svg`, plus `manifest.json` | Figma, Brandzone file, "Logos" component set |
| `avatars/1024/`, `avatars/512/` | Brand avatars (main and full variants) as PNG | Figma, Brandzone file, Avatars page |
| `backdrops/full/`, `backdrops/web/` | Gradient-mesh backdrops, 1920x1200 JPEG (full) and 1600 wide (web) | Figma, Brandzone file, Backdrops page |
| `illustrations/isometric/` | Isometric line-art scenes (Gemini), PNG originals and 1400 wide JPEG previews | Figma, Graphics file, Gemini page |
| `illustrations/concepts/` | The six concept illustrations (riso two-ink), light and dark, 3840x2160 JPEG and 1600 wide previews | Backgrounds project, Concepts Final |
| `guides/` | Brand-book slide panels used as reference figures | Figma, Brandzone file, Book page |

Naming: products are `company`, `platform`, `framework`, `server`, `insights`, `discuss`, `academy`.
Layouts are `icon`, `horizontal`, `vertical-left`, `vertical-center`, `vertical-right`.
Colors are `original`, `original-alt` (full color for dark backgrounds), `white`, `black`.

## Updating

Regenerate from the Figma sources, replace the files, commit, push, purge the changed paths.
Keep single files under 20 MB (jsDelivr's per-file limit).
