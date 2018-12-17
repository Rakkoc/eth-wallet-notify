# eth-wallet-notify
- Track wallet accounts.
- Track wanted Erc20 token transfer.
- Track block number for confirmations count.

## General Description
 A sample "replacement" to bitcoind wallet-notify logic , 
 Using [web3](https://github.com/ethereum/web3.js/) with [Node 8+](https://nodejs.org/en/).
 
 Tested on windows and ubuntu 18.04, using local [parity](https://github.com/paritytech/parity-ethereum/releases/tag/v2.1.10) full node.
 
 you can use infura node, but first change the code to get your wanted account list.
 check out [config.js](https://github.com/orelkabets/eth-wallet-notify/blob/master/config.js)
 
## Requirements
- [Node 8+](https://nodejs.org/en/)
- [Yarn (optional)](https://yarnpkg.com/en/)

## Setup
```
npm install
npm start

or 
yarn install
```


## Setup as a daemon service for ubuntu using systemctl
create a new file at your service folder (usually at /etc/systemd/system) :
```
nano /etc/systemd/system/eth-wallet-notify.service
```
and past in the following:
```
[Unit]
Description=Eth Blockchain Tracker
After=network.target

[Service]
Environment=NODE_PORT=3001
Type=simple
User=ubuntu
ExecStart=/usr/bin/node <path-to-eth-wallet-notify>/src/index.js
Restart=always
RestartSec=1s

[Install]
WantedBy=multi-user.target

```
then run:
```
systemctl enable eth-wallet-notify
systemctl start eth-wallet-notify
```


