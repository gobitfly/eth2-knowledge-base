---
description: >-
  A step by step tutorial on how to monitor your staking device & beaconnode on
  the beaconcha.in mobile app.
---

# Mobile App &lt;&gt; Node Monitoring

## General

This is a free monitoring tool provided by [beaconcha.in](https://beaconcha.in/) to enhance the solo staking experience. The user specifies the monitoring endpoint on its beacon & validator node.  


![](../.gitbook/assets/image%20%28209%29.png)

_By using this endpoint, beaconcha.in will be allowed and is required to store the given data to display it in the beaconcha.in the mobile application. To protect user privacy, the IP address will **never** be stored._  


### **Requirements**

* beaconcha.in [Account](https://beaconcha.in/register) 
* beaconcha.in [Mobile App](https://beaconcha.in/mobile) 
* **Lighthouse**  [**v.1.4.0**](https://github.com/sigp/lighthouse/releases) or higher
* **Prysm** [**v1.3.10**](https://github.com/prysmaticlabs/prysm/releases) or higher
* Staking on Linux \(No windows support by clients yet!\)

{% hint style="info" %}
**Please adjust the network on the beaconcha.in browser and mobile app accordingly.**
{% endhint %}

Both, the beaconcha.in [explorer](https://github.com/gobitfly/eth2-beaconchain-explorer) and the [mobile app](https://github.com/gobitfly/eth2-beaconchain-explorer-app) are open source!

## Lighthouse

_A step by step guide on the Prater Testnet. Please adjust the network for your own needs._

1. Head over to the [user settings](https://beaconcha.in/user/settings#api) on beaconcha.in and create an API key 

![](../.gitbook/assets/image%20%2811%29.png)

1. Open the **Mobile App** Tab and enter a name for your staking setup.  _Use the same worker name even if your beaconnode runs on a seperate machine than your validator node._

![beaconcha.in/user/settings](../.gitbook/assets/grafik%20%282%29.png)

3. Copy the generated flag and paste it add it to your beacon & validator node

![Lighthouse Beacon &amp; Validator node](../.gitbook/assets/image%20%2822%29.png)

_If your beacon-node or Ethereum 1.0 node is not in sync yet, you will see some warning logs!_

4. Open the [beaconcha.in mobile app](https://beaconcha.in/mobile) and login with your account under _Preferences._  
     Your staking device will appear under Machines!  


![](../.gitbook/assets/grafik%20%285%29.png)

## Prysm

{% hint style="danger" %}
This functionality is in its early stage alpha testing and may not be fully functional at this time.
{% endhint %}

1. Head over to the [user settings](https://beaconcha.in/user/settings) on beaconcha.in 
2. Open the **Mobile App** Tab and enter a name for your staking setup.  _Use the same worker name even if your beaconnode runs on a seperate machine than your validator node._ 
3. Make sure your **prysm.sh** file is updated and supports client-stats Updated version: [https://raw.githubusercontent.com/prysmaticlabs/prysm/develop/prysm.sh](https://raw.githubusercontent.com/prysmaticlabs/prysm/develop/prysm.sh) 
4. Open an extra terminal next to your validator and beacon-node and modify **YOUR-API-KEY** and **DEVICE-NAME**  


   _Use the same worker name even if your beaconnode runs on a seperate machine than your validator node._

  
   `./prysm.sh client-stats --beacon-node-metrics-url=`[`http://localhost:8080/metrics`](http://localhost:8080/metrics) `--validator-metrics-url=`[`http://localhost:8081/metrics`](http://localhost:8081/metrics) `--clientstats-api-url=https://beaconcha.in/api/v1/client/metrics?apikey=`**`<YOUR-API-KEY>`**`&machine=`**`<DEVICE-NAME>`**

**Docs:** [**https://docs.prylabs.network/docs/prysm-usage/client-stats/**](https://docs.prylabs.network/docs/prysm-usage/client-stats/)\*\*\*\*

## Nimbus 



## Teku

