### Software Versions
```
1. Truffle v5.4.33
2. Solidity - ^0.8.12 (solc-js)
3. Node v14.19.0
4. Web3.js v1.5.3
5. Mac M1 Max Pro (macOS Monterey)
6. MongoDB 4.0
```


### PRE-REQUISITE
```
1. nodejs & npm
2. truffle installation
3. gance-cli 
```


### Installation Steps
```
1. brew install nodejs [node -v & npm -v]
2. npm install -g truffle
3. npm install -g ganache-cli
```

### Ganache Deployment (Local Ganche)
```
1. git clone 
2. cd <repo> && npm install --save
3. truffle compile
4. truffle migrate --network ganache 0r truffle migrate --network ganache --reset
4. npm run ganache
```

### TRUFFLE CONSOLE COMMANDS TESTING access control
```
npx truffle console --network ganache
v1 = await DLTSCBTokenV1.deployed()
v1.address
(await v1.getCount())

Non Admin users shouldnt able to access the increment method
(await v1.getCount2({from: accounts[1]}))
(await v1.increment({from: accounts[2]}))
(await v1.increment({from: accounts[3]}))
(await v1.increment({from: accounts[4]}))
(await v1.increment({from: accounts[5]}))

Adding user to USER_ROLE to access the methods
(await v1.addUserRole(accounts[5],{from: accounts[0]}))
(await v1.addUserRole(accounts[2],{from: accounts[0]}))

Newly added user should able to access below methods
(await v1.increment({from: accounts[5]}))
(await v1.getCount2({from: accounts[5]}))
(await v1.increment({from: accounts[5]}))
(await v1.increment({from: accounts[5]}))

revokeUserRole
(await v1.revokeUserRole(accounts[4],{from: accounts[0]}))
(await v1.increment({from: accounts[4]}))
(await v1.decrement2({from: accounts[4]}))

npx truffle console --network ganache
v2 = await ERC20CustomUpgradeableV2.deployed()
v2.address
(await v2.getCount())
(await v2.increment()) x 5
```


