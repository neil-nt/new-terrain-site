# new-terrain.io

Static site. No build step. Plain HTML/CSS.

## Files

```
new-terrain-site/
  index.html                  Home
  mission/index.html          /mission/
  contact/index.html          /contact/
  privacy-policy/index.html   /privacy-policy/
  styles.css                  All styling
  robots.txt
  sitemap.xml
  llms.txt                    Grounding document for LLMs
  assets/                     Logo, background, photo, favicon, og-image
```

## Local preview

```sh
cd new-terrain-site
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy to your server

Upload the entire folder contents to your webroot (e.g. `/var/www/new-terrain.io/`).

Clean URLs work out of the box because each page is in its own directory with an `index.html`. No `.htaccess` or nginx rewrites needed.

## SEO / GEO

- Canonical URLs on every page
- OG + Twitter card meta on every page (image at `/assets/og-image.png`, 1200×630)
- JSON-LD `Organization` schema on home, `ContactPage` schema on contact
- `robots.txt` pointing at sitemap
- `sitemap.xml` listing all four pages
- `llms.txt` at root — markdown grounding doc per [llmstxt.org](https://llmstxt.org), so ChatGPT/Claude/Perplexity have a clean factual reference when citing the site

## Things you'll want to swap before going live

- **Company number** — privacy policy can be updated with the Companies House number once registered.
- **Analytics snippet** — privacy policy declares Google Analytics; install the GA4 script in each `<head>` once the property is set up.
- **`og:image`** — current generated card uses Arial fallback (PIL can't load Plex). Worth swapping for a designed version when you have time.
- **`sameAs` in JSON-LD** — empty array on home. Once you have LinkedIn/X profiles, list them there so Google understands they're the same entity.

## Fonts

Google Fonts: IBM Plex Sans (300/400/500/600). Pulled via `<link>` so no self-hosting needed.

## Colours

```
--bg-cream:      #f5f4f2
--bg-cream-warm: #eae3d7
--bg-dark:       #051513   (matches hero background image)
--accent:        #d4fb38   (lime, matches the logo dot)
```
