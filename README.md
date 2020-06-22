# Monero - Proof of Existence

## Intro

Proof of Existence is a pretty handy tool when it comes to a public proof of any record or document. It is an immutable timestamp stored on a distributed public ledger. The blockchain stores the timestamp with every block that is mined.

The publisher can publicly reveal the digest and if  a conflict arises they can prove they had the data that generated the digest at a certain point in time. Proof of Existence is useful for copyrighted material, records, patents, contracts, notary etc. You can prove a certain data exists at a certain moment in time.

## Monero's traits.

With Bitcoin the hash is stored on the blockchain itself. Monero **wont** allow this. But you can use a 256 Bit hash as spend key (sha256 or keccac). All you need is to send a small amount of XMR to a public address, generated from that spend key. One piconero (2^-12) is sufficient. A different aproach but it works great.

## First step: Calculate the hash

sha256sum calculates the digest/hash of your document.

```bash
sha256sum document.pdf
d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26
```
Save this hash as your Proof of Existence for some point in the future.

## Next step: --generate-from-spend-key

monero-wallet-cli provides a command line option *--generate-from-spend-key* to create a deteministic wallet from the spend key:

```bash
 --generate-from-spend-key arg          Generate deterministic wallet from 
                                        spend key
```
Example how to generate a wallet by using that spend key from above:

```bash
$ ./monero-wallet-cli --generate-from-spend-key myproof.wallet
Monero 'Nitrogen Nebula' (v0.16.0.0-release)
Logging to ./monero-wallet-cli.log
Secret spend key: d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26

Enter a new password for the wallet: 
Confirm password:
```
Do *not* enter a Password. Hit »Return« to continue.

## Last step: Write to the blockchain

Now create a new address and transfer a piconero to that address from any wallet.

```bash
[wallet 437M8F]: address
437M8FuCJFAhUC3kLvn1iYDDn2uUbi36gaidRPQigUgZAwfmGCL8ZS1C76NFLrZjN4EEgVBEBeD4D2MJKEWSW936BQXCYTB
```
Doeing the transaction will take care of the timestamp.

## Verify

The verifier requires the hash, the document itself and the date of transaction.
It is pretty much the same steps + calling:

```bash
[wallet 437M8F]: show_transfers
 2126035     in   8 blks       2020-06-22 07:07:05       0.000000000001 6440e62c10b33681d50fcf9cdf39870aec5365a997d4a8dd97bb3ed5e3fe58bf 0000000000000000 0.000000000000 437M8F:0.000000000001 0 -

```
