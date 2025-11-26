# Earn via the Stability Pool and Liquidations

Liquidation mechanism and stability pool overview

## Earn Yield through the Stability Pool

Similar to Liquity Protocol, users can earn and generate yield via the Stability Pool, which is the first line of defense in maintaining system solvency. It achieves this by acting as the source of liquidity to repay debt from liquidated Troves, ensuring that the total supply of USDM always remains fully backed. Stability pool deposits both absorb and cancel associated debt from Troves that have defaulted.

The Stability Pool is funded by users transferring USDM into it (otherwise known as Stability Providers). Over time, Stability Providers lose a pro-rata share of their USDM deposits, while gaining a pro-rata share of the liquidated collateral. However, because Troves are likely to be liquidated at just below `150%` collateral ratios, it is expected that Stability Providers will receive a greater dollar-value of collateral relative to the debt they pay off.

Users can withdraw collateral from the stability pool at any time when there are no troves below 150% CR.

### Depositors

Similar to Liquity, depositing USDM into the stability pool is effectively a way to gain exposure to their collateral. Stability Pool participants are rewarded with the acquisition of collateral from liquidated positions at a significant discount. Whenever liquidations occur, depositors are effectively buying the underlying collateral at a discount, usually around a 10% discount from market prices.

### Redistribution

If the Stability Pool is empty, the system uses a secondary liquidation mechanism called redistribution. In such a case, the system redistributes the debt and collateral from liquidated Troves to all other existing Troves. The redistribution of debt and collateral is done in proportion to the recipient Trove's collateral amount.

### Single Stability Pool

There is only one stability pool in Moor. This is to ensure there is enough collateral to handle large liquidations and prevent liquidity fragmentation. Stability pool providers will earn exposure to their collateral.

## Partial Liquidations

When a Trove is liquidated, the amount of USDM contained in the Trove multiplied by the Close Factor is burned from the Stability Pool's balance to repay its debt.

In exchange, 110% of the corresponding dollar value amount of collateral from the Trove is transferred to the Stability Pool (minus 0.5% liquidation gas fee). For instance, if a user is liquidated on a 1000 USDM Trove at 130% CR, $500 in USDM will be repaid by the stability pool. $550 (110% of 500) of collateral is then sent to the stability pool (minus 0.5% liquidation gas fee). Now the Trove is left with 500 USDM debt and $750 in collateral, returning the user to a safe CR of 175%. Stability pool participants earn roughly the same fee as in Liquity (~10%). The Close Factor is hardcoded at 50%, the same factor used by Aave, Compound, and MAI. Partial liquidations are the norm in DeFi, used by Aave, Compound, and MAI among others. Moor is the first Liquity-inspired protocol to use partial liquidations.

### Benefits of Partial Liquidations

Partial Liquidations protect and therefore retain users in the protocol. Losing 10% of an entire Trove in one liquidation is a large financial loss for users. Most importantly, Partial Liquidations soften market impact from liquidation sell-offs, reducing the systemic risk of a Liquidation Cascade. Partial liquidations also reduce the amount of idle USDM needed to be sitting in the stability at a giving time, increasing overall efficiency of the system and the velocity of money.

## Triggering Liquidations

Users can run liquidation bots or manually liquidate insolvent users without putting up any collateral. Therefore, the liquidation reward is relatively modest, as the only costs associated with liquidation are gas fees, which on Fuel Network are expected to be extremely low.

`gas compensation = 0.5% of liquidated collateral`

Gas compensation originates from liquidated collateral, slightly reducing the liquidation gain for Stability Providers. We do not include a fixed USDM gas compensation, as we expect the gas fees on Fuel Network to be exceptionally low. Not having a fixed USDM liquidation reserve also supports unlimited partial liquidations.
