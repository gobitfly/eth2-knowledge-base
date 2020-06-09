# Run a Slasher using prysm.sh

## General

The slasher's purpose is to find malicious validators and report slashable offenses to a validator, who then needs to include that information into its block proposal.  
****  
**Slashable offenses**

* **Double voting:** An **attester** signs two different attestations which have the same target.
* **Surround votes:** An **attester** and sign an attestation that surrounds another one.
* **Double block proposal:** A **block** **proposer** signs two different blocks for the same slot.

![](../../.gitbook/assets/image%20%2869%29.png)

