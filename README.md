# KAP Games

KAP Games is a web3 gaming distributor, publisher & studio, specializing in browser and mobile-native experiences.

Utilizing emerging technologies to unlock the next generation of gaming, KAP curates ecosystems where diverse games, innovative projects, and vibrant communities collide.

[Official docs](https://docs.kap.gg/)

## Tests

### Install node modules

`npm ci`

### Run tests

`npx hardhat test`

GovernanceV2 tests require access to ETH mainnet via a node service. To pass these tests, please fill in the Infura API key in the the `.env` file. To skip these tests, please add `.skip` after the first `describe` in the file.

### Test coverage

`npx hardhat coverage`

## Deployment

- Create a file `./.env`, and fill in missing information from `./.env.example`
- Add a network to `./hardhat.config.js` together with a provider url and relevant private keys as described in the [Hardhat docs](https://hardhat.org/tutorial/deploying-to-a-live-network.html#_7-deploying-to-a-live-network).
- `npx hardhat run scripts/deploy.js --network <network-name>`
- `./hardhat.config.js` has examples (commented out) for the Ropsten and Rinkeby testnets. The localhost network accounts can be overriden if deploying on a locally forked network.
