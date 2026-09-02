# AGENTS.md

This file provides guidance to coding agents working in this repository.

## What this repository is

This is **not a full Hugo site** — it's Kaldei's shared styling/theme template (`PRIVATE-KXN`) for a set of personal notes sites built with Hugo and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, skinned with the [Axentix](https://www.axentix.dev/) CSS/JS framework (loaded from CDN, not vendored).

Site content is intentionally **not** part of this repo. `.gitignore` excludes `content/`, `killchain/`, `tools/`, and `config.yaml` — those are supplied per-deployment by downstream repos. This repo only carries:
- `assets/custom.scss` — the site-wide style overrides (Axentix variables, sidenav/scrollspy styling, dark mode)
- `layouts/` — root-level Hugo layout overrides (currently just an image-render override)
- `themes/PaperMod/` — a **vendored, directly-modified copy** of the PaperMod theme (not a submodule)
- `static/images/` — logo/favicon/icon assets referenced from the theme layouts

## Distribution model

There is no local build/lint/test tooling in this repo (no `package.json`, no Makefile, no Hugo config). Instead, `.github/workflows/main.yml` runs on every push to `main` and:

1. Checks out this repo (`PRIVATE-KXN`) plus two sibling private repos: `KCN` ("Security") and `KDN` ("Devops")
2. `rsync`s this repo's contents (excluding `.git*`) into `source/` inside each sibling repo, deleting anything no longer present here
3. Commits and pushes the result to both sibling repos

In other words: **this repo is the single source of truth for theme/styling; the actual publishable sites live in `KCN` and `KDN`**, each with its own `content/`, `config.yaml`, etc. living alongside the synced `source/` tree. Changes made here propagate outward on push — there's nothing to "run" locally to see the effect unless you also have a sibling repo checked out with real content and a Hugo config.

## Making theme changes

- Edit `themes/PaperMod/layouts/**` and `themes/PaperMod/assets/**` directly for structural/behavioral theme changes (this is a fork-in-place, not something to keep in sync with upstream PaperMod).
- Edit `assets/custom.scss` for styling tweaks; it's compiled via Hugo Pipes (`resources.Get "custom.scss" | resources.ExecuteAsTemplate | toCSS | resources.Minify | resources.Fingerprint`) inside `themes/PaperMod/layouts/_default/baseof.html`, so it can reference Hugo site params directly (e.g. `{{ .Site.Params.color }}`).
- `baseof.html` wraps PaperMod's normal content column with a custom Axentix `sidenav` (left, branding/nav icons — home/GitHub/RootMe links, driven by `.Site.Params.acronym` / `.Site.Params.topic`) and a right-hand Axentix `scrollspy` sidenav populated from page `h1`/`h2` headings via inline JS in the same file.
- To test a change end-to-end you need a sibling content repo (e.g. a local checkout of `KCN` or `KDN`, or any Hugo site with `content/` + `config.yaml`) with this repo's `theme = "PaperMod"` and Hugo Pipes/SCSS transformer support — then run `hugo server` from that site's root, not from here.
- Since `themes/PaperMod` is modified in place (no git submodule, no upstream remote), there is no automated way to pull upstream PaperMod updates — changes must be re-applied by hand if upstream is ever refreshed.
