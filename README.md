# NWC-DRE v0.1

**NWC Categorization System — Digital Real Estate Gate Specification**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/status-draft-orange.svg)](https://github.com)

A globally standardized classification and indexing schema for **Digital Real Estate** objects using micro-BTL encoding.

## Features

- 🌐 Chain-agnostic digital property indexing (Bitcoin, Lightning, Ethereum, Solana, Filecoin, Arweave)
- 📦 Micro-BTL canonical encoding for deterministic hashing
- 🔗 Interoperable with BTL (Binary Transfer Language) and NWC G0 Gate
- 🏗️ Support for parcels, spaces, units, and virtual properties
- ✅ JSON Schema validation included

## Quick Start

```bash
npm install
npm test
```

## Specification

See [docs/nwc-dre-v0.1.md](docs/nwc-dre-v0.1.md) for the complete RFC-style specification.

## Example

**JSON Format:**
```json
{
  "chain": "btc",
  "chain_id": "b61b0172...",
  "owner_wallet": "bc1qxyz...",
  "object_type": "parcel",
  "host": "ipfs:QmX...",
  "namespace": "ens:landplot.eth",
  "persistence": "permanent",
  "sdk": ["unity2021"],
  "links": ["ipfs:QmManifest"]
}
```

**Micro-BTL Format:**
```
1(type=chain;btc).1(type=cid;b61b0172...).1(type=wallet;bc1qxyz...).1(type=type;parcel).1(type=host;ipfs:QmX...).1(type=namespace;ens:landplot.eth).1(type=persist;permanent).1(type=sdk;unity2021).1(type=link;ipfs:QmManifest)
```

## Repository Structure

```
NWC-DRE-v0.1/
├── docs/
│   └── nwc-dre-v0.1.md          # Full specification
├── schema/
│   └── nwc-dre-v0.1.schema.json # JSON Schema
├── src/
│   └── dre-microbtl-parser.ts   # Parser & serializer
├── examples/
│   ├── example-dre.json         # Example JSON
│   └── example-dre.btl          # Example micro-BTL
├── tests/
│   └── parser.test.ts           # Unit tests
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

## Integration with NWC G0

DRE is the 6th slot in the NWC BTL order:

```
publish.music.mphd.research.art.dre.5pac3.realty.juris.ph
```

Full NWC record example:
```
0.0.0.0.0.1(DRE_MICRO).0.0.1(type=ISO3166;US).0
```

## Validation Rules

1. If `chain != offchain`, a `chain_id` SHOULD be present
2. `object_type` MUST be non-empty
3. Known prefixes must be used for host pointers (`ipfs:`, `arweave:`, `http:`)
4. Persistence must be from allowed enum: `permanent`, `renewable`, `ephemeral`, `unknown`
5. Wallet format must match basic chain regex

## Related Projects

- [BTL (Binary Transfer Language)](../1.0.1-BTL/)
- [NWC G0 Gate System](../NWC/)

## License

MIT License - See [LICENSE](LICENSE) for details.

## Authors

- GPT + Andrew

## Status

**Draft v0.1** - Subject to breaking changes before v1.0 release.

