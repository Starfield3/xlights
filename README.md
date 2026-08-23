# xlights — `full-matrix-model`

Geometry for **FullMatrix**, the 4,800-pixel pixel matrix driven by the Kulp K32-Max.

Branched from `main`, so it carries only these files — the golden `xlights_rgbeffects.xml`
branches (`halloween`, `christmas`, `halloween-fixed`) are untouched.

## Files

| File | What it is |
|---|---|
| `FullMatrix.xmodel` | the xLights custom model |
| `full_matrix_custom_model.csv` | full node map as a grid — the model's node numbering |
| `module3_custom_model.csv` | single-module node map (the building block the full matrix repeats) |
| `matrix_node_map.png` | rendered node map, for reading the wiring without opening xLights |

## The prop

4,800 pixels on **10 K32 ports × 480 px**, channels **155 – 14554** (xLights numbering).
Ports are sized to 480 rather than the ~768 ceiling the port budget allows.

**Note on frame rate:** the port sizing was originally derived assuming 40 fps. The show
sequences currently export at **100 fps**, which leaves a 10 ms frame budget against roughly
14.4 ms needed to clock out 480 pixels at standard WS281x timing. That tension is unresolved as
of 23 Aug 2026 and is worth settling before relying on this model at full size.

## Why branches, not folders

This repo is organised **by branch**: the Halloween and Christmas golden files share the same
filename (`xlights_rgbeffects.xml`), so folders would collide. One branch per piece of work.

## ⚠ Line endings

The working machine has `core.autocrlf=true`, which rewrites checked-out text files to CRLF — so
hashing a *checked-out* file will not match the stored blob. This branch ships a `.gitattributes`
marking `*.xmodel`, `*.csv` and `*.png` as non-text so they stay byte-exact.

To verify a file against a recorded hash, read the blob rather than the working copy:

```bash
git show full-matrix-model:FullMatrix.xmodel | sha256sum
```

## Related

- `Starfield3/fpp-config` (private) — controller configuration snapshots
- `Starfield3/butzbach-show-admin` (private) — press, outreach, correspondence

Nothing with personal data belongs in this repository; it is public.
