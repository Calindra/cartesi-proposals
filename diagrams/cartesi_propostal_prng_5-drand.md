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
  actor Alice
  participant ConvenienceAPI as <<off-chain>><br>Convenience API
  participant CM as L1 & Cartesi Rollups
  participant ConvenienceMiddleware as <<Cartesi Machine>><br>Convenience Middleware
  participant UserProgram as <<Cartesi Machine>><br>User dApp Program
  autonumber

  # BOB INPUT
  Bob->>+CM: Bob's input that requires a random number
  CM->>+ConvenienceMiddleware: Bob's input
  ConvenienceMiddleware->>ConvenienceMiddleware: save input
  ConvenienceMiddleware-->>-CM: ok
  CM-->>-Bob: ok

  # Alice INPUT
  Alice->>+CM: Alice's input that requires a random number
  CM->>+ConvenienceMiddleware: Alice's input
  ConvenienceMiddleware->>ConvenienceMiddleware: save input
  ConvenienceMiddleware-->>-CM: ok
  CM-->>-Alice: ok

  # CONVENIENCE DRAND
  ConvenienceAPI->>+CM: input: Drand's beacon
  CM->>+ConvenienceMiddleware: input: Drand's beacon
  ConvenienceMiddleware->>ConvenienceMiddleware: verify BLS
  ConvenienceMiddleware->>ConvenienceMiddleware: verify Timestamp
  ConvenienceMiddleware->>ConvenienceMiddleware: load pending inputs
  
  # BOB resolved
  ConvenienceMiddleware->>+UserProgram: Bob's input with seed metadata
  UserProgram->>UserProgram: random(seed)
  UserProgram-->>-ConvenienceMiddleware: ok

  # Alice resolved
  ConvenienceMiddleware->>+UserProgram: Alice's input with seed metadata
  UserProgram->>UserProgram: random(seed)
  UserProgram-->>-ConvenienceMiddleware: ok

  ConvenienceMiddleware-->>-CM: ok
  CM-->>-ConvenienceAPI: ok

  
```

Anyone can send the Drand's beacon.
