# Getting Started with PEPTOMA

PEPTOMA is an open decentralized science (DeSci) platform for peptide research. Submit sequences for AI analysis, contribute community peer-review annotations, and earn $PEPTM token rewards.

---

## 1. Submit Your First Sequence

Go to **[The Lab](https://peptoma.xyz/lab)** and enter a peptide sequence in single-letter amino acid code:

```
KWLRRVWRPQKI
```

Select:
- **Analysis depth** — `Standard` (3 runs/day free) or `Deep` (requires RESEARCHER tier)
- **Disease target** — optional context (e.g. `MRSA`, `Cancer`, `Antiviral`)

Click **Submit**. Results appear within seconds:

| Field | Description |
|---|---|
| Bioactivity Score | Predicted activity (0–100) |
| Bioactivity Label | Class: antimicrobial, antiviral, hormonal, etc. |
| Confidence Score | Model confidence (0–100) |
| Structure Prediction | α-helix / β-sheet / random coil / mixed |
| Toxicity Risk | low / medium / high |
| Molecular Weight | Exact calculation (Da) |
| Half-life | Estimated plasma half-life |

---

## 2. Annotate a Sequence

Open any sequence from the **[Feed](https://peptoma.xyz/feed)** and choose an annotation type:

| Type | Points | When to use |
|---|---|---|
| **Confirm** | +2 | You agree with the AI classification |
| **Challenge** | +3 | You dispute the result with evidence |
| **Extend** | +5 | You add a related sequence or supporting data |
| **Tag** | +2 | You add a disease/target label |

Points earned are tracked in **[Mission Control](https://peptoma.xyz/missions)** and convert to $PEPTM.

---

## 3. Export Your Data

From any sequence's Annotate page, use the **Links + Export** panel:

- **Benchling ELN** — export directly to your lab notebook
- **GenBank** — download `.gp` file for NCBI submission
- **bioRxiv** — auto-generated preprint manuscript template
- **Opentrons** — download `.py` robot protocol for OT-2 synthesis

---

## 4. Use the API

**PRO** (≥ 2,000 $PEPTM staked) and **LAB** (≥ 10,000 $PEPTM staked) tier users get API access.

Generate a key at [Mission Control → API Keys](https://peptoma.xyz/missions).

Quick test:
```bash
curl -X POST https://peptoma.xyz/api/sequences \
  -H "Authorization: Bearer pptm_your_key" \
  -H "Content-Type: application/json" \
  -d '{"sequence":"KWLRRVWRPQKI","depth":"standard"}'
```

---

## 5. Connect an AI Agent

Install the MCP server to use PEPTOMA tools inside Claude, Cursor, or any MCP-compatible agent:

```bash
npx peptoma-mcp --api-key pptm_your_key
```

See the [MCP Server guide](mcp.md) for full setup.

---

## Next Steps

- [API Reference](api-reference.md) — complete endpoint documentation
- [SDK Guide](sdk.md) — programmatic access via TypeScript/JavaScript
- [Tokenomics](tokenomics.md) — staking tiers and reward mechanics
