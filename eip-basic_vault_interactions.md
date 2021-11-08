---
eip: <to be assigned>
title: Basic Vault Interactions
description: Creates a standard interface for investment vaults
author: Facu (@saltyfacu) and Doggie (@fubuloubu)
discussions-to: <URL>
status: Draft
type: Standards Track
category: ERC
created: 2021-11-08
requires: 20
---

## Abstract

This EIP creates a standard for basic operations that can done in a token vault: `deposit`, `withdraw`, and `pricePerShare` calculations.

## Motivation

The implementation of this operations has been battle tested and now issues were found so far. This standard will enable everyone to use a solid method to implement this functions, increase the overall safety of the Ethereum ecosystem.

## Specification

A vault token must always be an ERC20 Token.

### Methods

#### pricePerShare

The conversion ratio between the underlying deposited token and this contract's ERC20 balances

```vyper
    def pricePerShare() -> uint256: view
```

#### deposit

Perform a deposit of `amount` from the caller, with the shares given to the `recipient`.
Returns amount of share token `recipient` receives.

```vyper
def deposit(amount: uint256 = MAX_DEPOSIT, recipient: address = msg.sender) -> uint256: nonpayable
```

#### withdraw

Withdraw up to `maxShares` number of shares, with the redeemed underlying tokens given to `recipient`.
Returns the number of tokens that `recipient` receives.

```vyper
def withdraw(maxShares: uint256 = MAX_WITHDRAW, recipient: address = msg.sender) -> uint256: nonpayable
```

## Rationale

The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages.

## Backwards Compatibility

This has no effect on backwards compatibility.

## Test Cases

TBA

## Reference Implementation

Vaults from Yearn Finance are a good example of the implementation of these operations:

- [Vaults](https://github.com/yearn/yearn-vaults/blob/main/contracts/Vault.vy)

## Security Considerations

TBA

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
