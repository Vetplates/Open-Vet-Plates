# Open Vet Plates

An open catalogue of veterinary orthopaedic implants: 788 implants and 6,332 size variants from 49 manufacturers, with SKUs, specifications and SVG outline drawings.

## Layout

| Path | Contents |
|---|---|
| `catalogue.csv` | One row per variant: IDs, manufacturer, family, SKUs, specs and available views |
| `index.json` | One entry per implant, without drawings, for quick lookup |
| `implants/<manufacturer>/<implant>.json` | Full record for one implant, including the drawings of every variant |

## IDs

IDs are readable paths: `<manufacturer>/<implant>` for an implant and `<manufacturer>/<implant>/<variant>` for a variant, e.g. `osteocertus/0c-tplo-gen-4/large-narrow`. An implant's file lives at `implants/<implant id>.json`. Where two items would get the same ID, the later one gets a `-2`, `-3`, … suffix.

## Implant record

```json
{
  "id": "osteocertus/0c-tplo-gen-4",
  "name": "0C TPLO Gen 4",
  "description": "Low directed Head Screws",
  "manufacturer": "Osteocertus",
  "family": "TPLO Gen 4",
  "variants": [
    {
      "id": "osteocertus/0c-tplo-gen-4/large-narrow",
      "name": "Large Narrow",
      "skus": ["TO21-104-L", "TO21-104-R"],
      "specs": { "material": "Ti 6-4", "thickness": 4.0 },
      "views": [ { "orientation": "top", "svg": "<svg …>" } ]
    }
  ]
}
```

- `family` and `description` may be `null`.
- `specs` keys are among: `anatomic_location`, `curvature_type`, `diameter`, `hole_type`, `holes`, `indication`, `length`, `locking_type`, `material`, `offset`, `plate_size`, `rotation`, `side`, `size`, `thickness`, `weight_band`, `width`. Plain numbers are stored as numbers; anything else (e.g. `"2.6 mm"`, `"2x3"`) is kept as the manufacturer wrote it.
- `orientation` is one of `top`, `front`, `left`, `right`, `back`, `bottom`. A variant may have more than one view with the same orientation.

## Drawings

Each view is a standalone SVG. Coordinates are rounded to 3 decimal places. Most drawings group their shapes with these classes, which you can style yourself:

| Class | Meaning |
|---|---|
| `body` | Filled plate silhouette |
| `edge` | Outlines and hole edges |
| `guide` | Construction and reference lines |

A few drawings carry their own embedded styles with classes named `style-a`, `style-b`, ….

## License

Released into the public domain under [CC0 1.0](LICENSE). Manufacturer names, product names and SKUs are trademarks of their respective owners.
