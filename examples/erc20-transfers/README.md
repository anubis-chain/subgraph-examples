# Example: ERC-20 transfers on Anubis

Minimal Subgraph that indexes `Transfer` events for an ERC-20-style contract on **Anubis mainnet** (`network: anubis`).

## Before you build

1. Confirm the contract address and **deployment start block** on [AnubisScan](https://anubisscan.io/).
2. Edit `subgraph.yaml`: set `source.address` and `source.startBlock`.
3. If your ABI differs, replace `abis/ERC20.json` and regenerate handlers with Graph CLI.

## Commands

```sh
npm install
npm run codegen
npm run build
```

Anubis is supported on The Graph Network but **does not** currently have Subgraph Studio testing/staging. Prefer local Graph Node validation or `graph publish` to The Graph Network (see the root README).

```sh
# After build — publishes to The Graph Network (wallet flow)
npm run publish
```

## Privacy note

Only **public** on-chain events are indexable. Shielded / ZK-private data is not visible to Subgraphs.
