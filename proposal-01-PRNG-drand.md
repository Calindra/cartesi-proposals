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

### Drand PRNG

![Diagram](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesi_proposal_prng_5-drand.png?raw=true)

Bob starts a new random number process by sending a specific input to the Cartesi Rollups. This input will be recognized by the Convenience Middleware inside the Cartesi Machine and stored until Drand’s beacon arrives. The Convenience API will inspect the Cartesi Machine periodically to see if there is any input stored waiting for a beacon. When the Convenience API detects an awaiting input, it will request the latest beacon from the Drand network and send this beacon to the Cartesi Rollups.

The Convenience Middleware will calculate the beacon’s creation time by discounting a safe amount of seconds to prevent any user’s prior knowledge of the beacon. With that safe time, it will load the pending inputs sent before that timestamp and add a seed property to the input metadata. Finally, the DApp will receive the input with the seed metadata to generate a random number.

When an input requesting a random number arrives, it will force any subsequent input (that needs or does not need a random number) to be stored until the next Drand’s beacon arrives. This rule is to maintain the correct sequence of input execution.

We know that the user’s DApp calls the rollup server, we change the arrow direction to make the problem easier to think about. In reality, DApps will call our middleware and our middleware will call the rollup server.

## Milestones

**Milestone 1: Convenience POC**

POC to demonstrate the use case of generating a random number with the Convenience tools.

* Duration: 8 weeks

* Deliverables:
  1. An automated build and test process of the npm library artifact using Github Actions;
  2. An automated packaging and release process for the npm library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that explains the project;
  5. A Convenience Middleware with a new attribute in input_metadata to receive the generated seed;
  6. A library for the Cartesi Machine that obtains all the seeds and produces a random number sequence;
  7. A Convenience API (web2 application) that reads the drand's beacon and sends it to Cartesi Rollups as needed;
  8. An example of a simple game project that can help new developers learn how to use the solution;

<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 1: $10,500 USD

**Milestone 2: Convenience Edge Cases**

* Duration: 5 weeks

* Deliverables: 
  1. A list of edge cases (Drand signature error, drand timeout);
  2. An method to update the Drand's public key;
  3. An automated tests to cover edge cases;
<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->

* Funds request (USD) for milestone 2: $6,563 USD

**Milestone 3: Convenience Web3 Client**

* Duration: 3 weeks

<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->
* Deliverables: 
  1. An automated build and test process of the library artifact using Github Actions;
  2. An automated packaging and release process for the npm library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that provides an overview of the project;

* Funds request (USD) for milestone 3: $3,937 USD

## Total funds requested

### $32,000 USD

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
*Calindra*

Calindra helps our partners to execute their digital strategy through a experienced and talented team.

[Calindra Team](https://calindra.tech/team.html)

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
