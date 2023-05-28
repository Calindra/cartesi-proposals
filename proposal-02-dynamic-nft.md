## New Proposal

*Dynamic NFT*

A thrustless way to create and update NFT metadata and images

**Project Description**
<!-- [Write the description long-form here, or else paste a [google drive link](https://url/) to a slide deck]
-->
This project aims to create dynamic NFTs using the Cartesi Machine. Dynamic NFTs are NFTs that can change their characteristics according to certain circumstances that trigger their Cartesi Programs. They have metadata that describes their general and specific fields, which can be different for each NFT collection. They can change because of a special event like a DAO decision, or a video game progress.

The main challenge of this project is to enable the creation and updating of dynamic NFTs "on-chain" using the Cartesi Machine. Currently, most NFTs store the image and the metadata entirely off-chain or without any governance mechanism.

To overcome this challenge, We propose to create a public folder inside the Cartesi Machine that can store and update the images and metadata of the dynamic NFTs. The public folder would allow developers and users to access and modify the files on the Cartesi Machine. The public folder would also enable collaborative applications that require multiple parties to access the same files.

The main benefit of this project is that it would enable the creation of dynamic NFTs that are fully decentralized and transparent. The dynamic NFTs would not rely on any off-chain services or data sources to change their characteristics. The dynamic NFTs would also be verifiable by anyone who can inspect the state of the Cartesi Machine.

**Value proposition**
<!-- [Why would someone use this product/service? Or how does it add value to the Cartesi ecosystem or tech stack?]-->
Unlike common NFTs that store their metadata and assets off-chain, our dynamic NFTs in the Cartesi's public folder are created and updated transparently using the unique feature of the Cartesi technology.

## How you will use Cartesi, specifically?

<!--[Details about how you're using Cartesi specifically, and why it makes sense. This is the most important part of the proposal. If you are not precise, or your intention is not feasible, the proposal will be rejected.]-->

This project aims to add tooling for building DApps on Cartesi, which is why it makes sense to have the support of the community. The power of Cartesi's technology could open up new horizons in the crypto space. While we are currently revolutionizing the backend side by replacing it with smart contracts, we have the opportunity to advance frontend technology, which is lagging behind in terms of trustless, security, and ownership.

## Milestones

**Milestone 1: Public Folder**

A public folder that can be accessed through HTTP and is compatible with wallets for retrieving the NFTs.

* Duration: 6 weeks

* Deliverables: (draft)
  1. An automated build and test process of the rust library artifact using Github Actions;
  2. An automated packaging and release process for the rust library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that explains the project;

<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 1: $7,875 USD

**Milestone 2: Game Example**

A simple NFT game example that demonstrates the functionality of the first milestone.  

Samurai Monkey Battle

There is only one characteristic: dexterity. When the user buys a monkey, the DApp will generate a random face and dexterity value. Each player chooses a monkey. If the monkey suffers a hit, it loses. The success of the hit will be calculated by: random > (dexA / (dexB + dexA)). If both monkeys get hit, it’s a draw result. 
Each battle gives monkeyA XP points: 100 x (dexB / (dexB + dexA)). Each level up gives 1 point in dex.

* Duration: 3 weeks

* Deliverables: (draft)
  1. An automated build and test process of the rust library artifact using Github Actions;
  2. An automated packaging and release process for the rust library;
  3. The entire codebase under a permissive MIT open-source license;
  4. A readme file that explains the project;

<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 2: $3,938 USD

## Total funds requested

### $11,813 USD

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
