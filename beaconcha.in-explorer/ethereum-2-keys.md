---
description: An overview of ethereum staking keys
---

# Ethereum Validator Keys

## Extended overview of Ethereum Validator Keys

![Ethereum 2.0 Key overview](<../.gitbook/assets/image (140).png>)

## General

Both of these keys (Keys for EOA-wallets and validator-keys) are based on the same idea and use [elliptic-curve cryptography](https://en.wikipedia.org/wiki/Elliptic-curve\_cryptography) to create keys.\
\
However, validator keys have additional functionality, and its keys require different parameters when creating them, and use the [**B**oneh-**L**ynn-**S**hacham](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham) (=**BLS**) signature scheme.

## Ethereum validator keys

Compared to EOA-keys, where users only have a **single private** key to access their funds, validator-keys offers two different keys. The **validator** **private** key and the **withdrawal** **private** key.

### The validator key

As seen in the cutout below the validator signing key consists of two elements:

* Validator **private** key
* Validator **public** key

The purpose of the **validator private key** is to **actively** sign on-chain operations such as block proposals and attestations. Therefore these keys have to be held in a hot wallet.

This flexibility has the advantage to move validator signing keys very quickly from one device to another, however, if they have gotten lost or stolen, the thief has the ability to **act maliciously** in two ways:

* Get the validator [slashed](https://kb.beaconcha.in/glossary#validator-lifecycle) by:
  * Being a [proposer](https://kb.beaconcha.in/glossary#block-proposer) and sign two different beacon blocks for the same slot
  * Being an [attester](https://kb.beaconcha.in/glossary#attestations) and sign an attestation that "surrounds" another one.
  * Being an [attester](https://kb.beaconcha.in/glossary#attestations) and sign two different attestations having the same target.&#x20;
* Force a [voluntary exit](https://kb.beaconcha.in/glossary#validator-lifecycle), which stops the validator from "staking", and grants access to its ETH balance to the withdrawal key owner.

The **validator public key** is included in the _deposit data_ which allows the consensus layer to identify the validator.

![](<../.gitbook/assets/image (124).png>)

### The withdrawal key

Just like the validator keys, the withdrawal keys also consist of two components:

* Withdrawal **private** key
* Withdrawal **public** key

Losing this key means losing access to the validator balance. However, the validator can still sign attestations and blocks since these actions require the validator private key, but there is little to no incentive to do so if the keys are lost.

To withdraw, the validator status needs to be "[exited](https://kb.beaconcha.in/glossary#validator-lifecycle)".

![](<../.gitbook/assets/image (119).png>)

## Multiple validators from a single wallet

Each validator has their own _**unique deposit data**_ by which they are identified by the [beaconchain](https://kb.beaconcha.in/glossary#beaconchain).\
**Four keys** for **one validator**.

**Q:** How can I re-deposit to my validator balance? (e.g. [Effective balance](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance) has dropped)

**A:** Send another transaction (>=1ETH) to the _deposit contract_ with the _validator specific **deposit data**_ as the transaction input. After the first deposit-transaction, the _unique deposit data_ is stored on the blockchain and can be found on various explorers.

**Note:**\
The deposit contract requires about **150,000 gas** **limit.**

![](<../.gitbook/assets/image (145).png>)

## Mnemonics for  validator keys

Over the last few years, we have become so accustomed to the [12 or 24 word-system](https://en.bitcoin.it/wiki/Seed\_phrase).\
Why do we take steps back again and make our lives more complicated and more insecure with locally stored keys?

Known hardware wallets will not be able to support validator key generation until the BLS library gets audited. [EIP-2333](https://eips.ethereum.org/EIPS/eip-2333) and [EIP-2334](https://eips.ethereum.org/EIPS/eip-2334) offer a solution but yet need to be implemented.

#### How does it work?

[Mnemonics](https://en.bitcoinwiki.org/wiki/Mnemonic\_phrase) and paths are a known feature and usually found when [users try to access](https://ethereum.stackexchange.com/questions/19055/what-is-the-difference-between-m-44-60-0-0-and-m-44-60-0) their hardware wallets.

**"Old ETH 1.0" path structure and example:**

`m/44'/60'/0'/0`

[`m / purpose' / coin_type' / account' / change / address_index`](https://ethereum.stackexchange.com/questions/19055/what-is-the-difference-between-m-44-60-0-0-and-m-44-60-0)

![](<../.gitbook/assets/image (54) (1).png>)

The same logic applies to validator Keys, just with **different** parameters.\
**There is a single "master key"** (=Mnemonic phrase) which allows the user to attach as many validators to a single **withdrawal key** as they want.\
This way the user can **derive all keys** from the Mnemonic phrase.

A simplified overview would look like the following:

![](<../.gitbook/assets/image (135).png>)

[Source: Carl Beekhuizen](https://blog.ethereum.org/2020/05/21/keys/)

Credits: _Nishant Das_ for fact-checking
