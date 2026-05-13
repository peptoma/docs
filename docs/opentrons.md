# Opentrons Lab Automation

PEPTOMA generates Opentrons OT-2 compatible Fmoc SPPS Python protocols directly from peptide analysis results, enabling automated synthesis validation runs of top-ranked hits.

## Download a Protocol

1. Open any sequence at `peptoma.xyz/annotate/:id`
2. Scroll to the **Links + Export** panel in the sidebar
3. Click **Opentrons SPPS Protocol (.py)**
4. Upload the `.py` file to the [Opentrons App](https://opentrons.com/ot-app/)

## What the Protocol Contains

- **Header** — sequence ID, bioactivity score, structure, toxicity, MW, generated date
- **Reagent list** — all Fmoc building blocks needed with well assignments
- **Resin pre-swell** — DMF wash 15 min before cycles begin
- **Coupling cycles** — per-residue C→N direction:
  - Deprotection: 20% piperidine/DMF × 2 (5 min each)
  - DMF wash × 3
  - Coupling: AA + HATU/DIPEA (45 min)
  - Post-coupling DMF wash × 3
- **Final Fmoc deprotection**
- **PEPTOMA record URL** embedded in protocol

## Supported Robot

- **Opentrons OT-2** (`apiLevel: "2.15"`)
- Compatible with Opentrons Flex with minor labware substitutions

## Important Note

Protocols are generated from computational analysis data. Always simulate in the Opentrons App and validate wet-lab before running on actual hardware.
