# Taxi Path Replay

A single-page browser tool that replays an aircraft's taxi path on the airport diagram. Each ATC instruction becomes a step on the map, and each step's readback is checked against what the controller said.

## What it does

- Loads an FAA airport diagram (PDF or image) and aligns it to the ground.
- Reads an ATC transcript and turns each instruction into a numbered step (cleared to land, turn left at E2, hold short of K, and so on).
- Checks every pilot readback against the instruction and flags mismatches.
- Draws the ADS-B track (CSV or KML) and a replay scrubber over the diagram.
- Handles more than one aircraft, and reports how close they came on the ground.

## Inputs

| Input | Formats |
|---|---|
| Airport diagram | PDF (page 1) or image |
| ATC transcript | .txt file, or pasted text |
| ADS-B track | CSV or KML |

All files stay in the browser. Nothing is uploaded.

## Run it

Open `index.html` in a browser. It loads the SWA4628 at MKE sample on start. Leaflet and PDF.js load from cdnjs, so the browser needs an internet connection.

To serve it locally so the sample files load reliably:

```
python3 -m http.server
```

Then open http://localhost:8000.

## Samples

| File | Notes |
|---|---|
| `samples/mke-diagram.pdf` | MKE airport diagram (chart edition ended Mar 21, 2024) |
| `samples/swa4628-*` | SWA4628 at MKE, 24 Nov 2026: real transcript and ADS-B track |
| `samples/skw3401-test-*` | Made-up second aircraft for testing; follows SWA4628 and holds short of K |
| `samples/aal1154-*`, `samples/mia-test-diagram.pdf` | Made-up AAL1154 at MIA example |

Not for operational use. Use the current FAA diagram for anything beyond replay and review.
