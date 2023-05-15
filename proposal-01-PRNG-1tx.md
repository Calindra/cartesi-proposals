## New Proposal

**Cartesi PRNG**

This project is a component of a larger set of tools for generating random numbers on Cartesi’s convenience layer.

**Project Description**
<!-- [Write the description long-form here, or else paste a [google drive link](https://url/) to a slide deck]
-->
The goal of this project is to create a framework for Cartesi that will make it easy for web3 developers to create DApps using Cartesi. The framework will:
* use React and TypeScript to create a modular and reusable component library that will provide a common PRNG (Pseudo-Random Number Generator) algorithm to Cartesi technology;
* use Web3.js and Cartesi's SDK to connect to the blockchain and the Cartesi Machine;
* be documented with Docusaurus;
* be published on npm and GitHub and maintained with semantic versioning.

Our project will offer a easy and affordable way to generate random numbers.

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

This project aims to add tooling to build DApps on Cartesi, and this is why it makes sense to have community's support. The following sections describe how this algorithm will interact with the Cartesi environment to generate a trustless random number.

### Convenience PRNG

![Diagram](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesi_proposal_prng_3-1tx.png?raw=true)

Bob starts a new random number process by calling the REST Convenience API. Bob’s payload includes a signed receipt that can be executed by the Convenience layer if Bob fails to reveal his secret. The Convenience API responds with a signed commit and receipt.

We know that the user’s dApp calls the rollup server, we change the arrow direction to make the problem easier to think about. In reality, dApps will call our middleware and our middleware will call the rollup server.

Neither Bob nor Convenience can claim counterpart's share until Bob completes step 3, which involves Bob’s secret seed and Convenience’s signed commit.

There is a certain amount of money that must be staked as a guarantee to ensure the disclosure of the secrets.


## Milestones

**Milestone 1: Convenience MVP**

The MVP to demonstrate the use case of generating a random number with the Convenience tools.

* Duration: 4 weeks

* Deliverables:
  1. An automated build and test process of the npm library artifact using Github Actions;
  2. An automated packaging and release process for the npm library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that explains the project;
  5. A smart contract with a new attribute in input_metadata to receive blockhash;
  6. A library for the Cartesi Machine that obtains all the seeds and produces a random number sequence

<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 1: $8,000 USD

**Milestone 2: Convenience Edge Cases**

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

**Milestone 3: Convenience Web3 Client**

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
