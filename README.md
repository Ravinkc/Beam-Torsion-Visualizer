# Bending vs. Torsion — Interactive Beam Visualizer

A single-file, no-build-step 3D tool for the concept every mechanics-of-materials
student mixes up at least once: a bending moment and a torque look like the same
curved arrow on paper, but they rotate a cross-section about completely
different axes. This lets you watch the difference happen in real time instead
of squinting at a 2D sketch.

**[Live demo →]  https://ravinkc.github.io/Beam-Torsion-Visualizer/** 

---

## What's in it

- **Bending / Torsion / Combined** loading modes, driven by the actual closed-form
  beam equations (cantilever and simply-supported, point load or UDL) — not a
  canned animation
- **Cross-section swap**: rectangular, circular, and open I-beam profiles. The
  I-beam uses the real open thin-walled torsion constant
  (`J ≈ ⅓Σbt³`, stress ∝ local wall thickness), which is exactly why it twists
  far more than a closed section under the same torque
- **Stress heatmap** (3-stop blue→yellow→red), togglable against the plain
  checker-grid view
- **Free-body diagrams** that update live with your support/load choice, reactions included
- **Stress along the length** — an extreme-fiber stress chart across the whole span
- **Cross-section stress raster** — a pixel-accurate slice at any x you pick,
  colored the same way as the 3D mesh
- **Click-to-inspect + Mohr's circle** at any point, including a rotating stress
  element that visually (and numerically) shows shear stress collapsing to
  zero at the principal angle — with a θ-sweep chart proving *why* that happens
  (`dσx′/dθ = 2τx′y′` — shear is the slope of the normal-stress curve, so a
  flat spot and zero shear are the same event)

All physics lives in one place near the top of `index.html`'s `<script>` block,
so if you want to check or extend the formulas, that's where to look.

## Run it locally

No build step, no dependencies. Just open the file:

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
open index.html   # or: python3 -m http.server, then visit localhost:8000
```

It loads Three.js from a CDN (`cdnjs.cloudflare.com`), so you need an internet
connection the first time, but nothing else to install.


## Tech

Plain HTML/CSS/JS. 3D rendering via [Three.js](https://threejs.org/) (r128, loaded
from cdnjs). No React, no build tooling, no npm install — the whole thing is
one file so it's trivial to host anywhere that serves static files.

## Credits

Built by Ravin KC and Rojseen Shrestha, out of an idle-time
conversation about how confusing bending vs. torsion is the first time you meet it.


