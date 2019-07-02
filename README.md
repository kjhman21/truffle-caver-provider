# truffle-caver-provider
HD Wallet-enabled provider. This source was forked from [truffle-hdwallet-provider](https://github.com/trufflesuite/truffle/tree/master/packages/truffle-hdwallet-provider) and modified to work with Klaytn network. Use it to sign transactions for addresses derived from a 12 or 24 word mnemonic or any private key.

## Install

```
$ npm install truffle-caver-provider
```

## Requirements
```
Node >= 7.6
Web3 1.0.0-beta.37
```

## Truffle Usage

You can easily use this within a Truffle configuration. For instance:

truffle-config.js
```javascript
const CaverProvider = require("truffle-caver-provider");

const mnemonic = "mountains supernatural bird ...";

module.exports = {
  networks: {
    development: {
      host: "localhost",
      port: 8545,
      network_id: "*" // Match any network id
    },
    baobab: {
      // must be a thunk, otherwise truffle commands may hang in CI
      provider: () =>
        new CaverProvider(mnemonic, "https://api.baobab.klaytn.net:8651"),
      network_id: '1001', //Klaytn baobab testnet's network id
      gas: ‘2000000’,
      gasPrice: ‘25000000000’,
    }
  }
};
```

You can also use private key.

truffle-config.js
```javascript
const CaverProvider = require("truffle-caver-provider");

const privateKey = "0x...";

module.exports = {
  networks: {
    baobab: {
      provider: () =>
        new CaverProvider(privateKey, "https://api.baobab.klaytn.net:8651"),
      network_id: '1001', //Klaytn baobab testnet's network id
      gas: ‘2000000’,
      gasPrice: ‘25000000000’,
    }
  }
};
```
