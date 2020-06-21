# Monero - Proof of Existence

## Intro

Proof of Existence is a pretty handy tool when it comes to a public proof of any record or document. It is an immutable timestamp stored on a distributed public ledger. The blockchain stores the timestamp with every block that is mined.

The publisher can publicly reveal the digest and if  a conflict arises they can prove they had the data that generated the digest at a certain point in time. Proof of Existence is useful for copyrighted material, records, patents, contracts etc. You can prove a certain data exists at a certain moment in time.

## Monero's traits.

On Bitcoin the hash is stored directly on the blockchain. Monero **wont** allow this. But you can use a 256 Bit hash as spend key (sha256 or keccac). To prove you have known that hash at a specific time - you need to send a small amount of XMR to a public address, generated from that spend key. One piconero (2^-12) is sufficient.

## First step (sha256sum)

Use sha256sum to calculate the digest from your document.

```bash
sha256sum document.pdf
d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26
```
Save this hash as your Proof of Existence for some point in the future.

## --generate-from-spend-key

--generate-from-spend-key creates a deteministic wallet from the spend key:

```bash
 --generate-from-spend-key arg          Generate deterministic wallet from 
                                        spend key
```
This generates a wallet using that spend key generated with sha256sum. e.G.:

```bash
$ ./monero-wallet-cli --generate-from-spend-key myproof.wallet
Monero 'Nitrogen Nebula' (v0.16.0.0-release)
Logging to ./monero-wallet-cli.log
WARNING: You may not have a high enough lockable memory limit, see ulimit -l
Secret spend key: d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26

Enter a new password for the wallet: 
Confirm password:
```
No Password. 

## Write to the blockchain

Now create a new address and transfer a piconero to that address from any wallet.

```bash
[wallet 437M8F]: address
437M8FuCJFAhUC3kLvn1iYDDn2uUbi36gaidRPQigUgZAwfmGCL8ZS1C76NFLrZjN4EEgVBEBeD4D2MJKEWSW936BQXCYTB
```
Doeing the transaction will take care of the timestamp.

## Validation

The validator requires the hash, the document itself and the date of transaction.
It is pretty much the same steps + calling:

```bash
[wallet 437M8F]: show_transfers

```
