# litpathlabs-web

Source for **https://litpathlabs.com**: plain HTML and CSS with no build step and no dependencies.

## Deploying

Cloudflare Pages watches this repository (project `litpathlabs-web`).

- **Push or merge to `main`** and Cloudflare publishes to litpathlabs.com, usually within a minute or two.
- **Push any other branch** and Cloudflare builds a preview at its own `*.pages.dev` address; the live site is untouched.
- **If a deploy hangs** (it happened once during a Cloudflare outage), open Cloudflare → Workers & Pages → `litpathlabs-web` → Deployments and click *Retry deployment*.

There's nothing to build. The build command is empty and the output directory is the repository root.

## Layout

| Path | What it is |
| --- | --- |
| `index.html` | Homepage: project cards and the Writing section |
| `contact/index.html` | Contact page (embedded Google Form) |
| `manual/index.html` | *Without Lying to Yourself*, the GB10 field manual, read online |
| `manual/Without-Lying-to-Yourself.pdf` | The same manual as a PDF |
| `404.html` | Served by Cloudflare for any missing page; uses absolute paths because it can appear at any URL |
| `site.css` | Shared styles for the homepage, contact page and 404 |
| `favicon.svg` | Site icon |
| `og.png`, `manual/og.png` | 1200×630 images shown when a link is shared (Open Graph) |

The manual keeps its own inline styles. Its pages are laid out as Letter sheets for print, then reflow to the screen width below 860px.

## Editing notes

- **Colours** live as variables at the top of `site.css`. Link text uses `--link` (`#818cf8`); the darker indigo `--accent` is only for button backgrounds, because it is too dim to read as small text on black.
- **New pages** should link `site.css` and `favicon.svg`. Add `class="sub"` to `<body>` for the smaller inner-page header.
- **Link previews** need absolute URLs on `og:url` and `og:image`, under `https://litpathlabs.com/`. Check a page at opengraph.xyz after deploying.
- **Preview images** are 1200×630 PNGs. If the manual's cover changes, regenerate `manual/og.png` to match.
