# DigiGovSA Static Landing Page

This is a static HTML5, CSS and vanilla JavaScript implementation of the DigiGovSA landing page.

## Run Locally

Open `index.html` directly in a browser, or serve the folder locally:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Assets

The hero image is referenced at `assets/hero-digigov.jpg`.

Partner logos live in `assets/logos/`:

- `presidency-logo.png`
- `sarb-logo.png`
- `home-affairs-logo.png`
- `mymzansi-logo.png`
- `national-treasury-logo.png`
- `mzansixchange-logo.png`

The DigiGovSA wordmark used in the header, footer and favicon is `assets/logos/digigovsa-logo.png`.

## Styling

Colour, spacing, radius and typography tokens are defined at the top of `css/styles.css` in the `:root` block.

## Editing Content

Major HTML sections are marked with comments in `index.html`. Cards are grouped by section, so adding or editing a card usually only requires updating the relevant `<article>` block and, where needed, its icon reference.
