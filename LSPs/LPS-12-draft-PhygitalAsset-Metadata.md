---
lip: 12
title: Phygital Asset Metadata
author: Jean Cavallera (@CJ42) <contact.cj42@protonmail.com>
discussions-to: <URL>
status: Draft
type: LSP, Metadata
created: 2021-12-24 format>
requires: ERC165, ERC725Y, LSP2
---

## Simple Summary
<!--"If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the LIP.-->
If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the LIP.

This standard describes a set of [ERC725Y](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-725.md) keys that can be used to bind a real world asset to a digital space.

## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->
*A short (~200 word) description of the technical issue being addressed.*

## Motivation
<!--The motivation is critical for LIPs that want to change the Lukso protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the LIP solves. LIP submissions without sufficient motivation may be rejected outright.-->
*The motivation is critical for LIPs that want to change the Lukso protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the LIP solves. LIP submissions without sufficient motivation may be rejected outright.*

There is an upcoming requirement to transfer property of physical property to digital spaces *(explain why)*.
Using RFID chips attached to physical items, these items can be assigned unique digital identifiers, that can then be used to represent them in a digital context.



## Specification
<!--The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).-->
The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).

### ERC725Y Keys

#### SupportedStandards:LSP12PhygitalAsset

The supported standard SHOULD be `LSP12PhygitalAsset`

```json
{
    "name": "SupportedStandards:LSP12PhygitalAsset",
    "key": "0xeafec4d89fa9619884b6b89135626455000000000000000000000000921f776b",
    "keyType": "Mapping",
    "valueContent": "0x921f776b",
    "valueType": "bytes"
}
```

#### LSP12PhygitalBridge

Describes the method used to bridge the asset between the real and digital world. This method can help for 

The `valueContent` MUST be constructed as follows: 
```
bytesN(bridgeType) + bytesN(signatureAlgorithm)
```

Where:

- `bridgeType` = the type of bridge being used (eg: RFID chip, barcode...)
- `signatureAlgorithm` = the signature algorithm being used for signing (eg: RSA, ECDSA)

```json
{
    "name": "LSP12PhygitalBridge",
    "key": "0x6a49b4af0d4f37c934eba79cf9c70b7a85047e5ebf2c7d35f421d2641e924993",
    "keyType": "Singleton",
    "valueContent": "Mixed",
    "valueType": "bytes"
}
```

> **NB:** could that be a new value type in LSP2, called NFCID

#### LSP12Metadata

The description of the phygital asset.

```json
{
    "name": "LSP12Metadata",
    "key": "0x525bf955e844783b180d9c9f71946568bc5e72258b4eac835700011ff147e2e4",
    "keyType": "Singleton",
    "valueContent": "JSONURL",
    "valueType": "bytes"
}
```

> For construction of the JSONURL value see: [ERC725Y JSON Schema](https://github.com/lukso-network/LIPs/blob/master/LSPs/LSP-2-ERC725YJSONSchema.md#jsonurl-example)

The linked JSON file SHOULD have the following format:

```json
{
    "LSP12Metadata": {
        "description": "string",
        "manufacturer": "string",
        "brand": "string"
        // ...
    }
}
```

#### LSP12Creators[]

An array of addresses of creators.

```json
{
    "name": "LSP12Creators[]",
    "key": "0xdf5e3e7737012077fce988dbefcf5f118c20d07746b00a6e650dd3110ff640f7",
    "keyType": "Array",
    "valueContent": "Address",
    "valueType": "address"
}
```

## Rationale
<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->
The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

## Backwards Compatibility
<!--All LIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The LIP must explain how the author proposes to deal with these incompatibilities. LIP submissions without a sufficient backwards compatibility treatise may be rejected outright.-->
All LIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The LIP must explain how the author proposes to deal with these incompatibilities. LIP submissions without a sufficient backwards compatibility treatise may be rejected outright.

## Test Cases
<!--Test cases for an implementation are mandatory for LIPs that are affecting consensus changes. Other LIPs can choose to include links to test cases if applicable.-->
Test cases for an implementation are mandatory for LIPs that are affecting consensus changes. Other LIPs can choose to include links to test cases if applicable.

## Implementation
<!--The implementations must be completed before any LIP is given status "Final", but it need not be completed before the LIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->
The implementations must be completed before any LIP is given status "Final", but it need not be completed before the LIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
