# HVAC benchmark solution viewer

HTML pages showing the best known solution of each instance of the HVAC
field-service benchmark dataset, version 1.1.0 (60 instances).
Open `index.html`: one row per instance with its objective values and
their share of the published upper bounds, each linking to the instance's
page with a map of the jobs, the technicians' start and end points and the
routes, a timeline per team, every job's time windows, priority and skills,
the bounds and the objective values.

The pages are built from the dataset's published files only (problems,
solutions and the published validator) and show nothing beyond them.

## Map tiles

Opened as files, the pages request no map tiles: the map shows on a plain
background. To see the basemap (OpenStreetMap's standard tiles), serve this directory with any
static web server and open `index.html` over HTTP(S). The map library
(Leaflet 1.9.4) loads from unpkg.com, with subresource integrity; without
it, a plain map shows the same jobs and routes.

## Licences

- The data embedded in the pages (problems and solutions) is the dataset's
  data, under the Open Database License (ODbL) 1.0, as in the dataset's
  `LICENSE`.
- The code in the pages (stylesheet and script) is under the MIT License,
  as in the dataset's `LICENSE-CODE` (Copyright (c) 2026 PENDING: the owner's name.).
- Map tiles, when served: © OpenStreetMap contributors (or the tile
  source named on the map).

`SHA256SUMS` lists every file; check it with `sha256sum -c SHA256SUMS`.
