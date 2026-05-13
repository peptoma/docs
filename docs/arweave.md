# Arweave Archiving

Every peptide analysis and community annotation submitted to PEPTOMA is automatically archived to the Arweave blockweave for permanent, immutable storage.

## How It Works

1. Sequence is submitted → AI analysis runs
2. Full analysis report is packaged as JSON with metadata tags
3. Transaction is posted to `arweave.net` and signed with the PEPTOMA wallet
4. TxID is stored in the database and displayed on the sequence page
5. After ~30–60 minutes (blockchain confirmation time), the data is accessible at `arweave.net/<txId>`

## Data Format

Each archived record is a JSON object with:

```json
{
  "platform": "PEPTOMA",
  "version": "1.0",
  "rrid": "SCR_028424",
  "type": "sequence_analysis",
  "sequenceId": 42,
  "sequence": "KWLRRVWRPQKI",
  "analysis": {
    "bioactivityScore": 91,
    "bioactivityLabel": "antimicrobial",
    "structurePrediction": "alpha_helix",
    "toxicityRisk": "low",
    "confidenceScore": 84
  },
  "timestamp": "2026-05-13T00:00:00.000Z"
}
```

## Arweave Tags

Each transaction is tagged for querying via the Arweave GraphQL gateway:

| Tag | Value |
|---|---|
| `App-Name` | `PEPTOMA` |
| `Type` | `sequence_analysis` or `annotation` |
| `Sequence-ID` | Numeric sequence ID |
| `Bioactivity-Label` | e.g. `antimicrobial` |
| `RRID` | `SCR_028424` |

## First Confirmed Archive

[`LG43C9LtrS3veG51TRF-YVpZjvceyvoIEFK-HLFt-OU`](https://arweave.net/LG43C9LtrS3veG51TRF-YVpZjvceyvoIEFK-HLFt-OU)
