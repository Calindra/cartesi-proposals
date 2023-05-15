## New Proposal

**Cartesi PRNG**

A set of tools to generate random numbers on Cartesi's convenience layer.

**Project Description**
<!-- [Write the description long-form here, or else paste a [google drive link](https://url/) to a slide deck]
-->
The goal of this project is to create a framework for Cartesi that will make it easy for web3 developers to create DApps using Cartesi. The framework will:
* use React and TypeScript to create a modular and reusable component library that will provide a common PRNG (Pseudo-Random Number Generator) algorithm to Cartesi technology;
* use Web3.js and Cartesi's SDK to connect to the blockchain and the Cartesi Machine;
* be documented with Docusaurus;
* be published on npm and GitHub and maintained with semantic versioning.

Our project will offer three different ways to generate random numbers, each with its own advantages and disadvantages:
1. The first type uses block number, clock, and end user ethereum address to make a seed. This is a simple way to generate a seed that depends on some external factors that are hard to predict or manipulate. However, this type of PRNG may not be very secure or random, as it may be vulnerable to attacks or biases.
2. The second type uses VDF - Verifiable Delay Function, which will produce an unpredictable result in the future while the blockchain network is making another block. That way, the resulting seed cannot be predicted or biased. Also, the VDF result can be provided by anyone to avoid tampering.
3. The third type uses a hash function to commit to a number that will be revealed in the future and generate the seed. This is a more secure and random way to generate a seed, as hash functions are designed to produce outputs that are unpredictable and uniformly distributed. However, this type of PRNG may require more transaction steps and may not be very efficient.

**Value proposition**
<!-- [Why would someone use this product/service? Or how does it add value to the Cartesi ecosystem or tech stack?]
-->
We believe that creating these tools for developers we remove a important entry barrier for them. Random numbers are an essential part of many apps and DApps, specially games. So, as we add this feature to the convenience layer, we expect to see an increase in Cartesi's adoption and in our community growth.

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

For this type of PRNG, we will use a VDF - Verifiable Delay Function for cryptography. A VDF is a function that takes a certain amount of time to compute, and cannot be accelerated through parallelization or additional processors. Once computed, the output can be quickly verified by anyone.

1. Define a VDF that takes twice as long as the block production time.
2. Send an input to initiate the process and obtain the block hash of the transaction block: BlockHash[0].
3. Compute `VDF(BlockHash(N))` and send the result to the contract.
4. Meanwhile, the network will produce the next block hash: `BlockHash(N+1)`.
5. The contract will combine the VDF results with the block hash and generate a random number. 
6. Send the number to the target contract.

![](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesi_proposal_prng_1.png?raw=true)
 
This algorithm can be exploited by the leader only, if the leader has a sequential processing power more than twice as high as the network's. To illustrate, let's imagine a hypothetical scenario: The leader generates the blockhash, calculates the result of the VDF and if it is not favorable, he generates another blockhash.

### Hashed Turn Based Seed for PRNG

Based on the commit-reveal but applied to PvP games where the result can be WO.

The commit-reveal is a cryptographic scheme that allows players to hide their choices until they are revealed later. It is used to prevent front-running attacks, where someone can see the transactions in the pool and act before them. The commit-reveal has two phases: a commit phase, where the players send their hashed choices to a smart contract, and a reveal phase, where the players reveal their choices and the contract verifies them. The contract then uses the choices to generate a random outcome for the game.

PvP games are player versus player games, where two players compete against each other. Examples of PvP games are rock-paper-scissors, even or odd, or poker.

The result can be WO means that the result can be a walkover, which is when one player wins by default because the other player does not show up, forfeits, or fails to reveal their choice. 

![](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesi_proposal_prng_2.png?raw=true)

## Milestones

**Milestone 1: Simple PRNG**

* Duration: 4 weeks

* Deliverables:
  1. An automated build and test process of the npm library artifact using Github Actions;
  2. An automated packaging and release process for the npm library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that explains the project;
  5. A smart contract with a new attribute in input_metadata to receive blockhash;
  6. A library for the Cartesi Machine that obtains all the seeds and produces a random number sequence

A simple method to generate random numbers
<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 1: $8,000 USD

**Milestone 2: VDF PRNG**

* Duration: 6 weeks

* Deliverables: 
  1. An automated build and test process of the library artifact using Github Actions;
  2. An automated packaging and release process for the npm library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that provides an overview of the project;
  5. A smart contract with:
      1. a new method to verify the VDF result;
      2. a new method to register the configuration;
      3. a new attribute in input_metadata to receive the seed;
  6. A library for the Cartesi Machine that obtains the generated seed and produces a random number sequence
<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->

* Funds request (USD) for milestone 2: $12,000 USD

**Milestone 3: Hashed Turn Based Seed for PRNG**

* Duration: 8 weeks

<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->
* Deliverables: 
  1. An automated build and test process of the library artifact using Github Actions;
  2. An automated packaging and release process for the npm library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that provides an overview of the project;
  5. A smart contract with:
      1. a new method to register the commit hash;
      2. a new method to check the revealed result;
      3. a new attribute in input_metadata to receive the seed;
  6. A library for the Cartesi Machine that obtains the generated seed and produces a random number sequence

* Funds request (USD) for milestone 3: $16,000 USD

## Total funds requested

### $36,000 USD

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
LinkedIn: [/in/sandhilt](https://www.linkedin.com/in/sandhilt)

*Fabio Oshiro*

Web3 Specialist
LinkedIn: [/in/fabiooshiro](https://www.linkedin.com/in/fabiooshiro)

Contributions to the Cartesi community:

* [We ran a Solana DApp on Ethereum using Cartesi](https://blog.calindra.com.br/we-ran-a-solana-dapp-on-ethereum-using-cartesi-35da59ed1e47)
* [Open-Source: Cartesi’s Solana adapters](https://blog.calindra.com.br/solana-cartesi-under-the-hood-c4fbef266c89)

## Links and resources

Website: [calindra.tech](https://calindra.tech/) 

LinkedIn: [/company/calindra](https://www.linkedin.com/company/calindra)

Github: [/Calindra](https://github.com/Calindra) 

## ERC-20 Payee address

<!-- [your proposal will be rejected if you do not list a payee address. This address is where payments for the milestones will be made. The address must be a mainnet Ethereum ERC-20 address that can accept USDC. -->
0x7cE0AA3DFbB8abdCD0Ea426769ffD21302DAA8B8
