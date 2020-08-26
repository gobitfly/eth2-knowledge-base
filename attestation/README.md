---
description: Attestation Inclusion delay and why it is important
---

# Attestation

This post will use [AttestantIO](https://twitter.com/attestantio)'s post about [_Attestation effectiveness_](https://www.attestant.io/posts/defining-attestation-effectiveness/) as a reference and explain which metrics in regards of attestations the [beaconcha.in](https://beaconcha.in/) explorer is displaying and why it is important for the end user.

## General

#### Attestation 

Every [Epoch](https://kb.beaconcha.in/glossary#epoch) \(~6.4 minutes\) a validator proposes an attestation \(vote\) to the network.  
This vote consists of the following segments:

* [Committee](https://kb.beaconcha.in/glossary#slots)
* [Validator Index](https://kb.beaconcha.in/glossary#unique-index)
* Finality vote
* Signature
* Chain head vote \(vote on what the validator believes is the head of the chain\) 

As we know a minimum of 16,384 validators are required to start Ethereum 2.0.   
If we multiply that with the information included in each Attestation per Epoch, it adds up really quickly. Therefore, Ethereum 2.0 **aggregates** all of that information and minimises the data growth.  


#### Aggregated Attestation

> [_**Aggregation**_](http://dos.iitm.ac.in/OOSD_Material/Basic%20Concepts/Basic%20Concepts%20Of%20OO/aggregation.htm) _is a way of composing different abstractions together in defining a class. For **example**, a car class can be defined to contain other classes such as engine class, seat class, wheels class etc._

So what does that mean for Attestations?  
  
Each block one or more committees are chosen to attest. A committee has a minimum of 128 validators of which 16 are randomly elected to become an aggregator.  
As shown below, the validators send their unaggregated attestation to the aggregators. They then merge the attestations and forward a single aggregated attestation to the [block proposer](https://github.com/gobitfly/eth2-beaconchain-explorer/pull/218).

![](../.gitbook/assets/image%20%28164%29.png)



