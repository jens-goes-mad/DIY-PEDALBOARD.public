# documentation-github-page

Public build-log site for the DIY MIDI Music Workstation Pedal Board project. Built with
[Hugo](https://gohugo.io/) and the [Stack theme](https://github.com/CaiJimmy/hugo-theme-stack),
deployed to GitHub Pages via `../.github/workflows/hugo.yml` on every push to `main`.

This is a straight copy of the existing `diy-pedalboard` site content, retargeted from its
custom domain (`diy-pedalboard.de`) to a GitHub Pages project URL, with three fixes applied
for that subpath (the original content assumed a root-domain `baseurl`):

- `layouts/index.html`: homepage redirect now builds its target from `Site.BaseURL` instead of
  a hardcoded `/overview`.
- `layouts/_default/baseof.html`: the `accordion.css` stylesheet link now does the same.
- `config/_default/config.toml`: `canonifyURLs = true` — the bulk of the content links (e.g.
  `[design](/design)`) are written as root-relative Markdown links, which Hugo does not
  rewrite for a subpath by default. This setting stitches the subpath into every root-relative
  link at build time instead of hand-editing every content file.

## Local development

Hugo (extended) and Go are required to build this site; both are pinned into the bundled
Docker image, so no local install is needed:

```bash
docker compose up
```

Then open http://localhost:1313/DIY-PEDALBOARD.public/.
