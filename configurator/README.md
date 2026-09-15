# Michigan MeshCore region configurator

Single static page. Pick a city or county, repeater or companion, firmware
version, and options; get the commands. No build, no dependencies. Works
anywhere that serves static files (GitHub Pages, or the `map` repo alongside
the region map).

- `index.html` — the page
- `data.json` — county → subregion, live local tags, city → county, subregion labels

To add a live local tag, add it to `local`. To add a town to the search, add
it to `cities`. County assignments come from RFC-001 Addendum A; regenerate
from `county-subregions.json` rather than hand-editing them.
