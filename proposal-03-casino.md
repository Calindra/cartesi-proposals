Cassino NPC -> start roulette (commit + stake) => no one knows the secret seed
Crowd -> mixed = bet (xor / mix) => value independent from Cassino and Block Producer
Timeout to bet
(unknown phase to the Cassino)
BlockHashT => immune from Cassino
Cassino NPC -> reveal phase -> BlockHashT + mixed + secret seed

If Casino refuses to reveal, it will be slashed and the crowd gets the money back plus the casino’s stake.

The casino will lose its stake and be cut if the NPC does not show its cards. The crowd will get their money back and the casino’s stake as well.

What prevents the Casino from leaking the secret information and betting on the winning color?  
The BlockHashT is immune from Casino interference

