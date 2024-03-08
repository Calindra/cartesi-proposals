
[Compressing Digital Assets with Concurrent Merkle Trees](./solana-accont-compression-whitepaper.pdf)  
[Original source](https://drive.google.com/file/d/1BOpa5OFmara50fTvL0VIVYjtg-qzHCVc/view
)

given an op code like dehash("hint_filecoin", "hash123")

it will populate a internal memory

op1:
let desired_hash = "hash123"

op2:
let hint = "filecoin"

op3:
let dehashed = dehash(hint, desired_hash)

// on-chain L1 -> desired_hash == hash_fn(dehashed)

op4:
assert(hash_fn(dehashed), desired_hash) // does not matter
