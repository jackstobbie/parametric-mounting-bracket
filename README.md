# Parametric Mounting Bracket

A right-angle mounting bracket generated entirely from code using [CadQuery](https://cadquery.readthedocs.io/), a Python library for scripting real, exportable 3D CAD geometry.

Instead of drawing the part by hand in a CAD GUI, the shape is fully defined by parameters at the top of the script. Changing a single number (length, hole spacing, material thickness) and re-running the script regenerates a correct, ready-to-manufacture model — no manual redrawing.

## Why this approach

- **Repeatable design.** The same script produces a family of brackets at any size, which is how design automation and generative CAD workflows work at scale.
- **Version-controlled geometry.** The CAD model lives in a `.py` file, so changes are tracked in Git like any other engineering artifact — not buried in binary CAD save files.
- **Manufacturing-aware.** Mounting holes are sized for M6 hardware clearance, and the interior corner is filleted to reduce stress concentration, consistent with standard sheet-formed bracket design.

## Files

- `bracket_generator.py` — the parametric model definition
- `bracket.step` — CAD-native export, opens in SolidWorks, Fusion 360, Onshape, etc.
- `bracket.stl` — mesh export, used for 3D printing and the web viewer

## Running it

```bash
pip install cadquery
python bracket_generator.py
```

This regenerates `bracket.step` and `bracket.stl` from the current parameters.

## Parameters

| Parameter | Description | Default |
|---|---|---|
| `BASE_LENGTH` | Length of the horizontal base leg | 80 mm |
| `WALL_HEIGHT` | Height of the vertical wall leg | 60 mm |
| `WIDTH` | Width of the bracket | 40 mm |
| `THICKNESS` | Material thickness | 5 mm |
| `HOLE_DIAMETER` | Mounting hole diameter | 6.5 mm |
| `HOLE_INSET` | Hole center distance from leg ends | 12 mm |
| `FILLET_RADIUS` | Interior corner fillet radius | 4 mm |
