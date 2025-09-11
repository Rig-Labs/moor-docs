# Borrowing

Choosing a collateral and creating a Trove

## Use Cases

Moor Protocol allows users the ability to unlock liquidity from their collateral to use as they please. Instead of selling your collateral to participate in DeFi or other activities, you can borrow USDM and retain your collateral when you repay the loan. As long as you maintain your Collateral Ratio above 135%, you can keep your loan as long as you would like. Moor Protocol supplies liquidity without charging borrowers interest or recurring fees.

## Multi-Collateral

In Moor Protocol, there is only one redemption mechanism and one stability pool across the user's collateral types. This is practical because of the similarity between collateral types and the small number of collateral types. However, collateral types have their own separate price feeds.

_Accepted collateral types include: FUEL, ETH, stFUEL_

## Borrowing Fee

Moor protocol uses a fixed borrowing and redemption rate. Similar to the decision to not implement recovery mode, we found that this simplifies the codebase without significantly changing anything for average users. The borrowing fee is added to the debt of the Trove. The protocol charges a one time Borrowing Fee for newly drawn liquidity to support a USD based peg. The fee rate is fixed at `0.5%` and is multiplied by the amount of liquidity drawn by the borrower.

The redemption fee is charged when a user redeems USDM for underlying collateral. The redemption fee is fixed at 1%.

For example: The borrowing fee stands at `0.5%` and the borrower wants to receive `4,000 USDM` to their wallet. Being charged a borrowing fee of `20.00 USDM`, the borrower will incur a debt of `4,020 USDM` after the issuance fee is added.

## Troves

After locking up collateral in a smart contract and creating an individual position called a "Trove", the user can get instant liquidity in a permissionless manner by minting USDM. A Trove is where you take out and maintain your loan. Each Trove is linked to a user's address and each address can hold just one Trove. If you are familiar with Vaults or CDPs (Collateralized Debt Positions) from other platforms, Troves are similar in concept.

Troves maintain two balances: one is an asset acting as collateral and the other is a debt denominated in USDM. You can change the amount of each by adding collateral or repaying debt. As you make these balance changes, your Trove's collateral ratio changes accordingly.

You can close your Trove at any time by fully paying off your debt.

## Collateral Ratio

The collateral ratio of your trove is the ratio between the Dollar value of the collateral in your Trove and it's debt in USDM. The collateral ratio of your Trove will fluctuate over time as the price of collateral changes. You can modify the ratio by adjusting your Trove's collateral and/or debt — i.e. adding more collateral or paying off some of your debt. Similar to Liquity, since the borrower's debt is denominated in USDM, the current value of collateral is expressed in USD.

For example: Let's say the current price of your collateral is `$100` and you decide to deposit 40 units. If you borrow `2,000 USDM`, then the collateral ratio for your Trove would be `200%`.

The minimum collateral ratio (or MCR for short) is the lowest ratio of debt to collateral that will **not** trigger a liquidation. This is a protocol parameter that is set to `135%`. Thus, if your Trove has a debt of `10,000 USDM`, you would need at least `$13,500` worth of posted collateral to avoid being liquidated.

To avoid liquidation, it is recommended to keep the collateral ratio comfortably above `135%` (e.g. `200%` or more `250%`). It's important to note, that redemptions are suspended if the Total Collateral Ratio (TCR) is below 135%. This can prevent the system from experiencing situations similar to bank runs.
