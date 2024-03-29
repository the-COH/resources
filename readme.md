# Crowdsourced Resources for Canto Builders

![](banner.jpg)

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

Yes, `wss://canto.gravitychain.io:8546` and `wss://canto.dexvaults.com/ws`.

##### Is there anywhere I can get a dedicated Canto node?

Yes, [Ansybl](https://www.ansybl.io/) hosts dedicated Canto nodes, including both full and archive nodes, for a monthly fee.

##### The throughput/reliability of the public RPCs isn't good enough, what should I do?

If your application requires very high throughput/reliability, consider renting a dedicated Canto node (see above) or [setting up your own node](https://docs.canto.io/canto-node/validators).

##### Is there a public archive RPC?

`https://rpc.cantoarchive.com` is a public archive RPC node, with rate limiting allowing up to 50 requests per 10 seconds. As above, for more throughput, consider renting a dedicated node or [setting up your own *archive* node](https://docs.canto.io/canto-node/archive-node).

##### Are there any data APIs for Canto?

Data providers [Transpose](https://www.transpose.io/) and [Covalent](https://www.covalenthq.com/) have REST and SQL APIs exposing Canto chain data.

Additionally, the Blockscout explorers for mainnet ([tuber.build](https://tuber.build/)) and testnet ([testnet.tuber.build](https://testnet.tuber.build/)) support the default Blockscout [API endpoints](https://tuber.build/api-docs).

### Testnet

##### How do I connect to the testnet?

Use the public RPC `canto-testnet.plexnode.wtf` and chain ID 7701 in your development suite or wallet of choice.

##### How do I get testnet $CANTO?

Use the web-based faucet at https://www.cantofaucet.com/. Alternatively, use the Discord faucet by entering the `/driptestnet {address}` command in the #canto-testnet-faucet channel of the [Canto Discord](https://discord.gg/canto).

 Both faucets disperse 50 $CANTO per address per 24 hours.

##### How do I get testnet $NOTE?

The Discord faucet mentioned above also disperses 15 $NOTE each time it is used. If that's not enough, the Canto DEX testnet deployment has $CANTO <> $NOTE liquidity and can be interacted with programatically or through [LeetSwap](https://app.leetswap.finance/#/swap) (after switching to Canto testnet in the connected wallet).

##### Can I get other ERC20 tokens (USDC, USDT) on Canto testnet?

The Canto DEX testnet deployment also has liquidity for the $NOTE <> $USDC and $NOTE <> $USDT pairs. As above, it can be interacted with programatically or through [LeetSwap](https://app.leetswap.finance/#/swap).

##### What about the old testnet?

There was previously a testnet with chain ID 740. Due to incompatibility with CSR and validator sync issues, this testnet was deprecated and a new testnet (chain ID 7701).

### Free Public Infrastructure

##### How do I integrate the Canto DEX and Lending Market?

See the [DEX and Lending Market](https://docs.canto.io/evm-development/dex-and-lending-market) section of the docs for an overview of their architectures and links to source contracts.

### Other Contracts

##### Is there a Multicall deployment on Canto?

Yes, you can use Multicall1 and 2 on both mainnet and testnet:

|            | Mainnet                                    | Testnet                                    |
|------------|--------------------------------------------|--------------------------------------------|
| Multicall1 | 0x210b88d5Ad4BEbc8FAC4383cC7F84Cd4F03d18c6 | 0xe536cF7B00069894da25faC787d7aD9D211a2C1A |
| Multicall2 | 0x637490E68AA50Ea810688a52D7464E10c25A77c1 | 0x0e356B86FA2aE1bEB93174C18AD373207a40F2A3 |

### Contract Secured Revenue (CSR)

##### If multiple contracts are used in a single call, which of them gets the CSR revenue?

Only the entry contract.

##### Where do I find more information about CSR?

In the [CSR docs](https://docs.canto.io/evm-development/contract-secured-revenue).

##### What's the address for Turnstile, and where do I find the code?

0xEcf044C5B4b867CFda001101c617eCd347095B44 and [here](https://github.com/Canto-Network/Canto/blob/csr/contracts/turnstile.sol).

##### Can I `register` an EOA for CSR?

**No.** The Turnstile smart contract allows an EOA to call the `register` method. However, the `x/csr` module operating on the Cosmos-side **will not save this registration**, and no revenue will accrue to the NFT, even if you `assign` valid smart contracts to it.

##### How do I split CSR between multiple recipients?

CSR does not have native support for multiple fee recipients; however, Turnstile NFTs are composable and can be deposited to protocols like [Canto Splits](https://splits.neobase.one/) for trustless revenue sharing.

### Explorers

##### Does Canto have a blockchain explorer?

Canto has at least four contributor-operated block explorers: [tuber.build](https://tuber.build/), [mintscan.io/canto](https://www.mintscan.io/canto) [Cantoscan](https://cantoscan.xyz/), and [GaCanto](https://www.gacanto.com/).

##### How do I verify my contracts on the explorer?

For tuber.build, use [Sourcify](https://sourcify.dev/). You can also verify through Forge using Sourcify:

`forge verify-contract <contractAddress> src/<fileName>.sol:<contractName> --chain-id 7700 --verifier sourcify`

...or Blockscout:

`forge verify-contract <contractAddress> src/<fileName>.sol:<contractName> --chain-id 7700 --verifier-url https://evm.explorer.canto.io/api --verifier blockscout`

##### Why can't I verify my contract(s)?

Verification of some contracts is not supported by the explorer. Contributors are aware of this and working on solutions.

##### Is there a testnet explorer?

Yes, [testnet.tuber.build](https://testnet.tuber.build).

### Oracles

##### Are there any oracles on Canto?

Yes:
* [RedStone](https://redstone.finance/)
* [Scry](https://canto.dapp.scry.finance/)
* [Pyth](https://docs.pyth.network/pythnet-price-feeds/evm)

Note that the [Canto DEX router](https://github.com/Canto-Network/clm/blob/main/src/Swap/BaseV1-periphery.sol) deployed at [0xa252eEE9BDe830Ca4793F054B506587027825a8e](https://evm.explorer.canto.io/address/0xa252eEE9BDe830Ca4793F054B506587027825a8e) also has price oracle functionality.

##### Is there a VRF oracle on Canto?

Yes, Scry offers a [VRF oracle](https://docs.scry.finance/docs/morpheus/vrf-hash-ranch).

### NFTs

##### How can I prove ownership of an NFT on mainnet on Canto?

See [NFT Global Entry](https://github.com/the-COH/chapter_1_season_4/tree/main/nft-global-entry).

##### Is [Delegate.Cash](https://delegate.cash/) deployed to Canto?

Yes.

### DAO Tooling

##### Is there a multisig (a'la Safe) on Canto?

Yes, [Canto Safe](https://safe.neobase.one/) on the Canto EVM; [Pyxis Safe](https://safe.serenity.aura.network/welcome) on Canto bridge/native layer.

##### Is there any DAO tooling on Canto?

Yes, [CantoDao](https://cantodao.com/) and [Canto Collectives](https://canto.kali.gg/) by Kali.

### Grants and Promotion

##### Are there grants (or cover costs) for builders/validators?

The Canto Online Hackathon supports promising projects with generous $CANTO prizes. Outside of this, there are no established grant programs for builders or validators.

##### Can Canto social channels promote my project?

Canto social channels are run by various contributors. For your best chances at cross-promotion on these channels, make a professional and interesting Tweet about your project.

### Bridges and Interoperability

Canto is supported by the following bridges and interoperability protocols:

- Gravity Bridge
- LayerZero (Canto endpoint: 0x9740FF91F1985D8d2B71494aE1A2f723bb3Ed9E4)
- Synapse Bridge
- Multichain
- Celer cBridge

### Repositories

##### Where is the core Canto network repository?

https://github.com/Canto-Network/Canto

##### Where do I find the source code for IBC ERC20s and Turnstile?

In the `contracts` folder of the core Canto repo: https://github.com/Canto-Network/Canto/tree/main/contracts

##### Where do I find the Cosmos-side logic for the GovShuttle/CSR/other modules?

In the `x` (modules) folder of the core Canto repo: https://github.com/Canto-Network/Canto/tree/main/x

##### Where do I find the source code/ABIs for Canto's Free Public Infrastructure (Canto Lending Market, DEX, and $NOTe)?

https://github.com/Canto-Network/clm/tree/main/src