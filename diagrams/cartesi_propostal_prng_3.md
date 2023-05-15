```mermaid
%%{
  init: {
    "theme": "dark",
    "sequence": {
      "mirrorActors": true,
      "messageAlign": "center"
    }
  }
}%%
sequenceDiagram
  actor Bob
  participant ConvenienceAPI as <<off-chain>><br>Convenience API
  participant CM as L1 & Cartesi Rollups
  participant ConvenienceMiddleware as <<Cartesi Machine>><br>Convenience Middleware
  participant UserProgram as <<Cartesi Machine>><br>User dApp Program
  autonumber

  Bob->>+ConvenienceAPI: signed Bob's commit hash and receipt
  ConvenienceAPI-->>-Bob: signed Convenience's commit hash and receipt

  # BOB REVEAL
  Bob->>+CM: Bob reveals the secret and also send the Convenience's signed commit hash
  CM->>+ConvenienceMiddleware: input: revealed secret and Convenience's signed commit hash
  ConvenienceMiddleware->>ConvenienceMiddleware: save input
  ConvenienceMiddleware-->>-CM: ok
  CM-->>-Bob: ok

  # CONVENIENCE REVEAL
  ConvenienceAPI->>+CM: input: Convenience's revealed secret
  CM->>+ConvenienceMiddleware: input: Convenience's revealed secret
  ConvenienceMiddleware->>ConvenienceMiddleware: verify commit hashes
  ConvenienceMiddleware->>ConvenienceMiddleware: create seed
  ConvenienceMiddleware->>+UserProgram: generated seed
  UserProgram->>UserProgram: random(seed)
  UserProgram-->>-ConvenienceMiddleware: ok
  ConvenienceMiddleware-->>-CM: ok
  CM-->>-ConvenienceAPI: ok

  
```

Bob starts a new random number process by calling the REST Convenience API. Bob’s payload includes a signed receipt that can be executed by the Convenience Service if Bob fails to reveal his secret. The Convenience API responds with a signed commit and receipt.

We know that the user’s dApp calls the rollup server, we change the arrow direction to make the problem easier to think about. In reality, dApps will call our middleware and our middleware will call the rollup server.

Neither Bob nor Convenience can claim counterpart's share until Bob completes step 3, which involves Bob’s secret seed and Convenience’s signed commit.

There is a certain amount of money that must be staked as a guarantee to ensure the disclosure of the secrets.
