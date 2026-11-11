<p align="center">
  <a href="https://rdo-app.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/rdo-logo-dark.svg">
      <img src="assets/rdo-logo-light.svg" alt="RDO" width="225">
    </picture>
  </a>
</p>

<h1 align="center">Field-service routing solver: solutions demo</h1>

<p align="center">
  Interactive maps, routes and timelines of the <a href="https://rdo-app.com"><b>RDO</b></a> day planner's best known solutions
</p>

<p align="center">
  <a href="https://rdo-app.com"><img alt="rdo-app.com" src="https://img.shields.io/badge/rdo--app.com-E85D2A?style=flat-square"></a>
  <a href="https://rdoapp.github.io/field-service-routing-solver-solutions-demo/"><img alt="Live demo" src="https://img.shields.io/badge/live-demo-16130F?style=flat-square"></a>
  <a href="https://github.com/rdoapp/field-service-routing-solver-datasets"><img alt="hvac dataset v1.1.0" src="https://img.shields.io/badge/hvac-v1.1.0-16130F?style=flat-square"></a>
  <img alt="Data licence: ODbL 1.0" src="https://img.shields.io/badge/data-ODbL%201.0-16130F?style=flat-square">
  <img alt="Code licence: MIT" src="https://img.shields.io/badge/code-MIT-16130F?style=flat-square">
</p>

---

[RDO](https://rdo-app.com) plans the working day of field-service
companies: which technician or crew visits which customer, in which order
and when. We measure its solver on an open benchmark, the
[field-service routing solver datasets](https://github.com/rdoapp/field-service-routing-solver-datasets).
This repository shows the results. Every best known solution in the
benchmark gets a page you can open in a browser.

**[Open the live demo →](https://rdoapp.github.io/field-service-routing-solver-solutions-demo/)**

## What you can see

For each of the 60 HVAC field-service planning days (Budapest and Pécs, 5
to 50 technicians), the viewer shows:

- **Objective and bounds**: served service minutes, served priority-3
  (urgent) minutes and travel time, next to the instance's published upper
  bounds.
- **Map**: every job, each technician's start and end point, and the route
  each team drives, on OpenStreetMap.
- **Timeline**: each team's day, with driving, service, waiting and the
  lunch break, against the shift.
- **Jobs not served**: what stays in the queue, with time windows, priority
  and skills.

Some starting points:

| instance | what it is |
|---|---|
| [`budapest-t05-servable-s4`](https://rdoapp.github.io/field-service-routing-solver-solutions-demo/hvac-viewer/budapest-t05-servable-s4.html) | the smallest day: 5 technicians, 25 jobs, all served |
| [`pecs-t10-full-s1`](https://rdoapp.github.io/field-service-routing-solver-solutions-demo/hvac-viewer/pecs-t10-full-s1.html) | 10 technicians facing a 720-job backlog |
| [`budapest-t50-full-s1`](https://rdoapp.github.io/field-service-routing-solver-solutions-demo/hvac-viewer/budapest-t50-full-s1.html) | the largest: 50 technicians in 45 teams, 1,350 jobs |

## Results at a glance

- **`servable` days** (one known plan serves the whole queue): all 30 are
  served completely, reaching the upper bound on served minutes.
- **`full` days** (a backlog several times larger than the fleet can
  serve): on average 82 % of the upper bound on served minutes. The bound
  comes from a relaxation that counts only each job's cheapest possible
  drive, so it usually can't be reached. It is a ceiling, not a target.

The full per-instance table is on the [demo page](https://rdoapp.github.io/field-service-routing-solver-solutions-demo/#solutions)
and in [`hvac-viewer/index.html`](hvac-viewer/index.html).

## Running it locally

The pages are static HTML with the data embedded. They need no build step
and no backend.

```sh
git clone https://github.com/rdoapp/field-service-routing-solver-solutions-demo.git
cd field-service-routing-solver-solutions-demo
python3 -m http.server 8000      # then open the printed address in a browser
```

Opened straight from disk (`file://`), the maps show the routes on a plain
background. Serve the folder over HTTP, or use the GitHub Pages site, to
see the OpenStreetMap basemap. The map library (Leaflet 1.9.4) loads from
unpkg.com with subresource integrity.

## Repository layout

```
.
├── index.html       landing page (GitHub Pages)
├── README.md        this file
├── assets/          RDO logo
└── hvac-viewer/     one page per instance, an index, README and SHA256SUMS
```

The files in `hvac-viewer/` are generated from the dataset's published
problems, solutions and validator, and show nothing beyond them. Check
them with `cd hvac-viewer && sha256sum -c SHA256SUMS`.

## Beat our solutions

The problems are open. Get them from the
[datasets repository](https://github.com/rdoapp/field-service-routing-solver-datasets),
run your solver, check your solution with the published `validate.py`,
compare it with `score.py`, and send it in. Better solutions are added to
the dataset under your name.

## Licence

- **Problem and solution data** embedded in the pages: Open Database
  License (ODbL) 1.0, as in the dataset's `LICENSE`. © OpenStreetMap
  contributors; population grid © Eurostat.
- **Viewer code** (stylesheet and scripts in the pages): MIT, as in the
  dataset's `LICENSE-CODE`.
- **Map tiles**, when loaded: © OpenStreetMap contributors.

---

<p align="center">
  <a href="https://rdo-app.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="assets/rdo-logo-dark.svg">
      <img src="assets/rdo-logo-light.svg" alt="RDO" width="90">
    </picture>
  </a><br>
  <sub>Made by the <a href="https://rdo-app.com">RDO</a> team. The RDO name and logo are not covered by the data or code licences.</sub>
</p>
