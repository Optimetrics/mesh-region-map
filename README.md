# Michigan MeshCore region map and configurator

- **Map:** https://optimetrics.github.io/mesh-region-map/ — the five Michigan
  subregions from RFC-001, drawn as reference boundaries. Not borders; a
  repeater carries the region of the coverage it actually serves.
- **Configurator:** https://optimetrics.github.io/mesh-region-map/configurator/ —
  pick a city or county and your firmware, get the `region` commands.

Why any of this: [Regions and Scoping](https://michmesh.com/docs/MeshCore/Regions-and-Scoping) on michmesh.com.

## Credit

- Map viewer: [New England Mesh](https://newenglandme.sh/regions), copied from
  [their repo](https://github.com/newenglandmesh/newenglandmesh) as they invite.
- Region hierarchy: Kaylee's [RFC-001](https://github.com/AniMeiGrrl/mi-region-rfc).
- County lines: US Census via [us-atlas](https://github.com/topojson/us-atlas).
  Groupings started from Nielsen DMAs.
- Tiles © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors.

## Files

```
index.html, index.json, *.geojson   the map
configurator/                       the configurator and its data.json
region-tools/                       county-subregions.json + build.mjs to regenerate the geojson
```

## Contributing

Most changes are a one-file PR to `configurator/data.json`:

- **New live local region:** add the county to `local`, e.g. `"Muskegon": "mkg"`.
  Say which repeaters carry it. Plain place names, or an airport code only
  where it's already in use. No invented three-letter codes.
- **Town missing from search:** add it to `cities`, e.g. `"Sparta": "Kent"`.
- **New channel:** open a PR or issue with the channel name and its tag.

To move a county between subregions, edit `region-tools/county-subregions.json`,
run `node build.mjs` in that folder (needs `npm i us-atlas topojson-client d3-geo`),
and commit the regenerated files. Say why; coverage beats the county line.

Test locally with `python3 -m http.server` from the repo root.
