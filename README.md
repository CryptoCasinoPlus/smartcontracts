# CryptoCasinoPlus Contracts

## Deployments


## Deployed Contracts on Fuji Testnet CCIP

Avalanche Lending - (https://testnet.snowtrace.io/address/0xf25B0cBCA90Ac97e3037488Bb64F0E0D9D706597)

ProfileNFTContract - https://testnet.snowtrace.io/address/0x11d839AcBe82440228F0Cd14922A3092f7CaeaC7

## Deployed on Polygon Amoy CCIP

Polygon Lending - https://www.oklink.com/amoy/address/0x42fc1d53ecf8b4c46989da0d44f07490668338c8

ProfileNFTContract - https://www.oklink.com/amoy/address/0x8d36089ab6efdb3feb2d8ed42f7ec80f3c6d2b11/contract

### Polygon Amoy Network (VRF)

| Contract               | Address                                           |
| ---------------------- | --------------------------------------------------|
| roulette               | [`0x`][1] |
| slots                  | [`0x`][2] |
| lend/borrow            | [`0x`][3] |


NOTE: CCIP-sender and CCIP-protocol contracts came from: <https://github.com/smartcontractkit/ccip-defi-lending/tree/main/contracts>
They were deployed for reasearch and testing of future cross-chain implementations for our lending contracts.

## Contract Overview

### Roulette Contract

#### Uses Chainink VRF and Chainlink Automation

The game logic includes the functionality for players to place bets, initiate the roulette spin, and receive payouts. This contract maintains mapping of *rollers*, tracking who triggered each Chainlink VRF request.
Chainlink VRF is integrated in the *rollDice* function, which requests a random number. The fulfillRandomness function is called automatically with the random result once it's ready.
The payout logic is handled in fulfillRandomness. This roulette game is European Roulette and covers all possible bet types (straight, split, street, corner, six line, column, dozen, red, black, high, low, even. odd) and the payout will be calculated based on the respective odds of each win.
Chainlink Automation is implemented when a user places a bet. The upKeep is triggered after the bet is placed to automatically roll the dice (really spin the roulette wheel) then automatically calculate winnings and withdraw them to your wallet.

### Slot Machine Contract

#### Uses Chainink VRF and Chainlink Automation

This is a simple slot game where a user bets a certain amount of ether, and if they hit the jackpot (represented by a specific random number), they win a multiplier of their bet. For future improvements, implement different winning combinations, varying rewards, and a house edge.

### DeFi Cross-Chain Lending

#### Uses Data Feeds

You can either deposit MATIC as collateral and borrow LINK on the Mumbai network or you can deposit AVAX as collateral and borrow LINK tokens on the Fuji network. These lending contracts use chain link data feeds to fetch the latest price for each asset and uses that price to calculate max LTV. In the future we would also need to calculate
Since the lomg term vision for BetBlock is to enable cross-chain gaming, we want to enable players to be able to come to BetBlock and get any asset they may need for the game of their choice.
Future improvements would be leveraging Chainlink's CCIP for secure asset transfers to create a robust lending protocol that allows gamers on both Polygon and Avalanche to seamlessly borrow assets cross-chain. This would enhance the gaming experience by enabling players to access the resources they need without selling on of their assets.

### NFT Minting Contract

#### Uses Functions and Data Feeds

Function acts a core piece for the community/social aspect of our product where every player will be able to mint their own NFT using DALL-E3 (Open AI). Specifcally functions is implemented in the mint logic where the smart contract will call our own API and self hosted IPFS server to create AI generated images using input key words for player NFT PFPs

### Hardhat Setup

#### This was only used for Fuji deployments

```shell
npx hardhat compile
npx hardhat setup-nft-contract --network fuji
npx hardhat setup-lending-contract --network fuji
```


## VRF on Fuji C Chain 
subscription ID : 2808 or 2809 or 2810
contract address : 0xFB94b68c174d3e9fa739029fc244bBD9297E819D - 
https://testnet.snowtrace.io/address/0xFB94b68c174d3e9fa739029fc244bBD9297E819D

Consumer Transaction: https://testnet.snowtrace.io/tx/0x05a135f20151b6ac60ad8f859d0f86fb483f05b589355c269dfe777c244d3a95

## VRF on Polygon Amoy Testnet 
subscription ID : 15 and 16

contract address - 0x5E4e5347eB417982375Ef9BDe0B77F4322FCF79F 
https://www.oklink.com/amoy/address/0x5e4e5347eb417982375ef9bde0b77f4322fcf79f

## Roulette.sol on Polygon Amoy
contract address : 0xfBeFdC343861EDc521dD2512B4B64B33bB663E4d

https://www.oklink.com/amoy/address/0xfbefdc343861edc521dd2512b4b64b33bb663e4d

## Roulette.sol on Fiji C chain
contract address : 0xf9b55e22Eaa6A834a1De0bAAb69C9aCD52d36995

https://testnet.snowtrace.io/address/0xa6D6f4556B022c0C7051d62E071c0ACecE5a1228?q=0xf9b55e22Eaa6A834a1De0bAAb69C9aCD52d36995