# Optimal Inclusion Distance

\
The attestation for `slot 156508` was included in `slot 156510` but why is the inclusion distance 0?\
If were to use the formula from above and set the inclusion delay to 0, the rewards would be 0 for a proposed attestation

![](<../.gitbook/assets/image (169).png>)

Missed blocks are **not added** to the inclusion distance, but since the attestant is not responsible for the block proposal, and to only warn the user about its faults (e.g. slow internet connection, power failure etc.), the [beaconcha.in explorer](https://beaconcha.in/) displays the distance as 0.
