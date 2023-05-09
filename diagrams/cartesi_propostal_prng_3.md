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

  Bob->>+ConvenienceAPI: signed Bob's commit and receipt
  ConvenienceAPI-->>-Bob: signed Convenience's commit and receipt

  # BOB REVEAL
  Bob->>+CM: Bob's secret seed and Convenience signed commit
  CM->>+ConvenienceMiddleware: input: secret seed and Convenience signed commit
  ConvenienceMiddleware->>ConvenienceMiddleware: save input
  ConvenienceMiddleware-->>-CM: ok
  CM-->>-Bob: ok

  # CONVENIENCE REVEAL
  ConvenienceAPI->>+CM: Convenience's secret
  CM->>+ConvenienceMiddleware: input: Convenience's secret
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