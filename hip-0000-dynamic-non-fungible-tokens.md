---
hip: 0000-dynamic-non-fungible-tokens
title: Dynamic Non-Fungible Tokens (dNFT)
author: Matt Smithies (matt@trust.enterprises) @mattsmithies  
type: Standards Track
category: Application
status: Draft
created: 2021-03-10
discussions-to: <a URL pointing to the official discussion thread>
updated: [2021-02-17](https://github.com/trustenterprises/hedera-dnft-specification)
requires: <HIP number(s)>
replaces: <HIP number(s)>
superseded-by: <HIP number(s)>
---

## Abstract

This specification seeks to introduce a standard for connecting a token minted through HTS to a topic on HCS. this 

This is a description of the work in progress for implementing Dynamic Non-Fungible Tokens (dNFT) on Hedera Hashgraph. The goal is to bring together new community consensus on token standards and new primitives within the ecosystem to ensure interoperability and reduce fragmentation between products.

**All items below are subject to change, additional work needs to be conducted with regards to the decentralised trigger nature of dNFTs**

## Motivation

A dNFT is a new type of token which is presently unique to the hedera hashgraph ecosystem it's goal is to create a NFT where its concrete value increases over time. In short a dNFT is an NFT which can be linked to multiple sources of data, documents or image and can continuely be updated over time.

A holder of such a token has direct digital ownership or link to many kinds of media over time.

## Rationale

A dNFT consists of a Hedera Token Service (HTS) token linked to a Hedera Consensus Service (HCS) topic through the Name property metadata, a portion of the Name will be comprised of the HCS Topic ID. The treasurer of the dNFT make link new media to a dNFT through adding additional messages to the linked HCS topic.

## Specification

Below is a brief walkthrough of how a dNFT is formed and maintained, both the HTS and HCS metadata elements need to be immutable,

1. The "minter" account creates a HCS topic. The adminKey must not be set.
2. The "minter" account creates a HTS token. The adminKey, wipeKey, freezeKey must not be set.
3. The "name" of the token should confirm to the format specification below.
4. New messages that are sent to the HCS topic are linked with a piece of media which should be hosted on a decentralised file service, such as IPFS.

For testing S3 is fine, but all links to media should be accessible through HCS messages, permanently. Pinata and Fleek are options we are currently evaluating.

This is the proposed dNFT name format, within 100 bytes.

- The Topic Id of the HCS topic
- The Account ID of the minter account
- The Symbol of the proposed token
- Optional metadata to describe the dNFT

Here is the proposed structure

    'DNFT:{symbol}_{metadata}:{topic_id}:{account_id}'

With an example for Unibar designs

    'DNFT:UNIBAR_DESIGNS:0.0.22222222:0.0.123456789'


## Backwards Compatibility

N/A

## Security Implications

dNFTs are opt-in and pro

## How to Teach This

For a HIP that adds new functionality or changes interface behaviors, it is helpful to include a section on how to teach users, new and experienced, how to apply the HIP to their work.

## Reference Implementation

The reference implementation must be complete before any HIP is given the status of “Final”. The final implementation must include test code and documentation.

## Rejected Ideas

Using HTS memo instead of name

Throughout the discussion of a HIP, various ideas will be proposed which are not accepted. Those rejected ideas should be recorded along with the reasoning as to why they were rejected. This both helps record the thought process behind the final version of the HIP as well as preventing people from bringing up the same rejected idea again in subsequent discussions.

In a way, this section can be thought of as a breakout section of the Rationale section that focuses specifically on why certain ideas were not ultimately pursued.

## Open Issues

While a HIP is in draft, ideas can come up which warrant further discussion. Those ideas should be recorded so people know that they are being thought about but do not have a concrete resolution. This helps make sure all issues required for the HIP to be ready for consideration are complete and reduces people duplicating prior discussions.

## References

1. [Hedera Hashgraph Dynamic Non-Fungible Standard](https://github.com/trustenterprises/hedera-dnft-specification)
2. [Introducing Proof of Carbon on Hedera Hashgraph](https://blog.dovu.dev/introducing-proof-of-carbon/)

## Copyright/license

Each new HIP must be placed under the Apache License, Version 2.0 -- see [LICENSE](LICENSE) or (https://www.apache.org/licenses/LICENSE-2.0)
