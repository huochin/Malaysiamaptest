# Malaysia Dam & Reservoir Explorer — v0

## Basemap fix

The previous version used `tile.openstreetmap.org` directly. That produced a
403/blocked response in some environments.

This version uses Esri's World Street Map as the default basemap and includes
an optional Esri World Imagery satellite layer. This avoids relying on the
OpenStreetMap Foundation's volunteer-run standard tile server.



## Why not simply bypass the 403?

OpenStreetMap explicitly says its standard tile server can block applications
that do not meet its tile-use requirements. Its policy requires correct
identification, attribution, caching and prohibits bulk downloading/prefetching.
A 403 should therefore not be bypassed by trying different OSM tile URLs or
spoofing headers.

## Run

Keep `index.html` and `facilities.js` in the same folder and open
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

## Water / power toggle

`facilities.geojson` holds 48 points tagged `category: water | power`
(dams, reservoirs, lakes; hydro and thermal power plants). Two checkboxes in the
panel show/hide each category. Confidence A/B points are traced to a source;
**C points are approximate** (from general knowledge) and should be verified
before exact use. Remaining dams without coordinates are in `coordinate_pending.csv`.
`dams_seed.geojson` is the original verified seed, kept for reference.

## Teacher / student guide (v2 redesign)

- **Present to class** (or press `P`): full-screen map, big labels and a caption bar. `←`/`→` step through places, `1/2/3` = All/Water/Power, `Esc` exits.
- **Explore**: filter by Water/Power, type, state or search; each place has a plain-language explanation and "Think about it" discussion questions.
- **Learn**: short explainers (how hydro works, why dams are in highlands, trade-offs).
- **Quiz**: click the map to find 8 random places; scored by distance. For students after class.
- Works on phones. Opens directly from disk (data is in `facilities.js`, generated from `facilities.geojson`).
