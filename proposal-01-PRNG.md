## New Proposal

**Cartesi PRNG**

A set of tools to generate random numbers on Cartesi's convenience layer.

**Project Description**
<!-- [Write the description long-form here, or else paste a [google drive link](https://url/) to a slide deck]
-->
The goal of this project is to create a framework for Cartesi that will make it easy for web3 developers to create DApps using Cartesi. The framework will:
* use React and TypeScript to create a modular and reusable component library that will provide a common PRNG (Pseudo-Random Nunber Generator) algorithm to Cartesi technology;
* use Web3.js and Cartesi's SDK to connect to the blockchain and the Cartesi Machine;
* be documented with Docusaurus;
* be published on npm and GitHub and maintained with semantic versioning.

Our project will offer three different ways to generate random numbers, each with its own advantages and disadvantages:
1. The first type uses block number, clock, and end user ethereum address to make a seed. This is a simple way to generate a seed that depends on some external factors that are hard to predict or manipulate. However, this type of PRNG may not be very secure or random, as it may be vulnerable to attacks or biases.
2. The second type uses a hash function for a number to generate the seed. This is a more secure and random way to generate a seed, as hash functions are designed to produce outputs that are unpredictable and uniformly distributed. However, this type of PRNG may require more transaction steps and may not be very efficient.
3. The third type uses Chainlink, which is a decentralized oracle network that provides access to various sources of randomness. This is a reliable and verifiable way to generate a seed, as Chainlink uses multiple nodes and cryptographic proofs to ensure the quality and integrity of the randomness. However, this type of PRNG may involve some costs and delays, as it depends on the availability and performance of the Chainlink network3.

**Value proposition**
<!-- [Why would someone use this product/service? Or how does it add value to the Cartesi ecosystem or tech stack?]
-->
We believe that creating these tools for developers we remove a important entry barrier for them. Random numbers are an essential part of many apps and DApps, specialy games. So, as we add this feature to the convenience layer, we expect to see an increase in Cartesi's adoption and in our community growth.

Here are some types of games that could benefit from this framework:
- A decentralized soccer game that uses Cartesi’s random algorithm to generate fair and unpredictable moves for both players;
- A decentralized card game that uses Cartesi’s off-chain computation to handle encryption algorithms and game logic to randomize the deck;
- RPG games that use PRNGs to determine loot drops, enemy spawns, critical hits, etc. 

## How you will use Cartesi, specifically?

<!--[Details about how you're using Cartesi specifically, and why it makes sense. This is the most important part of the proposal. If you are not precise, or your intention is not feasible, the proposal will be rejected.]-->

This project aims to add tooling to build DApps on Cartesi, and this is why it makes sense to have community's support. The following sections describe how each of the algorithms will interact with the Cartesi environment.

### Simple PRNG

The Simple PRNG scheme is unpredictable and verifiable, but it is biasable because the block proposer for a given slot can directly manipulate the block’s hash by manipulating the block’s body.

### VDF PRNG

1. Define a VDF function that takes twice as long as the block production time.
2. Send an input to initiate the process and obtain the block hash of the transaction block: BlockHash[0].
3. Compute `VDF(BlockHash[0])` and send the result to the contract.
4. Meanwhile, the network will produce the next block hash: `BlockHash[1]`.
5. The contract will combine the results and generate a random number. 
6. Send the number to the target contract.

```mermaid
stateDiagram-v2
  BlockHash0: Block 0
  BlockHash1: Block 1
  BlockHash2: Block 2
  VDF: VDF(BlockHash[0])
  Seed: PRNG(VDF(BlockHash[0]), BlockHash[1])
  state fork_state <<fork>>

  [*] --> BlockHash0
  state BlockHash0 {
    [*] --> FutureBlockConfigured
    FutureBlockConfigured --> [*]
  }
  BlockHash0 --> fork_state
  fork_state --> VDF
  fork_state --> BlockHash1

  state join_state <<join>>
  VDF --> join_state
  BlockHash1 --> join_state
  join_state --> BlockHash2
  state BlockHash2 {
    [*] --> Seed
    Seed --> [*]
  }
  BlockHash2 --> [*]
```
It takes 2 transactions.

### Hashed Turn Based Seed for PRNG

```mermaid
%%{
  init: {
    "theme": "dark",
    "sequence": {
      "mirrorActors": true,
      "messageAlign": "left"
    }
  }
}%%

sequenceDiagram
  actor Bob
  actor Alice
  participant Frontend as Frontend Framework
  autonumber
  Bob->>+Frontend: Bob's move
  activate Frontend
  Frontend->>Frontend: bob_hash = hash(bob_seed)
  Frontend->>+ConvenienceSmartContract: save bob_hash
  ConvenienceSmartContract->>-Frontend: saved
  Frontend-->>Bob: waiting Alice

  Alice->>Frontend: Alice's move
  activate Frontend
  Frontend->>Frontend: alice_hash = hash(alice_seed)
  Frontend->>+ConvenienceSmartContract: save alice_hash
  ConvenienceSmartContract->>-Frontend: saved
  Frontend-->>Alice: waiting seeds



  Frontend->>+ConvenienceSmartContract: bob_seed
  ConvenienceSmartContract->>ConvenienceSmartContract: check(hash, seed)
  ConvenienceSmartContract-->>-Frontend: ok
  Frontend->>+ConvenienceSmartContract: alice_seed
  ConvenienceSmartContract->>ConvenienceSmartContract: check(hash, seed)
  ConvenienceSmartContract->>ConvenienceSmartContract: mix_seed = hash(b_seed, a_seed)
  
  ConvenienceSmartContract->>+CartesiInput: random(mix_seed)
  CartesiInput-->>-ConvenienceSmartContract: ok

  ConvenienceSmartContract-->>-Frontend: ok
  Frontend-->>Alice: ok
  deactivate Frontend
  Frontend-->>Bob: ok
  deactivate Frontend

```

## Milestones

**Milestone 1: Simple PRNG**

* Duration: 1 months

* Deliverables: A simple method to generate random numbers
<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 1: $8,400 USD

**Milestone 2: VDF PRNG**

* Duration: 2 months

* Deliverables: Frontend framework and ConvenienceSmartContract
<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->

* Funds request (USD) for milestone 2: $16,800 USD

## Total funds requested

### $25,200 USD

<!--
Use of funds (specific breakdown):

* [List item: price in usd]
* [List item: price in usd]
* [List item: price in usd]
* [List item: price in usd]
* [List item: price in usd]
* [List item: price in usd]
-->
## About your Team

<!-- ordem alfabetica -->
<!--*[person 1]*-->
*Bruno Ochotorena*

Web3 Developer
https://www.linkedin.com/in/sandhilt

*Fabio Oshiro*

Web3 Specialist
https://www.linkedin.com/in/fabiooshiro

Contributions to the Cartesi community:

* [We ran a Solana DApp on Ethereum using Cartesi](https://blog.calindra.com.br/we-ran-a-solana-dapp-on-ethereum-using-cartesi-35da59ed1e47)
* [Open-Source: Cartesi’s Solana adapters](https://blog.calindra.com.br/solana-cartesi-under-the-hood-c4fbef266c89)

## Links and resources

Website: [https://calindra.tech/](https://calindra.tech/)  
Social: [Linkedin](https://www.linkedin.com/company/calindra/mycompany/)  
Github: [https://github.com/Calindra](https://github.com/Calindra)  

## ERC-20 Payee address

[your proposal will be rejected if you do not list a payee address. This address is where payments for the milestones will be made. The address must be a mainnet Ethereum ERC-20 address that can accept USDC.