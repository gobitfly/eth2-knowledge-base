## Beaconcha.in Charts Explained
___
## [Overview of all charts](https://beaconcha.in/charts)
___

### [Blocks](https://beaconcha.in/charts/blocks)

Displays all the [proposed, missed or oprhaned Blocks](https://kb.beaconcha.in/glossary#block-status) for a specific time period. 

<ins>Blue candles</ins> = Proposed Blocks , <ins>Green candles</ins> = Missed Blocks , <ins>Orange candles</ins> = Orphaned Blocks

![blocksGIF](https://user-images.githubusercontent.com/26490734/78765940-f3bd3d00-7988-11ea-8734-e6fd35f4e710.gif)
---

### [Validators](https://beaconcha.in/charts/validators)

Displays the amount of [validators](https://kb.beaconcha.in/glossary#validator) for each timestamp.

![testnetValitdators](https://user-images.githubusercontent.com/26490734/78768801-bb1f6280-798c-11ea-91f1-4780830542ee.png)
---

### [Staked Ether](https://beaconcha.in/charts/staked_ether)

Displays the total amount of staked Ether [(*effective* balance)](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance).

![stakedEth](https://user-images.githubusercontent.com/26490734/78771349-52d28000-7990-11ea-9ba6-8ba9904e7f4c.png)
---

### [Validator Balance](https://beaconcha.in/charts/average_balance)

Displays the [current average validator balance](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance).

![currentValidatorBalance](https://user-images.githubusercontent.com/26490734/78773270-46035b80-7993-11ea-9ab8-e3c64a63b761.png)
---

### [Network Liveness](https://beaconcha.in/charts/network_liveness)

Displays how far the last finalized [Epoch](https://kb.beaconcha.in/glossary#epoch) compared to the Head Epoch took place.
A minimum of 2 epochs is caused by how [finalization](https://kb.beaconcha.in/glossary#finalization) works. An empty timestamp as shown in the picture can be interpreted as a finalization problem. In that case **all** [validators](https://kb.beaconcha.in/glossary#validator) get punished.

![networkLiveness](https://user-images.githubusercontent.com/26490734/78787440-a4880400-79aa-11ea-83c3-d8f57990b964.png)
---

### [Participation Rate](https://beaconcha.in/charts/participation_rate)

Displays the participation of validators in the chosen time period.

<sub> *Calculation: Participation rate = (number of attestations in last epoch) / (number of attesting validators)* </sub>

![participationRate](https://user-images.githubusercontent.com/26490734/78873463-39dad500-7a4b-11ea-801d-635fdfac0ce8.png)
---

### [Average daily validator income](https://beaconcha.in/charts/validator_income)

Displays the average income of all [validators](https://kb.beaconcha.in/glossary#validator) per day starting off at the [genisis block](https://en.bitcoin.it/wiki/Genesis_block).

![averageDailyIncome](https://user-images.githubusercontent.com/26490734/78872647-e4ea8f00-7a49-11ea-9bfa-625fc747e9e6.png)
---

### [Staking Rewards](https://beaconcha.in/charts/staking_rewards)

Displays the sum of all staking rewards and punishments of all validators on a specific day. 

**Example** in the picture below: 1471.15 ETH have been lost on Februar 7th.

![stakingRewardsPerDay](https://user-images.githubusercontent.com/26490734/78907107-8bea1d80-7a80-11ea-8cd1-29259862a4b4.png)
---

### [Stake Effectiveness](https://beaconcha.in/charts/stake_effectiveness)

Measurement of the relation between [effective balance](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance) [validator](https://kb.beaconcha.in/glossary#validator) and [current balance](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance) [validator](https://kb.beaconcha.in/glossary#validator) of **all validators**. 100% means that the total locked ETH is actively being staked. Due to the fact that the effective balance cannot increase more than 32, but the **current balance can**, the Stake effectiveness decreases. 

![stakeEffectiveness](https://user-images.githubusercontent.com/26490734/78873129-a3a6af00-7a4a-11ea-977d-03d182c573b8.png)
---

### [Balance Distribution](https://beaconcha.in/charts/balance_distribution)

Displays the distribution of [current balances](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance) of all [validators](https://kb.beaconcha.in/glossary#validator) for the current epoch. 

**Example** in the picture below: 5404 validators at 3.28ETH .

![balanceDistribution](https://user-images.githubusercontent.com/26490734/78874403-a3a7ae80-7a4c-11ea-9527-356ce17e81f6.png)
---

### [Effective Balance Distribution](https://beaconcha.in/charts/effective_balance_distribution)

Displays the distribution of [effective balances](https://kb.beaconcha.in/glossary#current-balance-and-effective-balance) of all [validators](https://kb.beaconcha.in/glossary#validator). 

**Example** in the picture below: 2200 at have an effective balance of 3ETH.

![effectiveBalanceDistribution](https://user-images.githubusercontent.com/26490734/78874836-49f3b400-7a4d-11ea-83f3-8254a94a0611.png)
---

### [Income Distribution of the last 365 Days](https://beaconcha.in/charts/performance_distribution_365d)

Displays the income distribution of all [validators](https://kb.beaconcha.in/glossary#validator) of the last 365 days. 

**Example** in the picture below: 38 validators have gained 0.020360794 ETH.

![incomeDistribution](https://user-images.githubusercontent.com/26490734/78877206-c63bc680-7a50-11ea-901b-ab27a404c581.png)
---




