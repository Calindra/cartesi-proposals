**Cartesi & Syscoin Data Availability**

Combining the computational power of Cartesi and the data availability (DA) of Syscoin, to leverage the benefits of both platforms.

**Core Concept and purpose statement**
<!--[A POC is meant to de-risk the central component of a larger project or idea. What's the essential idea or concept that your POC is trying to prove? What makes it essential to a larger scope project or product? Provide an objectively verifiable statement of purpose, to which the final outcome (success or failure) of the POC project will be measured. (see "success criteria" section below)] -->
This project aims to demonstrate the feasibility and potential of integrating Cartesi’s layer-2 solution with Syscoin’s NEVM, enabling developers to create scalable, secure, and decentralized applications using mainstream software stacks and tools. This Prof of Concept will fetch and validate raw data from Syscoin DA solution and process it using Pandas inside the Cartesi Machine.

**How will you use Cartesi, specifically?**
<!-- [Details about how you're using Cartesi specifically in your POC, and why it makes sense. Be as precise as possible, using diagrams and pictures liberally. Alternatively, you can reference specific sections of your response to the next question. You cannot leave this question blank though.] -->
Cartesi is a layer-2 solution that enables developers to use mainstream software stacks and tools to build smart contracts on top of any blockchain. Cartesi provides a Linux-based virtual machine (VM) that runs off-chain, but can be verified on-chain, allowing for complex and intensive computations to be performed without compromising the security and decentralization of the blockchain.

We are using Cartesi for our project because it offers several advantages that make it suitable for our needs. Some of these advantages are:

- **Programming flexibility**: Cartesi allows us to use familiar programming languages and tools, such as Python, R, SQL, or Pandas, to create and execute our smart contracts. This reduces the learning curve and the development time, as well as the complexity and cost of the code. It also enables us to access a rich set of libraries and frameworks that can enhance the functionality and performance of our smart contracts.
- **Scalability**: Cartesi enables us to perform large-scale computations off-chain, without being limited by the gas fees, block size, or throughput of the blockchain. This allows us to process and analyze the big data that is accessible and retrievable from Syscoin's network-enhanced virtual machine (NEVM), which offers fast, low-cost, and interoperable transactions, as well as Ethereum-compatible smart contracts and decentralized applications. By using Cartesi's VM, we can handle complex tasks such as machine learning, data mining, or optimization, that would otherwise be impractical or impossible on-chain.
- **Interoperability**: Cartesi allows us to deploy our smart contracts on any blockchain that supports smart contract execution, such as Syscoin's NEVM, Ethereum, Binance Smart Chain, or Polygon. This gives us more flexibility and choice in selecting the best platform for our project, as well as the possibility to interact with other blockchains and platforms that offer different features and functionalities.

In summary, by combining Cartesi and Syscoin, we can leverage the best of both worlds: a layer-2 solution that enhances the performance and functionality of the off-chain processing power, and a layer-1 solution that ensures the data availability and security of the on-chain transactions. We believe that this project will add value to the Cartesi ecosystem or tech stack by expanding its reach and compatibility with other blockchain platforms, enhancing its performance and functionality with more advanced and sophisticated DApps, such as data analysis and machine learning, and increasing its adoption and innovation with more developers and users who can benefit from its features and advantages.

**Technical details**
<!--[Provide a technical description here, and please use images and diagrams to support it.] -->
![Cartesi and Syscoin](https://github.com/Calindra/cartesi-proposals/blob/main/images/cartesi_proposal_Syscoin_3.png?raw=true)  

1. We will create a client called Web3DAClient to simplify the process of uploading data to the Syscoin DA solution and sending the hash to InputBox through DAContract.

2. We will develop the SyscoinFetcher component to fetch the data from Syscoin given a hash.

3. We will deploy all the [Rollups Contracts](https://github.com/cartesi/rollups-contracts) on the [Tanenbaum testnet](https://faucet.tanenbaum.io) to run inside Syscoin's NEVM.

4. Inside Cartesi's solution, we will develop an integration with the Dispatcher component.

**Value Proposition**
<!--[How does this POC provide value to the Cartesi developer ecosystem or core technology? Why would the community or other developers be interested in its successful execution?]-->
This product/service leverages the computational power of Cartesi's layer-2 solution to process and analyze the big data that is accessible and retrievable from Syscoin’s network-enhanced virtual machine (NEVM), enabling developers to create scalable, secure, and decentralized applications using mainstream software stacks and tools. By integrating Cartesi with Syscoin, this product/service offers fast, low-cost, and interoperable transactions, as well as Ethereum-compatible smart contracts and decentralized applications. Moreover, by using PoDA protocol, this product/service ensures that the data needed to verify the off-chain computation is available to anyone who wants to verify it, without requiring the full data to be stored on the blockchain. This product/service also ensures the data availability of the blockchain itself, by using various methods to prevent data withholding attacks.

**Estimated Duration and Funds Requested**
Duration: [x weeks/months]
Funds request (USD) for the POC: [$x USD]

**Subsequent Vision and Extensibility**
<!--[If the POC proves to be successful, what potential does it hold for a full-scale project or product? Share a brief vision of what a larger project would look like. Additionally, describe the next steps or features that should be implemented immediately following a successful proof of concept that extend the POC's functionality.] -->

In the future, we plan to add **Filecoin** support to our solution, which will enable us to leverage a decentralized storage network over **IPFS**. Filecoin is an open-source, public cryptocurrency and digital payment system that allows users to rent unused hard drive space. By integrating Filecoin with our solution, we will be able to offer more data storage options, as well as enhance the security and reliability of our data retrieval service. Our vision is to create a scalable and flexible DApp that can handle real-life and complex use cases using **Cartesi Rollups**, which have a powerful rollups technology with a Linux runtime. Cartesi Rollups allow us to move the bulk of the computation outside the blockchain, using any ledger as a data source but not as an execution environment. This way, we can overcome the scalability limitations of the Ethereum Virtual Machine (EVM) and use any package or library that is available for Linux (like Pandas). The next steps or features that we would implement after a successful proof of concept are:

- Developing a **Filecoin Fetch** component that is responsible for retrieving the data from Filecoin IPFS.
- Developing a **Filecoin Arbitration** component that is responsible for validating the data and opening a dispute when the raw data diverges.
- Developing a **Filecoin FS Client** that simplifies the data requests, driver mountings, and so on.
- Testing and optimizing our DApp's performance, security, and usability.



**Reusability and Other Use Cases**
<!--[What are other potential uses for this POC? If not for the POC, then what about for the fuller-scale project for which it was implemented? How could they be adapted or expanded upon for other applications within the Cartesi ecosystem? Which modules of the POC can be immediately reused by the developer community, even without pursuing the more complex project?]-->
The three main components could be reused by other DApps to handle large and complex datasets that require advanced analysis and processing. It can also ensure the security and reliability of the data retrieval service. Some other potential uses for our solution are:

- **Data science**: Everyone can use our solution to perform data science tasks, such as data cleaning, exploration, visualization, modeling, and evaluation. You can use any library or package that is available for Linux, such as Pandas.
- **Machine learning**: Everyone can use our POC to train and deploy machine learning models, such as classification, regression, clustering, and reinforcement learning. You can use any framework or tool that is compatible with Linux, such as Keras, PyTorch, FastAI, and Ray.
- **Artificial intelligence**: Everyone can use our POC to create and run artificial intelligence applications, such as natural language processing, computer vision, speech recognition, and generative adversarial networks. You can use any library or package that supports Linux, such as NLTK, SpaCy, OpenCV, and PyTorch.

These are just some of the examples of how you can use your POC for other purposes. There are many more possibilities and opportunities that you can explore.

**Risks and Contingency Plans**
<!--[What are the potential challenges or risks for this POC? If things don't go according to plan, how will you you know? How will you pivot or adjust your approach?]-->
Cartesi and Syscoin are two blockchain-based platforms that aim to provide scalability and interoperability for decentralized applications (DApps).

There challenges and risks that could arise from this an integration. Some of them are:

- **Technical complexity**: Integrating two different platforms with different architectures and protocols could pose technical difficulties and require a lot of development resources and testing.
- **Security risks**: Integrating two platforms could also introduce new attack vectors or vulnerabilities that could compromise the security or integrity of the DApps or the platforms themselves. For example, if one platform suffers a network outage, a malicious attack, or a bug, it could affect the other platform or the DApps that rely on them. Additionally, there could be potential issues with data privacy, custody, or compliance when transferring data or assets across platforms.
- **Economic trade-offs**: Integrating two platforms could also involve economic trade-offs or opportunity costs that could affect the profitability or sustainability of the DApps or the platforms themselves. For example, if one platform has higher transaction fees, lower adoption, or lower liquidity than the other platform, it could affect the user experience, demand, or revenue of the DApps or the platforms. Using two tokens for the DApps might make them harder to adopt.

**Success criteria**
<!--[What is considered success for this POC? How will you know whether the POC is finished? What deliverables will you produce to demonstrate that the POC accomplished what it set out to do?]-->
The POC should use all three components successfully to fetch a sample of data from Syscoin’s DA and use it inside the Cartesi Machine using Pandas.

**Final report**
<!--[Upon a failure of the POC, the Grants Council may still issue prorated payment if the applicant provides a written debriefing that sufficiently details the approaches used, why they failed, and what next steps would be if someone else were to resume the project. This will be shared with the community. Do you agree to provide this? Yes/no]-->
At the end of this POC, we will provide a detailed report containing any reasons for failure that we encountered during the development process. This will allow others from community to overcome those issues and continue the project with confidence.

**About Your Development team**
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

ERC-20 Payee address
0x7cE0AA3DFbB8abdCD0Ea426769ffD21302DAA8B8