Draft:

![Alt text](images/cartesi_proposal_Syscoin_Draft.png)

1. Bob sends the data to Syscoin DA:
```json
{
    "merkleTree": ["rootHash", "leaf01Hash", "leaf02Hash"],
    "rawData": "Leaf01DataLeaf02Data"
}
```
The chunk size is 10 characters to simplify.

2. The DA stores the data and returns a hash of the data:
```json
{
    "hash": "SyscoinHash",
    "content": {
        "merkleTree": ["rootHash", "leaf01Hash", "leaf02Hash"],
        "rawData": "Leaf01DataLeaf02Data"
    }
}
```

3. Bob checks the hash `SyscoinHash`.
4. Bob sends the hash to the `Data Availability Contract` + merkle root + leaf index.
5. The `Data Availability Contract` verifies the data availability (6 hours).
6. The `Data Availability Contract` sends the parameters to `InputBox`.
7. The `DApp` requests the data from the `DataReader`.
8. The `DataReader` calls any `DataProviders` to fulfill the request.
9. The `MerkleValidator` checks the `SyscoinHash`.
10. The `MerkleValidator` checks the path of the merkle tree against the leaf data.
11. The `DataReader` returns the verified data to `DApp`.

Everything will be computed inside the Cartesi Machine.
If any part of the data is wrong, Alice should send the `leaf01Hash` and the `Leaf01Data` to L1 `Data Chunk Arbitrage` to do the arbitration process.

If the `SyscoinHash` does not match the full data, the current process of Cartesi can handle the problem.

If any path of the merkle tree is wrong, the current process of Cartesi will handle the problem.