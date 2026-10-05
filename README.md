# Malaysia Dam & Reservoir Explorer — v0

## Basemap fix

The previous version used `tile.openstreetmap.org` directly. That produced a
403/blocked response in some environments.

This version uses Esri's World Street Map as the default basemap and includes
an optional Esri World Imagery satellite layer. This avoids relying on the
OpenStreetMap Foundation's volunteer-run standard tile server.

The dam dataset itself is unchanged.

## Why not simply bypass the 403?

OpenStreetMap explicitly says its standard tile server can block applications
that do not meet its tile-use requirements. Its policy requires correct
identification, attribution, caching and prohibits bulk downloading/prefetching.
A 403 should therefore not be bypassed by trying different OSM tile URLs or
spoofing headers.

## Run

Keep `index.html` and `dams_seed.geojson` in the same folder and open
`index.html` in a modern browser. An internet connection is required for the
basemap tiles.

The map now has:
- Street Map layer
- Satellite layer
- Dam markers
- Popup source/confidence information

## Future production option

For a deployed public site, we can move to a dedicated basemap provider or
self-hosted/vector-tile setup. CARTO currently offers OSM-derived basemaps with
a free API-key tier for qualifying non-commercial projects, subject to its
current terms and attribution requirements.
