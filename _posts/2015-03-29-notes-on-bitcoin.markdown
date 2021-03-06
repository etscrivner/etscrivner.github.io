---
layout: post
title:  "Notes On Bitcoin"
date:   2015-03-29 03:29:00 -0800
categories: cryptocurrency
---

The following is a set of notes made while reading the [Bitcoin Whitepaper](https://bitcoin.org/bitcoin.pdf).
My goal was to summarize the paper at a higher level of abstraction in order to make Bitcoin more accessible for philosophical discussions.

### Coins

Coins are the various solutions to the same difficult, and thermodynamically
costly, problem. The parameters of the problem can be modified to increase or
decrease its difficulty. The difficulty is amplified over time to keep pace
with gains from Moore's law. In this way proof-of-work solutions serve the same
purpose as collectibles in Nick Szabo's origins of money article [^1]

**SIDENOTE:** The problem mentioned above is specifically that of starting from
zero and incrementing by 1 each time, finding an integer value that - when
hashed along with the blocks transactions and the hash from the previous
block - produces a value that begins with a required number of zero bits. The
required number of zero bits is increased to amplify difficulty.

Once a coin is mined it becomes, quite literally, its history of ownership. It
is an ordered chain stretching from the genesis of the coin in a miner (or pool
of miners) to its current owner. Each change of ownership is recorded as part
of the coin itself.

### Temporality And The Blockchain

In theory, the exact calendar dates and clock times of transactions in bitcoin
are ultimately irrelevant to its proper functioning. Though in practice part of
the validation of a black, as explained by Vitalik Buterin in the
[Ethereum White Paper](https://github.com/ethereum/wiki/wiki/White-Paper), is
ensuring the block has a sensible timestamp neither less than the previous
block nor too far in the future. The temporality, as mentioned by
[Nick Land in the 1st lecture](http://thenewcentre.org/seminars/bitcoin-philosophy/),
is a constructed tensed or A-series temporality defined by the blockchain.

The past is constructed as a series of blocks. Each block freezes all the
transactions that a given mining node observed before attempting to freeze the
block. A mining node is entitled to freeze and share a block when it has found
a solution to the thermodynamically costly problem discussed above.

There are orphaned blocks and block chain forks that can occur and further
complicate this process. There can be either temporary or permanent competing
temporal records, but the longest fork to date was resolved back into a single
blockchain in a mere 4 blocks [^2]. The ontological status of these abandoned
temporal records may or may not be interesting to investigate.

Ultimately, the temporality constructed by bitcoin is not the temporality of an
added spatial dimension. There is only one spatial dimension to be denoted by block
number. This growing block-universe [^3] is an ever expanding transactional
history.

To reduce the burden of this accumulated past Merkle trees are used to save a
"summary" (hash) of what was previously seen, allowing the rest to be safely
discarded or only accessed in depth as needed.

### Relationship Between Coins And Blocks

The first transaction in a block is reserved for any new bitcoins to be awarded
for solving and creating that block. Thus, bitcoins come into circulation and
are assigned to the miner whose proof-of-work of the latest block is accepted
into the blockchain first. This relationship between coins and blocks allows
the currency to be bootstrapped into existence - the first coins are mined
along with the first blocks

### Overpower The Network

It's almost hilariously impractical and non-sensical to do such a thing. You
gain little to no economic power, the only real gain is the ability to deny
service to others and potentially shut the whole network down [^4].

### Addendum

To summarize Nick Land's description:

Bitcoin can be viewed, in many ways, as the enactment of transcendental
philosophical critique instantiated within software. Trusted third parties take
the place of the transcendental entity that is to be subtracted from the
monetary process via the critque. Buried beneath the technical details of the
paper is an entire framework for staging a critique of these institutions. Much
of this framework is implicit within in the assumptions taken for granted.
Through this lense Bitcoin is a philosophically interesting entity worthy of
further investigation and consideration. Especially as it relates to
capitalism, modernity, and the (neo-)liberal project.

---

[^1]: [Shelling Out](http://szabo.best.vwh.net/shell.html).

[^2]: [What Is The Longest Blockchain Fork That Has Been Orphaned To Date](http://bitcoin.stackexchange.com/questions/3343/what-is-the-longest-blockchain-fork-that-has-been-orphaned-to-date)

[^3]: [Growing Block Universe](http://en.wikipedia.org/wiki/Growing_block_universe)

[^4]: [What Can An Attacker With 51% Of Hash Power Do](http://bitcoin.stackexchange.com/questions/658/what-can-an-attacker-with-51-of-hash-power-do).