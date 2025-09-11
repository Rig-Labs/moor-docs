# Redemption

Any USDM holder can redeem for underlying collateral at any time

## How it works

USDM is a fully redeemable stablecoin. When USDM is redeemed, the collateral provided to the redeemer is allocated from the Trove(s) with the lowest collateral ratio (CR), even if it is above `135%`. If at the time of redemption you have the Trove with the lowest ratio, you will surrender some of your collateral, but your debt will be reduced accordingly. The recommended way to avoid having your trove redeemed is to keep your CR well above the minimum threshold.

The USD value by which your collateral is reduced corresponds to the nominal USDM amount by which your Trove's debt is decreased. You can think of redemptions as if somebody else is repaying your debt and retrieving an equivalent amount of your collateral. As a positive side effect, redemptions improve the collateral ratio of the affected Troves, making them less risky.

Redemptions that do not reduce your debt to 0 are partial redemptions, while redemptions that fully pay off a Trove's debt are called full redemptions. In such a case, your Trove is closed, and you can claim your collateral surplus at any time.

When redeemed, the system uses the USDM to repay the riskiest Trove(s) based on the lowest collateral ratio, and transfers the respective amount of collateral from the affected positions to the redeemer. The amount drawn from each borrower is limited by their corresponding debt, so the affected borrowers can retain their collateral surpluses. Thus, borrowers no longer retain the same nominal amount of debt (in USDM) as they lose collateral (in USD) and do not endure a net loss resulting from redemptions. On the contrary, redemptions do have a positive effect on the total collateralization of the protocol, improving robustness and stability.

## Multiple Collateral Types

Unlike other multi-collateral Liquity-based protocols, Moor Protocol does not allow redeemers to choose a particular collateral. Instead, redeemers are distributed a pro-rata share of their collateral types. The lowest CR Troves from each collateral type will be chosen during redemption.

For example: Moor Protocol consists of 60% collateral units with an oracle market price of $2, and 40% of Liquid Staked collateral units with a market price of $1.8. A USDM holder who redeems 600 USDM will receive 180 collateral units`(60% * 600 / 2)` + 133.33 Liquid Staked collateral units `(40% * 600 / 1.8)` minus the redemption fee.

## Redemption Fee

Similar to Liquity, Moor Protocol charges a redemption fee. instead of using a variable baserate, the redemption fee is fixed at 1%.
