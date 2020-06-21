# Monero - Proof of Existence

## Intro

Proof of Existence is a pretty handy tool when it comes to a public proof of any record or document. It is an immutable timestamp stored on a distributed public ledger. The blockchain stores the timestamp with every block that is mined.

The publisher can publicly reveal the digest and if  a conflict arises they can prove they had the data that generated the digest at a certain point in time. Proof of Existence is useful for copyrighted material, records, patents, contracts etc. You can prove a certain data exists at a certain moment in time.

## Monero's traits.

On the Bitcoin blockchain the hash is stored directly on the blockchain. Monero **wont** allow this. But you can use a 256 Bit hash as spend key (sha256 or keccac). To prove you have known that hash at a specific time - you need to send a small amount of XMR to a public address, generated from that spend key. One piconero (2^-12) is sufficient.

## --generate-from-spend-key
