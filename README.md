# Monero - Proof of Existence

## Intro

Proof of Existence is a pretty handy tool when it comes to a public proof of any record or document. It is an immutable timestamp stored on a distributed public ledger. The blockchain stores the timestamp with every block that is mined.

The publisher can publicly reveal the digest and if  a conflict arises they can prove they had the data that generated the digest at a certain point in time. Proof of Existence is useful for copyrighted material, records, patents, contracts etc. You can prove a certain data exists at a certain moment in time.

## Monero's traits.

On the Bitcoin blockchain the hash is stored directly on the blockchain. Monero **wont** allow this. But you can use a 256 Bit hash as spend key (sha256 or keccac). To prove you have known that hash at a specific time - you need to send a small amount of XMR to a public address, generated from that spend key. One piconero (2^-12) is sufficient.

## --generate-from-spend-key

--generate-from-spend-key creates a deteministic wallet from the spend key:

```bash
 --generate-from-spend-key arg          Generate deterministic wallet from 
                                        spend key
```

First you need to create the hash with sha256sum. In this example we use "Hello World" for our document.

```bash
sha256sum document.pdf
d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26
```
Save this hash as your Proof of Existence for some point in the future.

Now you can create a new wallet using that spend key. No password.
```bash
$ ./monero-wallet-cli --generate-from-spend-key helloworld
This is the command line monero wallet. It needs to connect to a monero
daemon to work correctly.
WARNING: Do not reuse your Monero keys on another fork, UNLESS this fork has key reuse mitigations built in. Doing so will harm your privacy.

Monero 'Nitrogen Nebula' (v0.16.0.0-release)
Logging to ./monero-wallet-cli.log
WARNING: You may not have a high enough lockable memory limit, see ulimit -l
Secret spend key: d2a84f4b8b650937ec8f73cd8be2c74add5a911ba64df27458ed8229da804a26

Enter a new password for the wallet: 
Confirm password:
```

Create a new address and transfer a piconero to that address.

```bash
[wallet 437M8F]: address
437M8FuCJFAhUC3kLvn1iYDDn2uUbi36gaidRPQigUgZAwfmGCL8ZS1C76NFLrZjN4EEgVBEBeD4D2MJKEWSW936BQXCYTB
```

##Validation

The validator pretty much does the same steps and calls:

```bash
[wallet 437M8F]: show_transfers

```
