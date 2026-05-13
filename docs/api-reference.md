# API Reference

Base URL: `https://peptoma.xyz/api`

Authentication: pass your API key as `Authorization: Bearer pptm_...` header.  
Keys available to **PRO** and **LAB** tier wallets from [Mission Control](https://peptoma.xyz/missions).

---

## Sequences

### `POST /api/sequences`
Submit a peptide sequence for AI analysis.

**Request body:**
```json
{
  "sequence": "KWLRRVWRPQKI",
  "userId": "your_wallet_address",
  "depth": "standard",
  "diseaseTarget": "MRSA",
  "notes": "AMP candidate"
}
```

| Field | Type | Required | Description |
|---|---|---|---|
| `sequence` | string | Yes | Single-letter AA codes, 3–512 residues |
| `userId` | string | No | Wallet address for on-chain attribution |
| `depth` | `"standard"` \| `"deep"` | No | Analysis depth (default: `"standard"`) |
| `diseaseTarget` | string | No | Disease or organism context |
| `notes` | string | No | Research notes |

**Response `201`:**
```json
{
  "id": 42,
  "sequence": "KWLRRVWRPQKI",
  "status": "completed",
  "bioactivityScore": 91,
  "bioactivityLabel": "antimicrobial",
  "confidenceScore": 84,
  "structurePrediction": "alpha_helix",
  "toxicityRisk": "low",
  "molecularWeight": 1634.2,
  "hydrophobicityIndex": 0.41,
  "chargeAtPH7": 4,
  "halfLife": "~8h (s.c.)",
  "annotationSuggestions": [...],
  "tags": ["antimicrobial", "alpha_helix"],
  "createdAt": "2026-05-13T00:00:00.000Z"
}
```

---

### `GET /api/sequences/:id`
Retrieve a sequence by ID.

**Response `200`:** Full `SequenceAnalysis` object (same as POST response).

---

## Feed

### `GET /api/feed`
Get the public research feed.

**Query parameters:**

| Param | Type | Description |
|---|---|---|
| `disease` | string | Filter by disease target |
| `minScore` | number | Minimum bioactivity score (0–100) |
| `sort` | `newest` \| `score` \| `annotations` \| `trending` | Sort order |
| `page` | number | Page number (default: 1) |
| `limit` | number | Results per page (default: 20, max: 100) |

**Response `200`:**
```json
{
  "items": [...],
  "total": 1247,
  "page": 1,
  "totalPages": 63
}
```

---

### `GET /api/feed/stats`
Platform-wide aggregate statistics.

**Response `200`:**
```json
{
  "totalAnalyses": 1247,
  "avgBioactivityScore": 71.4,
  "avgConfidenceScore": 76.2,
  "totalAnnotations": 3891,
  "totalVotes": 12043,
  "recentActivity": 34,
  "diseaseBreakdown": [
    { "disease": "antimicrobial", "count": 312 }
  ]
}
```

---

### `GET /api/feed/trending`
Top 10 sequences ranked by community vote count.

---

## Annotations

### `POST /api/annotations`
Submit a peer-review annotation.

**Request body:**
```json
{
  "sequenceId": 42,
  "userId": "your_wallet_address",
  "type": "confirm",
  "content": "Consistent with APD entry #1824. Confirmed membrane-active AMP."
}
```

| Type | Points | Description |
|---|---|---|
| `confirm` | +2 | Agree with AI classification |
| `challenge` | +3 | Dispute with evidence |
| `extend` | +5 | Add related data |
| `tag` | +2 | Add disease/target label |

---

### `GET /api/annotations/:sequenceId`
Get all annotations for a sequence.

---

### `POST /api/annotations/:id/vote`
Vote on an annotation.

```json
{ "direction": "up" }
```

---

## Token

### `GET /api/token/balance?userId=`
Get token balance and staking tier for a user.

### `GET /api/token/leaderboard`
Top contributors ranked by total $PEPTM earned.

---

## Governance

### `GET /api/governance/proposals?wallet=`
All proposals with user vote status.

### `POST /api/governance/proposals/:id/vote`
Cast a governance vote.

```json
{ "vote": "yes", "walletAddress": "your_wallet", "stakingTier": "pro" }
```

---

## Errors

| Code | Meaning |
|---|---|
| `400` | Bad request — check request body |
| `401` | Invalid or missing API key |
| `403` | Tier restriction — upgrade staking tier |
| `404` | Resource not found |
| `429` | Daily run limit reached — resets midnight UTC |
| `500` | Internal server error |
