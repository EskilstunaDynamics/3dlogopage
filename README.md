# 3dlogopage

A single-page WebGL rendering of the **stapp** logo as a spinning 3D object,
built with [Three.js](https://threejs.org/).

## What it does

- Rebuilds the blocky, point-symmetric "S" as extruded geometry: a horizontal
  stroke with a descending angled leg (top-left), a stepped drop (top-right),
  and the same two shapes rotated 180° for the bottom half.
- The middle stroke is a green, emissive parallelogram (vertical ends, slanted
  top/bottom) that bridges the two halves on an angle, matching the source mark.
- Slow spin + gentle float, pulsing green glow, `UnrealBloomPass`, environment
  reflections, a drifting particle field, and orbit/zoom controls.

The source artwork is `screenshot-2026-09-08_21-29-56.png`.

## Running

Three.js loads from a CDN via an import map, so the page must be served over
HTTP (not opened as a `file://` URL):

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

Add `#still` to the URL to hold the logo face-on (orbit and zoom still work).

## Tuning

The knobs are grouped near the top of the `<script>` in `index.html`:

- `D` – extrude depth of the S arms
- `shapeAPts` / `shapeBPts` – the traced arm profiles (source-image pixels)
- the `midGeo` block – size, shear angle, and position of the green bar
- `bloom`, light intensities, and the `tick()` animation values
