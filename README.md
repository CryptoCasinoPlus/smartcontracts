# CryptoCasino Contracts

## Deployed Contracts on Fuji Testnet CCIP

Avalanche Lending - https://testnet.snowtrace.io/address/0xf25B0cBCA90Ac97e3037488Bb64F0E0D9D706597

ProfileNFTContract - https://testnet.snowtrace.io/address/0x11d839AcBe82440228F0Cd14922A3092f7CaeaC7

## Deployed on Polygon Amoy CCIP

Polygon Lending - https://www.oklink.com/amoy/address/0x42fc1d53ecf8b4c46989da0d44f07490668338c8

ProfileNFTContract - https://www.oklink.com/amoy/address/0x8d36089ab6efdb3feb2d8ed42f7ec80f3c6d2b11/contract

NOTE: CCIP-sender and CCIP-protocol contracts came from: <https://github.com/smartcontractkit/ccip-defi-lending/tree/main/contracts>

They were deployed for reasearch and testing of future cross-chain implementations for our lending contracts.

### Roulette Contract

#### Utilizes Chainlink VRF and Chainlink Automation

The Roulette contract encompasses game logic that allows players to place bets, spin the roulette wheel, and receive payouts. This contract maintains a mapping of *rollers*, tracking which player initiated each Chainlink VRF request. Chainlink VRF is embedded in the *rollDice* function, requesting a random number. The *fulfillRandomness* function is then automatically invoked with the random result. The payout logic is handled within *fulfillRandomness*. This European Roulette game supports all traditional bet types (straight, split, street, corner, six line, column, dozen, red, black, high, low, even, odd) with payouts calculated based on the respective odds of each bet type. Chainlink Automation is triggered upon bet placement, initiating the *upKeep* process that spins the roulette wheel, calculates winnings, and transfers them to the player's wallet.

### Slot Machine Contract

#### Utilizes Chainlink VRF and Chainlink Automation

This contract represents a simple slot game where players bet ether, and hitting the jackpot (a specific random number) results in a multiplied payout. Future enhancements will include multiple winning combinations, varying rewards, and the implementation of a house edge.

### DeFi Cross-Chain Lending

#### Utilizes Chainlink Data Feeds

Players can deposit MATIC as collateral on the Mumbai network or AVAX on the Fuji network to borrow LINK tokens. These lending contracts use Chainlink Data Feeds to fetch the latest asset prices and calculate the maximum Loan-to-Value (LTV). Our long-term vision includes enabling cross-chain gaming, allowing players to obtain any necessary assets for their chosen games. Future improvements will leverage Chainlink's CCIP for secure asset transfers, creating a robust lending protocol that facilitates seamless cross-chain borrowing of assets on both Polygon and Avalanche networks, thereby enhancing the gaming experience without requiring players to sell their assets.

### NFT Minting Contract

#### Utilizes Chainlink Functions and Data Feeds

This contract is central to the community/social aspect of CryptoCasino, allowing each player to mint their own NFT using DALL-E3 (Open AI). The mint logic incorporates Chainlink Functions, where the smart contract calls our custom API and self-hosted IPFS server to generate AI-created images based on user-provided keywords for player NFT profile pictures.

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

## Roulette.sol on Fuji C chain
contract address : 0xf9b55e22Eaa6A834a1De0bAAb69C9aCD52d36995

https://testnet.snowtrace.io/address/0xa6D6f4556B022c0C7051d62E071c0ACecE5a1228?q=0xf9b55e22Eaa6A834a1De0bAAb69C9aCD52d36995
