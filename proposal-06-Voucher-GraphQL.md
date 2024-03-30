# Convenience Layer for Voucher Management on Cartesi

## Objective:

The objective of this proposal is to develop a convenience layer to simplify the process of managing, indexing, and tracking vouchers within the Cartesi ecosystem. This layer will enhance user experience by providing efficient access to voucher-related information and facilitate the monitoring of voucher execution status.

## Proposed Solution:

1. Voucher Creation Command Enhancement:

    Enhance the voucher creation command (createVoucher) to include parameters necessary for indexing and tracking, such as output index, input index, beneficiary address, amount, etc.

2. Indexing and Tracking using Reports:

    **Introduce a createReport specific payload** to generate reports associated with voucher creation. These reports will contain essential details required for indexing and tracking vouchers. Each report will be labeled with the type of voucher (e.g., ERC-20, ERC-721, ERC-1155).

3. Database Structure:

    Implement a database structure to store voucher-related information. This structure will consist of tables corresponding to different types of vouchers, such as native ethers tokens, ERC-20 tokens, ERC-721 tokens, and ERC-1155 tokens. Alternatively, a single table with a type column can be used for easier access.

4. GraphQL Integration:

    Develop GraphQL queries to allow frontend applications to query voucher data efficiently. These queries will provide access to relevant information stored in the database, enabling seamless integration with frontend interfaces.

5. Event Listening for Voucher Execution:

    Set up event listeners to monitor the execution status of vouchers. Specifically, listen for VoucherExecuted or OutputExecuted events to detect when vouchers are executed on the L1 smart contract. Update the executedAt field/column in the database to mark the voucher execution.

## Addressing Challenges:

One of the main challenges is determining the number of tokens in transit from Cartesi Machine (CM) to L1. To overcome this challenge, we propose the following approach:

Implement a tracking mechanism within the convenience layer to monitor the movement of vouchers between CM and L1.
Integrate with Cartesi's infrastructure to retrieve information about vouchers in transit.
Utilize the actual event architecture to capture voucher execution events and update the transit status accordingly.

## Technical details

Code draft to explain the inner workings of the withdraw process, which triggers voucher and report creation.

```ts
// dapp backend within the CM
async function withdrawERC20(owner: string, token: Address, amount: bigint)
    const voucher = await _wallet.withdrawERC20(token, owner, amount)
    const outputIndex = await _dapp.createVoucher(token, payload)
    const voucherMetadata = {
        label: `erc-20-voucher`,
        outputIndex,
        amount,
        owner,
        token,
        /* other params */
    }
    await _dapp.createReport({ payload: createHexPayload(voucherMetadata) })
}
```

We will develop a Proof of Concept (PoC) in the NoNodo to both test and refine the idea.

```go
graphConfig.Resolvers.Mutation().UpdateVoucherMetadata(context, model.VoucherExecutionEvent{
    InputIndex:  eventL1.InputIndex,
    OutputIndex: eventL1.OutputIndex,
    ExecutedAt:  eventL1.timestamp,
})
```

## Conclusion:

By implementing this convenience layer, we aim to streamline voucher management within the Cartesi ecosystem, providing users with enhanced accessibility and transparency regarding voucher operations. This solution will improve the overall user experience and facilitate the seamless integration of voucher functionality into Cartesi-based applications.
