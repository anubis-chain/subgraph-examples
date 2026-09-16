# Anubis Subgraph Examples

Starter material for indexing **Anubis Chain** with [The Graph](https://thegraph.com/).

Anubis is supported on The Graph Network. Official network guide:

**[The Graph · Anubis Mainnet](https://thegraph.com/docs/en/supported-networks/anubis/)**

## Network parameters

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

## Studio limitation (important)

Anubis is on The Graph Network but **does not currently have Subgraph Studio testing/staging**. Do not expect the Studio playground path. Options:

- Validate with a **local Graph Node** pointed at `anubis:https://rpc.anubispace.org`
- Or **`graph publish`** directly to The Graph Network (Indexers that support Anubis pick it up; curation signal helps)

## Quick start

```sh
npm install -g @graphprotocol/graph-cli@latest
graph --version
```

Initialize against your own contract (recommended for real apps):

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

## Related Anubis links

- Explorer: https://anubisscan.io/
- Faucet (testnet): https://anubisfaucets.com / source: [anubis-faucet](https://github.com/anubis-chain/anubis-faucet)
- Multisig dapp: https://guardsafe.org/
- DEX: https://rocketswap.org/

## License

MIT — see [LICENSE](LICENSE).
