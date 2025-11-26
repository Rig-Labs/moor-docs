# Moor Overview

An over-collateralized, decentralized borrowing platform for the Fuel ecosystem.

## Introduction

USDM is an over-collateralized, native stablecoin built on Fuel Network. Borrowers can draw 0% interest-free loans by depositing their collateral, whereby receiving USDM. Fuel Network is the fastest modular execution layer, delivering maximum security and highest flexible throughput.

## Stablecoin Landscape

Decentralized stablecoins have flourished in the last several years, with various design models gaining traction. The protocol design is inspired by leading stablecoin protocols, primarily Liquity protocol. If you are not familiar with Liquity, you can read their docs [here](https://docs.liquity.org/). **These docs assume familiarity with Liquity's mechanism design, so please start there**.

### What We Like About Liquity

- Liquity is fully immutable
- Liquity's stablecoin cannot be shut down or frozen

### Related Protocols

Other relevant protocols in the space:

- **Hedge** - An example of a Liquity-inspired protocol that uses a liquid staked native token as an alternative collateral type
- **MAI** - An example of a stablecoin protocol charging 0% interest + fixed rate fee
- **Vesta** - A Liquity-based protocol on Arbitrum that implements multiple collateral types, although with separate stability pools

## Currency Peg

Moor is committed to meeting the needs of protocol users for a stable digital currency on Fuel. The U.S. Dollar (USD) is an important international reserve and is the most widely used fiat currency in the world.

USDM is a digital asset that is soft-pegged and serves as an equivalent to the USD on a 1:1 ratio. USDM is designed to maintain a price of approximately $1. Given that protocol design is dependent on assumptions about the future, USDM acts a soft peg and does not provide assurances for price stability.

## Differences from Liquity

Of the various protocols that have been inspired by Liquity Protocol, Moor is among the most differentiated in mechanism design, and therefore we will be testing and potentially adjusting all of these factors and parameters during testnet.

| Feature                      | Moor                                                    | Liquity                                              |
| ---------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------- |
| **Minimum Collateral Ratio** | 150%, Fixed                                                      | 110% to 175%, Variable                               |
| **Liquidation**              | Partial                                                          | Full                                                 |
| **Collateral Types**         | Multi-collateral                                                 | ETH only                                             |
| **Stability Pool**           | Single pool yields multiple assets from liquidations             | Yields ETH from liquidations                         |
| **Protocol Token**           | Yields USDM from borrowing, and multiple assets from redemptions | Yields LUSD from borrowing, and ETH from redemptions |

### Fixed CR instead of Recovery Mode

Moor uses a Fixed Minimum CR (Collateral Ratio) of 150% (slightly less than 75% LTV), as the minimum safe ratio. For reference, Aave currently uses 82.50% LTV (Loan to Value) for ETH collateralized loans. During protocol design, we opted not to implement Recovery Mode. Recovery Mode can potentially catch users off guard during periods of high volatility.

Imagine the following situation: You open a trove with 180% CR. Another user opens a trove at 130% CR while Recovery Mode is disabled (because of your position). The price of the native collateral takes a steep dive. The other user is liquidated, the collateral is sold on the market further lowering the collateral price, and now your CR has dipped below 175% as a result of the collateral losing value, and Recovery Mode is activated. You are now subject to be liquidated, potentially near 175%.

Because of the high liquidation risk associated with low CR troves, only a small portion of users actually use such troves. At the time of writing, only 25 out of 630 troves in Liquity are below 150% CR. Liquity's docs also encourage users to maintain a CR above 175%. While Recovery Mode may slightly increase capital efficiency for a small subset of users during calm market conditions, we feel the simplicity and peace of mind of having a hard fixed minimum CR will benefit users in the long term.

## Advantages of Moor

- Interest- free Liquidity
- Fixed Minimum Collateral Ratio (150%)
- Protocol Incentives
- Multi Collateral Types
- Partial Liquidations
- Governance- free Algorithmic Fiscal Policy
- Censorship Resistant

### Multiple Collateral Types

Moor accepts a basket of collateral types, including:

FUEL, ETH, stFUEL

## Liquidation Mechanism and Penalty

Moor is the first Liquity-inspired protocol to support partial liquidations. See [Stability Pool and Liquidations](./04-stability-pool-and-liquidations.md) for more info.
