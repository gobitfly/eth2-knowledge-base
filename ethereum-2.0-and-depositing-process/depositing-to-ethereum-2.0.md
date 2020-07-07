# Depositing to Ethereum 2.0

## Warning

**The following steps occur on a Ethereum Testnet with Goerli Testnet-ETH and might be outdated for the Ethereum main-net launch.**

## **Requirements**

There are multiple wallets and possibilities, however, let's demonstrate the most common way for the average user. 

* [MyCrypto](https://beta.mycrypto.com/add-account)
* Prysm Client to **create** Ethereum 2.0 keys \([macOS](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/macos-prysm/run-with-macos-using-prysm.sh#step-3) or [Windows](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/windows-prysm/script-beaconnode-and-validator#step-4)\)
* at least 32 Goerli Testnet ETH \(ask on [Discord](https://discord.gg/gmSMfrF)\)

## Create **ETH 2.0 K**eys

For demonstration purposes the Prysm Client will be used to create Ethereum 2.0 keys, any other Ethereum 2.0 client would work as well.  
  
Create your own keys - on [macOS](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/macos-prysm/run-with-macos-using-prysm.sh#step-3) or [Windows](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/windows-prysm/script-beaconnode-and-validator#step-4)

![Key generation](../.gitbook/assets/image%20%2895%29.png)

These 842 letters are the Ethereum 2.0 validator [identity](https://kb.beaconcha.in/ethereum-2-keys).

```bash
0x22895118000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000120afd078c8e46733de1c116df653afef908cc7a809009b375ffab943f495974a700000000000000000000000000000000000000000000000000000000000000030a10010049908f68bdf86baaae2c4e1df7456f11f1f0124c25ebeeb7541ac34d6562782694d316c7a912259e2d7b4e59000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002000040231464d41e1c646c708bd84fe5fd4dcc6fa2f4d9bfdfa64f40c974618c80000000000000000000000000000000000000000000000000000000000000060a4884293664737cb4860033c0150b91915ccbc9ab1337eae5b4ec70f38cddc64d2db5a450ccd667ae9ab7d0f2ae35cd40c97e3a086e57f77a489b7d73e0ad9532134906671a086dd369bd3e10b52cbc648bf352ee18aea6c7ec2fec11053aaa00x22895118000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000120afd078c8e46733de1c116df653afef908cc7a809009b375ffab943f495974a700000000000000000000000000000000000000000000000000000000000000030a10010049908f68bdf86baaae2c4e1df7456f11f1f0124c25ebeeb7541ac34d6562782694d316c7a912259e2d7b4e59000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002000040231464d41e1c646c708bd84fe5fd4dcc6fa2f4d9bfdfa64f40c974618c80000000000000000000000000000000000000000000000000000000000000060a4884293664737cb4860033c0150b91915ccbc9ab1337eae5b4ec70f38cddc64d2db5a450ccd667ae9ab7d0f2ae35cd40c97e3a086e57f77a489b7d73e0ad9532134906671a086dd369bd3e10b52cbc648bf352ee18aea6c7ec2fec11053aaa0
```

  
These letters, **the input data**, have to be included into the transaction to the deposit contract.

###  Depositing

1. Open [MyCrypto](https://beta.mycrypto.com/add-account) and open your wallet and head over to _**Send Assets**_. 
2. **Advanced options** Paste the 842 letters into the **Data field** `0x22895118000000000000000000...`. 
3. **Recipient** is the deposit contract **Onyx** Testnet**:** `0x0F0F0fc0530007361933EaB5DB97d09aCDD6C1c8` **Altona** Multiclient Testnet**:** `0x16e82D77882A663454Ef92806b7DeCa1D394810f` 
4. **Amount** Minimum of 1 ETH
5. **Gas Limit** 500,000
6. Send transaction
7. Track your deposit on the [beaconcha.in](https://beaconcha.in/validators/eth1deposits) explorer with your Ethereum 1.0 address

![Transaction Overview](../.gitbook/assets/image%20%28101%29.png)



