# Anubis Subgraph Examples

> [!IMPORTANT]
> This repository was archived on 2026-09-17 and is kept as a historical example. Start new projects from [anubis-chain/subgraph-starter](https://github.com/anubis-chain/subgraph-starter), which receives current Anubis network and tooling updates.

Historical starter material for indexing **Anubis Chain** with [The Graph](https://thegraph.com/).

At the time of archive, Anubis was supported on The Graph Network. Current official network guide:

**[The Graph · Anubis Mainnet](https://thegraph.com/docs/en/supported-networks/anubis/)**

## Network parameters

These values are an archived snapshot. Confirm current values in the maintained [subgraph starter](https://github.com/anubis-chain/subgraph-starter) and official network guide before deploying.

| Item | Value |
| --- | --- |
| The Graph network id | `anubis` |
| Chain ID | `6714` (`eip155:6714`) |
| Native gas asset | `gasDAI` |
| Public RPC | `https://rpc.anubispace.org` |
| Explorer | [anubisscan.io](https://anubisscan.io/) |
| Protocol | EVM (`ethereum` in Graph CLI) |

Machine-readable copy: [`network.json`](./network.json).

## What this repo is for

Public chains usually do **not** put “cloud indexer infra” on GitHub. They publish:

1. A clear pointer to The Graph’s supported-network docs
2. Network identifiers developers must use in `subgraph.yaml`
3. Small **example Subgraphs** you can fork

That is what this repository is. It is **development source / examples**, not a hosted Graph Node deployment.

## What a Subgraph does

A Subgraph listens to public smart-contract events on Anubis, stores structured entities, and serves them over **GraphQL**. Frontends, dashboards, and bots query that API instead of scanning every block themselves.

**Selective privacy:** only data that is public on-chain can be indexed. Events from transparent transactions are indexable; data inside shielded (PLONK ZK) transactions is not.

## Studio status at archive time

As of 2026-09-17, Anubis was on The Graph Network but **did not have Subgraph Studio testing/staging**. The available options were:

- Validate with a **local Graph Node** pointed at `anubis:https://rpc.anubispace.org`
- Or **`graph publish`** directly to The Graph Network (Indexers that support Anubis pick it up; curation signal helps)

## Quick start

```sh
npm install -g @graphprotocol/graph-cli@latest
graph --version
```

Historical initialization reference (use the maintained starter for active projects):

```sh
graph init
# Protocol: ethereum
# Ethereum network: anubis
# Contract address + ABI from https://anubisscan.io/
# startBlock: contract deployment block
```

Or start from the example in this repo:

```sh
cd examples/erc20-transfers
npm install
# Edit subgraph.yaml address + startBlock first
npm run codegen
npm run build
```

Publish (wallet flow; protocol contracts live on Arbitrum One — that is The Graph’s settlement layer, not Anubis):

```sh
graph publish
```

## Examples

| Path | Description |
| --- | --- |
| [`examples/erc20-transfers`](./examples/erc20-transfers) | Minimal ERC-20 `Transfer` indexer template for `network: anubis` |

## License

MIT — see [LICENSE](LICENSE).
