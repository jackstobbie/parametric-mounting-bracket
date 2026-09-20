# Parametric Wing & Engine Nacelle

A swept, tapered aircraft wing with an underslung engine nacelle, generated entirely from code using [CadQuery](https://cadquery.readthedocs.io/), a Python library for scripting real, exportable 3D CAD geometry.

The wing is built by lofting between root and tip airfoil cross-sections — not just a stretched box — with independent control over span, chord (root and tip), sweep angle, and nacelle position/size. Changing a parameter and re-running the script regenerates a correct, watertight solid.

## Why this approach

- **Real aerodynamic-style geometry.** The wing surface is a genuine loft between two airfoil sections, not a placeholder shape.
- **Parametric.** Span, taper ratio, sweep, and nacelle placement are all top-level variables.
- **Manufacturing-aware boolean unions.** The nacelle and pylon are fused into the wing as a single watertight solid, verified via boundary-representation validity checks, not just visual inspection.

## Files

- `wing_generator.py` — the parametric model definition
- `wing.step` — CAD-native export, opens in SolidWorks, Fusion 360, Onshape, etc.
- `wing.stl` — mesh export, used for 3D printing and the web viewer

## Running it

```bash
pip install cadquery
python wing_generator.py
```

## Parameters

| Parameter | Description | Default |
|---|---|---|
| `ROOT_CHORD` | Chord length at the wing root | 140 mm |
| `TIP_CHORD` | Chord length at the wing tip | 55 mm |
| `SPAN` | Wing span | 260 mm |
| `SWEEP` | Leading-edge sweep offset at the tip | 90 mm |
| `NACELLE_SPAN_POS` | Spanwise position of the engine | 95 mm |
| `NACELLE_RADIUS` | Engine nacelle radius | 16 mm |
| `NACELLE_LENGTH` | Engine nacelle length | 70 mm |
