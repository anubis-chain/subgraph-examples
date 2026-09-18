# Anubis Subgraph Examples (archived)

This repository is archived and no longer maintained.

For new projects, use **[anubis-chain/subgraph-starter](https://github.com/anubis-chain/subgraph-starter)**. It contains the current Anubis network settings and build instructions.

## Archived example

[`examples/erc20-transfers`](./examples/erc20-transfers) is a minimal example that indexes ERC-20 `Transfer` events with The Graph.

The network values below are retained only for historical reference:

| Parameter | Value |
| --- | --- |
| The Graph network id | `anubis` |
| Chain ID | `6714` (`eip155:6714`) |
| RPC | `https://rpc.anubispace.org` |
| Explorer | [anubisscan.io](https://anubisscan.io/) |

Do not use this archive as the starting point for a production deployment. Check the maintained starter and [The Graph's Anubis network page](https://thegraph.com/docs/en/supported-networks/anubis/) for current information.

## Build the archived example

```sh
cd examples/erc20-transfers
npm install
# Set the contract address and deployment block in subgraph.yaml.
npm run codegen
npm run build
```

## License

MIT — see [LICENSE](LICENSE).
