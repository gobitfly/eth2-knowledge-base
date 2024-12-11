---
description: Manage notifications in the v2 dashboard
---

# ⏰ WIP: Notifications v2

## Requirements

* beaconcha.in acccount&#x20;
  * Register [here](https://beaconcha.in/register)
  * Login [here](https://v2-beta-mainnet.beaconcha.in/login)
* Configure notifications [here](https://v2-beta-mainnet.beaconcha.in/notifications)

<figure><img src="../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>



## Overview

* **A**: Shows whether email notifications are enabled.
* **B**: Daily email limit. The limit resets at 00:00 UTC. Upgrading to a higher [premium](https://v2-beta-mainnet.beaconcha.in/pricing) tier increases this limit.
* **C**: Indicates whether push notifications for the mobile app are enabled.
* **D**: Notification history. Notifications for dashboards, machines, clients, and network events will appear in dedicated tabs.
* **E**: Set up or manage your notifications in this section.

<figure><img src="../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>



## Setting up v2 notifications via web

### Validator notifications

V2 notifications are group-based, meaning you can set validator notifications for each [group](validator-groups.md) configured on the [validator dashboard](https://v2-beta-mainnet.beaconcha.in/dashboard).

To set up notifications:

1. Make sure you have created a [validator dashboard](https://v2-beta-mainnet.beaconcha.in/dashboard) first.
2. Go to [https://v2-beta-mainnet.beaconcha.in/notifications#dashboards](https://v2-beta-mainnet.beaconcha.in/notifications#dashboards).
3. Click on `Manage Notifications`.
4. Ensure email and push notifications are **enabled**.
5. Send a test notification to confirm you receive notifications.
6. Go to the Dashboard tab, select the group, and edit the subscription column.

<figure><img src="../.gitbook/assets/Export-1733926931270.gif" alt=""><figcaption></figcaption></figure>

### Validator notifications via webhook



1. Follow the steps in [Validator Notifications](wip-notifications-v2.md#validator-notifications)
2. Click the Edit icon in the webhook column.
3. Add your webhook URL.
   1. Check the 'Send via Discord' box if notifications should be sent to a [Discord channel](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks).
4. Send a test notification to ensure everything is working.
5. Click Save.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Client notifications

To set up notifications for EL and CL clients like Geth, Nimbus, or Erigon, go to the Clients tab.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Network notifications

To set up notifications for Gas prices, Rocket Pool reward round or Participation rate of the network, go to the Networks tab.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>



