# Museum Painting Colors & LRV Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24303543.svg)](https://doi.org/10.5281/zenodo.24303543)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

2,501 colors extracted from 414 public-domain paintings in the collections of
**The Metropolitan Museum of Art** and **The Art Institute of Chicago**, with
perceptual color data (CIELAB, LCh) and **Light Reflectance Value (LRV)** for
every color — the same metric interior and exterior paint brands print on
their color cards.

Built and maintained by [Light & Pigment](https://lightandpigment.com/), a
site that helps people choose paint colors by matching them against colors
found in real paintings. This dataset is the raw data behind that site,
published so researchers, designers, and other color tools can use it too.

## Why LRV

LRV (0–100) measures how much light a color reflects: near 0 is near-black,
100 is pure white. It is one of the few color metrics with direct real-world
meaning for interior design — a wall painted at LRV 15 reads very differently
in a north-facing room than one at LRV 70 — but public datasets that pair LRV
with real, attributable source imagery are rare. This one does, because every
row traces back to a specific, nameable, public-domain painting.

## Files

- `museum-painting-colors-lrv.csv` — one row per extracted color (2,501 rows).
- `museum-painting-colors-lrv.json` — the same data grouped by painting (441
  paintings, including a handful with colors not yet fully processed).

### CSV columns

| Column | Description |
|---|---|
| `painting_slug` | Stable identifier, also the Light & Pigment page slug |
| `painting_title` | Title of the painting |
| `artist` | Artist name as credited by the museum |
| `date` | Date/period as credited by the museum |
| `museum` | Source museum |
| `museum_url` | Link to the museum's own collection page |
| `license` | Rights status of the source image (all rows: public domain / CC0) |
| `source_image_url` | Direct link to the museum's digital image |
| `color_rank` | Rank of this color within the painting by area share (1 = largest) |
| `hex` | sRGB hex value |
| `lab_l`, `lab_c`, `lab_h` | CIELAB lightness, and chroma/hue in LCh form (D65 illuminant) |
| `lrv` | Light Reflectance Value, 0–100 |
| `share_pct` | Approximate share of the painting's visible area this color covers |
| `color_family` | Broad color-name bucket (e.g. `blue`, `beige`, `brown`) |
| `light_pigment_url` | The Light & Pigment guide page for this painting's palette |

## Methodology

1. Source images are pulled from each museum's own open-access API/collection
   (Metropolitan Museum of Art Open Access; Art Institute of Chicago API),
   limited to works explicitly marked public domain / CC0 by the museum.
2. Each image is downsampled and clustered into dominant colors, weighted by
   the share of the image area each color covers.
3. Each resulting color is converted from sRGB to CIELAB (D65) and LCh, and
   LRV is computed from the CIELAB lightness channel using the standard
   relative-luminance formula paint manufacturers use.
4. Colors are bucketed into a broad human-readable family name for filtering.

No color has been manually adjusted. The numbers are what the computation
above produces from the museum's own public image file, linked in
`source_image_url` for independent verification.

## License

- **This dataset's structure, the LRV/LAB/LCh computations and the CSV/JSON
  files themselves** are released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)
  — no rights reserved, use for anything, no attribution required (though a
  link back to [lightandpigment.com](https://lightandpigment.com/) is always
  appreciated).
- **The underlying painting images** are not included here (only linked) and
  remain subject to each museum's own open-access terms: [The Met's Open Access policy](https://www.metmuseum.org/about-the-met/policies-and-documents/open-access)
  and the [Art Institute of Chicago's open access collection](https://www.artic.edu/open-access).
  Both museums have marked the specific works in this dataset as public
  domain / CC0.

## Citing this dataset

Every release is archived on Zenodo and has a DOI, so the dataset can be cited
in published work. The DOI above resolves to the most recent version; each
individual version also has its own DOI on the Zenodo record page.

> Light & Pigment, *Museum Painting Colors & LRV Dataset* (2026).
> Zenodo. https://doi.org/10.5281/zenodo.24303543

A link to [lightandpigment.com](https://lightandpigment.com/) is always
appreciated too, though CC0 means none is required.

## Questions / corrections

Open an issue in this repository, or use the contact form at
[lightandpigment.com/contact](https://lightandpigment.com/contact/).
