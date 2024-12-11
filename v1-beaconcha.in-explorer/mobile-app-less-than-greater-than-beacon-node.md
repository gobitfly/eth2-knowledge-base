---
description: >-
  A step by step tutorial on how to monitor your staking device & beaconnode on
  the beaconcha.in mobile app
---

# Mobile App <> Node Monitoring

## General

This is a free monitoring tool provided by [beaconcha.in](https://beaconcha.in/) to enhance the solo staking experience. The user specifies the monitoring endpoint on its beacon & validator node.

![](<../.gitbook/assets/image (152).png>)

_By using this endpoint, beaconcha.in will be allowed and is required to store the given data to display it in the beaconcha.in the mobile application. To protect user privacy, the IP address will **never** be stored_

### **Requirements**

* beaconcha.in [Account](https://beaconcha.in/register)
* beaconcha.in [Mobile App](https://beaconcha.in/mobile)
* **Lighthouse** [**v.1.4.0**](https://github.com/sigp/lighthouse/releases) or higher
* **Prysm** [**v1.3.10**](https://github.com/prysmaticlabs/prysm/releases) or higher
* **Nimbus** [**v1.4.1**](https://github.com/status-im/nimbus-eth2/releases) **or higher**
* **Teku v22.3.0 or higher**
* **Lodestar** [**v1.6.0**](https://github.com/ChainSafe/lodestar/releases) **or higher**
* Staking on Linux (No windows support by clients yet!)

{% hint style="info" %}
**Please adjust the network on the beaconcha.in browser and mobile app accordingly.**
{% endhint %}

Both, the beaconcha.in [explorer](https://github.com/gobitfly/eth2-beaconchain-explorer) and the [mobile app](https://github.com/gobitfly/eth2-beaconchain-explorer-app) are open source!

## Lighthouse

_A step by step guide on the Prater Testnet. Please adjust the network for your own needs._

1. Open the [**Mobile App** ](https://beaconcha.in/user/settings#app)Tab and enter a name for your staking setup.\
   &#xNAN;_&#x55;se the same worker name even if your beaconnode runs on a seperate machine than your validator node._\
   \_\_\
   \_\_Copy the generated flag and paste it add it to your **beacon & validator node**\
   \_\_

![](../.gitbook/assets/mspaint_2021-08-05_08-47-46.png)

![](../.gitbook/assets/mspaint_2021-08-05_08-59-42.png)

_If your beacon-node or Ethereum 1.0 node is not in sync yet, you will see some warning logs!_

\
2\. Open the [beaconcha.in mobile app](https://beaconcha.in/mobile) and login with your account under _Preferences._\
Your staking device will appear under _Machines_ !

![](<../.gitbook/assets/grafik (5).png>)

## Prysm

1. Head over to the [beaconcha.in settings](https://beaconcha.in/user/settings#app) and open the prysm section:

![](../.gitbook/assets/firefox_2021-08-05_09-51-26.png)

2\. Open a **new Terminal** and copy paste the commands

![](../.gitbook/assets/AnyDesk_2021-08-05_09-09-52.png)

![](../.gitbook/assets/mspaint_2021-08-05_09-53-29.png)

3\. Make sure your Prysm client (beacon & validator) is already up and running. The exporter will now send the data to your mobile app!

![](../.gitbook/assets/mspaint_2021-08-05_09-55-15.png)

4\. Wait a few minutes and open the [beaconcha.in mobile app](https://beaconcha.in/mobile) and login with your account under _Preferences._\
\
Your staking device will appear under _Machines_ !

![](<../.gitbook/assets/grafik (5).png>)

## Nimbus

1. Head over to the [beaconcha.in settings](https://beaconcha.in/user/settings#app) and open the nimbus section:

![](../.gitbook/assets/mspaint_2021-08-05_10-14-30.png)

2\. Add `--metrics --metrics-port=8008` to your nimbus client! Otherwise the exporter will not be able to get any data from your client.

![](../.gitbook/assets/mspaint_2021-08-05_10-13-08.png)

3\. Wait a few minutes and open the [beaconcha.in mobile app](https://beaconcha.in/mobile) and login with your account under _Preferences._\
\
Your staking device will appear under _Machines_ !

![](<../.gitbook/assets/grafik (5).png>)

## Teku

Add the following endpoint to your teku node `--metrics-publish-endpoint https://beaconcha.in/api/v1/client/metrics?apikey=YOUR_API_KEY`

You can find your API Key here: [https://beaconcha.in/user/settings#app](https://beaconcha.in/user/settings#app)

## Lodestar

Add the following CLI flag to your Lodestar validator and beaconnode `--monitoring.endpoint 'https://beaconcha.in/api/v1/client/metrics?apikey=YOUR_API_KEY'`

You can find your API Key in the [account settings](https://beaconcha.in/user/settings#api).

Check out the Lodestar documentation about [client monitoring](https://chainsafe.github.io/lodestar/usage/client-monitoring/) for further details.

## Monitoring with Rocket Pool

**Works with Lighthouse, Lodestar, Teku and Nimbus only.**

\*\*\*\*\
**Lighthouse, Lodestar and Teku**

Add Your [beaconcha.in API key ](https://beaconcha.in/user/settings#app)in Monitoring/Metrics (service config)

![](<../.gitbook/assets/image (1).png>)\*\*\*\*

***

**Nimbus**

Nimbus does not expose every data, thus, some data such as validators are not visible in the app.

Guide: [https://gist.github.com/jshufro/89e32d417801bf3dfb02c32a983b63cf](https://gist.github.com/jshufro/89e32d417801bf3dfb02c32a983b63cf)

***

## Gnosis

Just as on Ethereum, the flag can be found at [https://beaconcha.in/user/settings#app](https://beaconcha.in/user/settings#app) **OR** [https://gnosischa.in/user/settings#app](https://gnosischa.in/user/settings#app).&#x20;

Please note that the API key for beaconcha.in users is the same on gnosischa.in, so it doesn't matter which one is chosen.&#x20;

The same applies to the flag in the instructions. However, it's recommended to use the beaconcha.in endpoint as it offers several fallbacks.&#x20;

The best support for the metric feature is available using the Lighthouse client. Other clients **may not work or may only support a limited number of metrics in the app.**
