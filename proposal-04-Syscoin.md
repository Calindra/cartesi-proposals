## New Proposal

**Cartesi & Syscoin Data Availability**

Combining the computational power of Cartesi and the data availability (DA) of Syscoin, to leverage the benefits of both platforms.

**What is Syscoin?**

Syscoin is a full-stack modular Proof-of-Work blockchain solution merge-mined with Bitcoin. At its base is a dual-chain Layer 1: the core is the Syscoin native (UTXO) blockchain network providing Data Availability and Finality, and running in tandem with it is an Ethereum Virtual Machine (EVM) chain called NEVM (Network-Enhanced Virtual Machine) which provides Ethereum equivalence while inheriting enhanced security from the native chain and providing scalability through rollups.

**Project Description**
<!-- [Write the description long-form here, or else paste a [google drive link](https://url/) to a slide deck]
-->

This project aims to demonstrate the feasibility and potential of integrating Cartesi’s layer-2 solution with Syscoin’s NEVM, enabling developers to create scalable, secure, and decentralized applications using mainstream software stacks and tools. This Prof of Concept will fetch and validate raw data from Syscoin DA solution and process it using Pandas inside the Cartesi Machine.

![Cartesi and Syscoin](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesi_proposal_Syscoin_2.png?raw=true)
The two components in green will be designed to be reusable for other DApps and be transformed into Cartesi’s plugins. One has the responsibility to fetch the data, and the Arbitration is responsible for validating the data and opening a dispute when the raw data diverges. 
Last but not least, we will provide an FS Client to ease the data requests, driver mountings, and so on.
As you can see in the image above, in the future we plan to add FileCoin support as well.

**The DApp**

As end user developers, we will incorporate Pandas into our proof of concept. We will use the plugin (described above) to fetch the raw data and then use Pandas to extract an average number from it. In the end, we will send a notice with the calculated result to the Cartesi’s Rollups.

**Value proposition**
<!-- [Why would someone use this product/service? Or how does it add value to the Cartesi ecosystem or tech stack?]
-->
This product/service leverages the computational power of Cartesi's layer-2 solution to process and analyze the big data that is accessible and retrievable from Syscoin’s network-enhanced virtual machine (NEVM), enabling developers to create scalable, secure, and decentralized applications using mainstream software stacks and tools. By integrating Cartesi with Syscoin, this product/service offers fast, low-cost, and interoperable transactions, as well as Ethereum-compatible smart contracts and decentralized applications. Moreover, by using PoDA protocol, this product/service ensures that the data needed to verify the off-chain computation is available to anyone who wants to verify it, without requiring the full data to be stored on the blockchain. This product/service also ensures the data availability of the blockchain itself, by using various methods to prevent data withholding attacks. This product/service adds value to the Cartesi ecosystem or tech stack by expanding its reach and compatibility, enhancing its performance and functionality, and increasing its adoption and innovation.

## How you will use Cartesi, specifically?

<!--[Details about how you're using Cartesi specifically, and why it makes sense. This is the most important part of the proposal. If you are not precise, or your intention is not feasible, the proposal will be rejected.]-->

Cartesi is a layer-2 solution that enables developers to use mainstream software stacks and tools to build smart contracts on top of any blockchain. Cartesi provides a Linux-based virtual machine (VM) that runs off-chain, but can be verified on-chain, allowing for complex and intensive computations to be performed without compromising the security and decentralization of the blockchain.

We are using Cartesi for our project because it offers several advantages that make it suitable for our needs. Some of these advantages are:

- **Programming flexibility**: Cartesi allows us to use familiar programming languages and tools, such as Python, R, SQL, or Pandas, to create and execute our smart contracts. This reduces the learning curve and the development time, as well as the complexity and cost of the code. It also enables us to access a rich set of libraries and frameworks that can enhance the functionality and performance of our smart contracts.
- **Scalability**: Cartesi enables us to perform large-scale computations off-chain, without being limited by the gas fees, block size, or throughput of the blockchain. This allows us to process and analyze the big data that is accessible and retrievable from Syscoin's network-enhanced virtual machine (NEVM), which offers fast, low-cost, and interoperable transactions, as well as Ethereum-compatible smart contracts and decentralized applications. By using Cartesi's VM, we can handle complex tasks such as machine learning, data mining, or optimization, that would otherwise be impractical or impossible on-chain.
- **Interoperability**: Cartesi allows us to deploy our smart contracts on any blockchain that supports smart contract execution, such as Syscoin's NEVM, Ethereum, Binance Smart Chain, or Polygon. This gives us more flexibility and choice in selecting the best platform for our project, as well as the possibility to interact with other blockchains and platforms that offer different features and functionalities.

In summary, we are using Cartesi specifically because it enables us to create scalable, secure, and decentralized applications using mainstream software stacks and tools, while ensuring the data availability and verifiability of our smart contracts integrating with Syscoin's NEVM, which offers fast, low-cost, and interoperable transactions, as well as Ethereum-compatible smart contracts and decentralized applications. We believe that this combination of Cartesi and Syscoin makes sense for our project, as it offers the best of both worlds: a layer-2 solution that enhances the performance and functionality of the smart contracts, and a network-enhanced virtual machine that enhances the performance and functionality of the transactions. We think that this project will add value to the Cartesi ecosystem or tech stack by expanding its reach and compatibility, enhancing its performance and functionality, and increasing its adoption and innovation.

## Milestones

**Milestone 1: Base Contract Deployment (Draft)**
<!--
Realmente a gente que deveria fazer esse deploy?
existe algum privilégio do owner do contrato?
-->
We will deploy all the [Rollups Contracts](https://github.com/cartesi/rollups-contracts) on the [Tanenbaum testnet](https://faucet.tanenbaum.io).

* Duration: 3 weeks

* Deliverables:
  1. Rollups Contracts deployed

<!-- 
[what will be produced, accomplished, or demonstrated by the end of this period?]
-->

* Funds request (USD) for milestone 1: $3,937 USD

**Milestone 2: Syscoin Data Availability (DA) Plugin (Draft)**

* Duration: 9 weeks

* Deliverables:
  1. Fetch Plugin
  2. Arbitration Plugin
  3. FS Client
  4. An automated build and test process of the library artifact using Github Actions;
  5. The entire codebase under a permissive MIT open-source license;
  6. A readme file that explains the project;
<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->

* Funds request (USD) for milestone 2: $11,812 USD

**Milestone 3: Pandas experiment (Draft)**

* Duration: 6 weeks

<!--[what will be produced, accomplished, or demonstrated by the end of this period?]-->
* Deliverables:
  1. An automated build and test process of the DApp using Github Actions;
  2. The entire codebase under a permissive MIT open-source license;
  3. A readme file that explains the project;

* Funds request (USD) for milestone 6: $7,875 USD

## Total funds requested

### $23,624 USD

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
