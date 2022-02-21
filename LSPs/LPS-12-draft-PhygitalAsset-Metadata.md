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

This standard describes a set of [ERC725Y](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-725.md) keys that can be used to bind a real world asset to a digital space.

## Abstract

## Motivation

There is an upcoming requirement to transfer property of physical property to digital spaces *(explain why)*.
Using RFID chips attached to physical items, these items can be assigned unique digital identifiers, that can then be used to represent them in a digital context.



## Specification

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


## Backwards Compatibility


## Test Cases

## Implementation


## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
