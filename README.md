# alexandergould.dev

Personal portfolio site for Alexander Gould. A single, dependency-free `index.html` with hash routing, deployed to Netlify on every push to `main`.

## Structure

- `index.html` — the whole site: styles, markup, the project data, and the workshop viewer.
- `netlify.toml` — publish directory and security/caching headers. No build step.

## Adding a project to the workshop

Projects live in the `PROJECTS` array near the top of the `<script>` in `index.html`. Each entry has:

| field | purpose |
| --- | --- |
| `title`, `tag`, `blurb` | card text; `tag` also drives the filter chips |
| `link` | live site (or repo). External `http` links get an "Open live site" button |
| `embed` | URL loaded in the iframe when "Launch the demo" is clicked; falls back to `link` when empty |
| `gh` | GitHub repo name under `Agould94` — adds the collapsible “Changelog” (live commit history) at the bottom of the story |
| `repo: true` | treat `link` as a code repo — the CTA opens it in a new tab instead of iframing |
| `noDemo: true` | story only, no demo button or live-site link (set `link` to any non-URL string so the card still opens) |
| `story` | the pop-out narrative: `status`, `tagline`, `forWho`, `what`, `how`, `why`, optional `note` callout, `hint`, `updated`, `stats` |

Embedding a live site requires that site to allow framing (no `X-Frame-Options: SAMEORIGIN/DENY` and a permissive `frame-ancestors` CSP).

## Deploying

```
git push origin main
```

Netlify picks up the push and publishes the repo root.
