# Governance and Immutability

Moor operates without governance. Protocol parameters are predefined and immutable or algorithmically controlled by the protocol itself, rendering governance unnecessary. The long-term roadmap aims to fully remove contract upgradeability from the protocol. However, given the nascent state of the Fuel network and the Sway ecosystem, launching without upgradeability isn't currently viable. For instance, the availability of high-quality oracle options on Fuel is limited. In contrast, Liquity utilizes Chainlink price feeds with a fallback to Tellor, both of which are well-established and reliable. Unexpected bugs in the early stages of Moor or within the underlying Fuel Network may necessitate upgrades. Additionally, adapting to changing standards and ensuring compatibility of the protocol and USDM might require updates. New collateral types will also need to be incorporated post-launch based on factors like underlying adoption.

The criteria for removing upgradeability are as follows:

- Availability of at least two long-term stable oracle price feeds for collateral.

- A minimum of six months of beta deployment on the mainnet without incidents.

Once these criteria are met, contract upgradeability will be disabled, rendering the protocol fully immutable.
