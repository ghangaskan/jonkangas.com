# jonkangas.com

Static HTML, CSS, and JavaScript for jonkangas.com. Deployment is manual to Amazon S3.

## Bible reading tracker

`bible-reading-tracker/index.html` is the self-contained Bible Reading Tracker Builder v1.1. Its help, maintainer notes, and GPL license are included in the same directory. No build step or package installation is required.

For local development, run from this repository:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open the tracker at `/bible-reading-tracker/index.html` on the local server.

For deployment, copy the entire `bible-reading-tracker/` directory to the bucket with that prefix, keeping all four files together. Serve HTML as `text/html`, Markdown as `text/markdown`, and `LICENSE` as `text/plain`. On an S3 website endpoint configured with `index.html` as its index document, `/bible-reading-tracker/` resolves to the tracker. For other endpoints, use the explicit `/bible-reading-tracker/index.html` path unless directory-index routing is configured.

## Deuteronomy conference

`deuteronomy/index.html` is a static adaptation of the supplied conference website draft. It uses local CSS with no framework, CDN, or build step. The page preserves the original program and marks the event as a proposal with unconfirmed dates, venue, and registration.

Copy the whole `deuteronomy/` directory to the matching S3 prefix. Serve `styles.css` as `text/css`, PDFs as `application/pdf`, and text documents as `text/plain` (Markdown as `text/markdown`). Use `/deuteronomy/index.html`, or `/deuteronomy/` with directory-index routing configured.

The downloadable source documents contain draft placeholders. Two alternate “Choose Life” brochures describe a different schedule and are labeled separately. The tiny incomplete PDF and editable Word draft were not included in the deployment folder; the supplied uploads remain available outside the checkout.

## Billybob story

`billybob/index.html` is the supplied static reader for **Billybob: The Hundred-Yard Potato**. All twelve illustrations, `BB_1.png` through `BB_12.png`, are present and validated. Browser checks passed for image decoding, next/previous buttons, keyboard navigation, thumbnails, last-page state, and mobile width. Billybob is included in the combined S3 archive.

Copy the entire `billybob/` directory to the bucket under that prefix. Serve PNG files as `image/png`. No build step or dependencies are required.

The main homepage has not been added yet.
