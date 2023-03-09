# Crowdsourced Resources for Canto Builders

![](https://pbs.twimg.com/profile_banners/1583707619474042881/1675108605/1500x500)

Welcome to a crowdsourced directory of resources for Canto Online Hackathon builders and other community members. Not sure where to start? See the FAQ below for answers to builders' most frequent questions.

Is this directory missing something? Make a [contribution](contributing.md).

## Frequently Asked Questions (FAQ)

A list of Canto builders' most Frequently Asked Questions (FAQ), filtered by topic.

### Getting Started

##### How do I connect to Canto?

With chain ID 7700 and an RPC of your choice e.g. `https://canto.gravitychain.io/`.

##### How do I get Canto?

Ideally, [bridge over](https://docs.canto.io/user-guides/bridging-assets/to-canto) from Ethereum or Cosmos Hub, or other networks using Synapse Network.

##### Is there a faucet?

The Canto Public Messaging Service has [a faucet](https://www.cpms.wtf/), but you will likely want to bridge over anyway.

### EVMness and Network Specs

##### What tooling can I use to build on Canto?

The Canto EVM is fully EVM-compatible. For development, Hardhat, Truffle, Foundry, Remix, and others work perfectly.

##### Why doesn't my Forge deployment script work?

Forge deployment scripts send concurrent transactions which cause issues with Ethermint. Consider using the `--slow` flag or deploying manually.

##### What is the block time?

Approximately 6 seconds.

##### How are gas fees determined?

The Canto network uses a modified EIP-1559 gas model *without* priority fees. The minimum base fee is 1000 acanto (the equivalent of gwei) and self-adjusts based on how full blocks are.

### RPCs, Nodes, APIs

##### What RPC should I use to connect to Canto?

`https://canto.gravitychain.io/`, `https://canto.slingshot.finance/`, and `https://canto.neobase.one/` are the most reliable.

##### Is there a websockets (WSS) RPC I can use?

Yes, `wss://canto.gravitychain.io:8546`.

##### The throughput/reliability of the public RPCs isn't good enough, what should I do?

If your application requires very high throughput/reliability, consider [setting up your own node](https://docs.canto.io/canto-node/validators).

##### Is there a public archive RPC?

While some of the public RPCs have archival data, there are no fully unpruned public archive RPC nodes. If you need one, consider [setting up your own archive node](https://docs.canto.io/canto-node/archive-node).

##### Are there any data APIs for Canto?

[Transpose](https://www.transpose.io/) has both REST and SQL APIs exposing Canto chain data. [Covalent](https://www.covalenthq.com/) also has a REST API for Canto chain data.

### Testnet

##### How do I connect to the testnet?

Use the public RPC `canto-testnet.plexnode.wtf` and chain ID 7701 in your development suite or wallet of choice.

##### How do I get testnet tokens?

Join the [Canto Discord](https://discord.gg/canto) and locate the #canto-testnet-faucet channel. In this channel, use the `/driptestnet {address}` command.

##### What about the old testnet?

There was previously a testnet with chain ID 740. Due to incompatibility with CSR and validator sync issues, this testnet was deprecated and a new testnet was released with the details above.

### Free Public Infrastructure

##### How do I integrate the Canto DEX and Lending Market?

See the [DEX and Lending Market](https://docs.canto.io/evm-development/dex-and-lending-market) section of the docs for an overview of their architectures and links to source contracts.

### Contract Secured Revenue (CSR)

##### If multiple contracts are used in a single call, which of them gets the CSR revenue?

Only the entry contract.

##### Where do I find more information about CSR?

In the [CSR docs](https://docs.canto.io/evm-development/contract-secured-revenue).

##### What's the address for Turnstile, and where do I find the code?

0xEcf044C5B4b867CFda001101c617eCd347095B44 and [here](https://github.com/Canto-Network/Canto/blob/csr/contracts/turnstile.sol).

##### Can I `register` an EOA for CSR?

**No.** The Turnstile smart contract allows an EOA to call the `register` method. However, the `x/csr` module operating on the Cosmos-side **will not save this registration**, and no revenue will accrue to the NFT, even if you `assign` valid smart contracts to it.

### Explorers

##### How do I verify my contracts on the explorer?

Use [Sourcify](https://sourcify.dev/).

##### Why can't I verify my contracts on the explorer?

Verification of some contracts is not supported by the explorer. Contributors are aware of this and working on solutions.

### Oracles

##### Are there any oracles on Canto?

Yes, [RedStone](https://redstone.finance/) and [Scry](https://canto.dapp.scry.finance/).

##### Is there a VRF oracle on Canto?

Not at this time.

### DAO Tooling

##### Is there a multisig (a'la Safe) on Canto?

Yes, [Canto Safe](https://safe.neobase.one/).

##### Is there any DAO tooling on Canto?

Yes, [CantoDao](https://cantodao.com/).

### Grants and Promotion

##### Are there grants (or cover costs) for builders/validators?

The Canto Online Hackathon supports promising projects with generous $CANTO prizes. Outside of this, there are no established grant programs for builders or validators.

##### Can Canto social channels promote my project?

Canto social channels are run by various contributors. For your best chances at cross-promotion on these channels, make a professional and interesting Tweet about your project.

### Repositories

##### Where is the core Canto network repository?

https://github.com/Canto-Network/Canto

##### Where do I find the source code for IBC ERC20s and Turnstile?

In the `contracts` folder of the core Canto repo: https://github.com/Canto-Network/Canto/tree/main/contracts

##### Where do I find the Cosmos-side logic for the GovShuttle/CSR/other modules?

In the `x` (modules) folder of the core Canto repo: https://github.com/Canto-Network/Canto/tree/main/x

##### Where do I find the source code for Canto's Free Public Infrastructure (Canto Lending Market and DEX)?

https://github.com/Canto-Network/clm