# SDK Guide

The `peptoma-sdk` package provides a typed TypeScript/JavaScript client for the full PEPTOMA API.

**GitHub:** [github.com/peptoma/sdk](https://github.com/peptoma/sdk)  
**npm:** [npmjs.com/package/peptoma-sdk](https://www.npmjs.com/package/peptoma-sdk)

## Installation

```bash
npm install peptoma-sdk
pnpm add peptoma-sdk
yarn add peptoma-sdk
```

Requires Node.js ≥ 18 (native `fetch`). Works in Bun and Deno.

## Quick Start

```typescript
import { PeptomaClient } from "peptoma-sdk";

const client = new PeptomaClient({
  apiKey: process.env.PEPTOMA_API_KEY!,
});

const result = await client.sequences.analyze({
  sequence: "KWLRRVWRPQKI",
  depth: "deep",
  diseaseTarget: "MRSA",
});

console.log(result.bioactivityScore);  // 91
console.log(result.toxicityRisk);      // "low"
```

## Available Resources

| Resource | Methods |
|---|---|
| `client.sequences` | `.analyze()`, `.get()` |
| `client.feed` | `.list()`, `.stats()`, `.trending()` |
| `client.annotations` | `.list()`, `.create()`, `.vote()` |
| `client.token` | `.balance()`, `.leaderboard()` |
| `client.copilot` | `.ask()`, `.research()`, `.compare()`, `.buildProtocol()` |
| `client.citations` | `.forks()`, `.citations()`, `.fork()` |
| `client.teams` | `.create()`, `.list()`, `.get()`, `.invite()` |
| `client.keys` | `.list()`, `.generate()`, `.revoke()` |

Full reference: [github.com/peptoma/sdk](https://github.com/peptoma/sdk)
