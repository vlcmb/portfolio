# vlacombe.cloud — personal site

Live at **<https://vlacombe.cloud>**.

`public/` in this repository is the **deployed site, byte for byte** — exactly
what Caddy serves. It is the authoritative copy.

## ⚠️ `public/` is hand-edited — do not regenerate it

The site was originally generated with [Hugo](https://gohugo.io) and the
[Toha](https://github.com/hugo-toha/toha) theme. That source is preserved on
the [`hugo-source`](../../tree/hugo-source) branch.

A number of changes were then made **directly in `public/`** and have never
been back-ported to the Hugo templates:

- page title, meta description, canonical URLs
- `robots.txt` and a real `sitemap.xml`
- `noindex,follow` on the section pages that have no content yet
- Open Graph tags, Twitter card, JSON-LD `Person` schema
- navbar logo and favicon (`VL` monogram, SVG)
- avatar (square-cropped headshot — the theme box is a hard 148×148 with no
  `object-fit`, so a portrait source gets squashed)
- contact links, and the project cards

**Running `hugo` from the `hugo-source` branch would silently undo all of it.**
Until those edits are ported back into the templates and config, `public/` is
the only reference version.

## Deploying

Static files — no build step, no service to restart:

```bash
cd public
rsync -rlptvz --chmod=D755,F644 ./ root@<host>:/opt/portfolio/public/
```

Host, Caddy configuration, pre-flight checksum diff and troubleshooting are in
`DEPLOIEMENT.md`, kept outside this repository on purpose.
