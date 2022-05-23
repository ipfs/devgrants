# Open Grant Proposal: `NFT Game Machine`

**Name of Project:** NFT Game Machine

**Proposal Category:** `devtools-libraries`, `app-dev` 

**Proposer:** `@kedarkshatriya`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes (MIT License)

# Project Description

## Problem Statement
Currently, if you see the web2 gaming space, we can see two types of development approaches,
* First is from the indie developers like Wukong Game devs, etc.
* Second is from the big companies with huge budgets like EA, Crafton, Xbox studios, etc.

We see few problems here,
1. The first problem is not all indie developers have web3 knowledge or cannot hire web3 developers to build web3 related features in their games (because of the high cost of development)
2. These big companies put a heavy amount of time and funding to build the NFT logic which essentially is redundant considering the vast numbers of games that we see being built using NFT Logic.

Using our idea, we plan to build two different things - one is **a generalized API service**, which can handle all sorts of things like NFT Minting, Transfers, Burning, Storing metadata and assets on IPFS storage solutions, and storing scores related to statistical data, etc.

The second is **a platform** that would give a gateway to different types of indie games just like a play store or an app store. There would be a common player leaderboard system that is tracked across the blockchain. We plan to create a platform for the indie developers who can host their games on it and players could be onboarded on the platform and play these games, bet on multiplayer lobbies which would feature a metaverse like an interactive streaming map or game where they can watch streams and bet on the games while watching.

The most huge gaming markets in the world are PC, Console, and Mobile gaming. All these developers are creating games on centralized servers. They store data like scores, ranking, maps, etc on their own private servers. As these scores are open to all, these data values could be stored on IPFS to be accessed by everyone all over the world. For Example, data like screenshots of the game you are currently playing, if the user wants to share the screenshot with someone it should be accessible to everyone rather than downloading it they can easily just share the IPFS link of the screenshot to their friends.

**We want to revolutionize the gaming industry** and provide them with **a one-stop solution** for all the different problems which occur when we convert a **web2 game to web3**. Things like adding NFTs to game assets, storing assets on the IPFS storage, showing scores and other information over the decentralized platform, etc.

As we have created a prototype - [NFT Game Machine](https://showcase.ethglobal.com/lfgrow/nft-game-machine-qfu59 "NFT Game Machine")  in EthGlobal Hackathon demonstrating a future use of our tool. There are many things in web2 based games where IPFS can be of great use, these types of games have their own statistics stored in the centralized server, statistics as the number of players alive, the survival time of each player, winning player, top 3 players leaderboard, etc, and that too for multiple games/matches. This data doesn't need to be kept private. Whatever gamers need nowadays is to have a transparent system of different things like scores, levels, their unique assets.

In the prototype we have introduced 2 games and converted them to use web3 technology, we have used Tableland to store all the data like scores and levels into the IPFS and used nft.storage and NFTPort storage solutions to store the data like NFT Metadata.json file and image file on the IPFS decentralized storage. We are willing to expand and scale this project in many ways. Recently we have built two separate prototypes with different genres of games, one being a jumper style 3d game ([Crypto Chicken Run](https://devfolio.co/projects/crypto-chicken-run-c1cd "Crypto Chicken Run")) and the other one is a touch based 2d arcade game ([Symbals](https://showcase.ethglobal.com/buildquest/symbals-ewfav "Symbals")).

Our NFT solution would help Game developers to freely mint NFTs of in-game assets like player characters, skins assets and weapon skins, which would help bring utility in any web2 game for example considering our above jumper style game we added utility to add perks and powers to the characters. Now consider games like FIFA, WWE, Mario, Racing Games, we can add NFT utility for them.

## Value

### What are the benefits of getting this right?
The major benefit is that we would have a standard API system or a platform which can transition any web2 based game to a web3 based game. This statement in itself is very powerful because currently there are around a million games in web2 space with an active user base of around a billion players worldwide. Think if these people can enter the blockchain space essentially through different games. This brings mass adoption in the blockchain and in itself to IPFS and Filecoin.


### What are the risks if you dont get it right?
If we dont get adequate funding or grants then it might be difficult to build such a huge robust API service and a potential platform.

## Deliverables

Right now the prototypes we have created are in simple vanilla JS and Dynamic HTML (EJS) as frontend with Express Js as backend. We are planning to develop the frontend with ReactJS from Scratch which is the reason for Hiring Fullstack dev and a react frontend junior developer.

We are planning to build an API service that would provide gasless NFT magic in any web2 game on Polygon Network. All public data will be stored on IPFS. Web2 developers would need to use our APIs in their game engine to mint through our NFT smart contracts. Players could buy and sell NFTs on our marketplace where each games NFT collection would be different just like the Steam marketplace. API would handle services like:

1. Storing metadata
2. Storing images
3. In-game Assets
4. Minting NFTs (ERC721, ERC 1155 - according to the assets used in the game)
5. Buying, selling, and transfer of NFTs in the marketplace.
6. Burning of these NFTs to earn perks
7. API service will provide routes for minting NFTs, transferring NFTs, and enabling a bidding and auction system for a particular NFT. This API will help any game dev creator to fetch and retrieve data regarding the NFTs and load them into the game.

## Development Roadmap


|                          Milestone                           |                           Details                            | Duration | Funding |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :---: |  :-----: |
|                   Planning Phase                     | Planning on building a custom Smart Contract - (Remove NFTPort) which will include 3 smart contracts, one would be a NFT marketplace contract and another two would be ERC721 and ERC1155 smart contracts to handle the NFTs. First Milestone would cover specs docs to be built it would require us around 3 weeks of time. |  3 weeks |  $8000  |
|                   Smart Contract Development V1.0                  | Working on the smart contract building ERC721 smart contract and ERC1155 smart contract and deploying on the Polygon Testnet. Plan to start development of Frontend Marketplace.  |  3 weeks |   $8000  |
|                    Start Frontend Development                    | Start on the development of the ReactJS frontend marketplace, Select designs for the marketplace (1 week), Development of the marketplace page. Continue development of the smart contracts.    |  3 weeks |   $8000  |
|                   Backend API Development                  | Start development on backend API Repo, creating routes for different services like minting, transferring, burning the NFTs with Authentication token from the collection’s owner, etc. Backend will be developed on the new and improved NestJs framework in Nodejs. |  3 weeks |   $8000  |
|                   Smart Contract Development V1.1                  | Development of backend API services, enabling auction and bidding features, and development of the marketplace smart contract. We will focus on the integration for the next milestone.  |  3 weeks |   $8000  |
|                   Beta Integration of Services                  | Integration of the backend API services with the marketplace frontend. Start deployment of the working build on Testnet and temporary CI/CD pipeline to start QA check for the same. Meanwhile, we would also start the outreach and marketing to different developers/companies who are working on various games and give them beta access. |  3 weeks |   $8000  |
|                   Final Integration and Production Deployment                    | Last 2 weeks of the development, production beta deployment for QA purpose, deploying the smart contracts on Polygon Mainnet. Run all the QA tests for load and other checks before release on production. | 2 weeks |     $4500  |


## Funds Distribution

Below is the list of people who would be working on the project for the next 5 - 6 months:

Senior Full Stack developer working full time - $ 4,000 * 5 months = $20,000

Solidity Developer working part time - $2,000 * 5 months = $10,000

Fullstack Developer working part time - $2,000 * 5 months = $10,000

Junior React Frontend developer full time - $1,000 * 5 months = $5,000

QA full time - $1,000 * 5 months = $5,000

Marketing/Outreach Manager Part time - $500 * 5 months = $2,500

### Total Budget Requested

The Total Budget Requested is **$52,500**

# Team

## Team Members

- Kedar Kshatriya [Linkedin Profile](https://www.linkedin.com/in/kedar-kshatriya/) | [Github Profile](https://github.com/kedarkshatriya)

- Vinay Sudrik [Linkedin Profile](https://www.linkedin.com/in/vinaysudrik/) | [Github Profile](https://github.com/optimus789)

## Team Website
- [Link to Live Proof of Concept.](https://nft-game-machine.herokuapp.com/)

## Relevant Experience
- Kedar has Smart contract and Dapp Development experience from the last 2 years. 

- Vinay is a Full Stack Developer with 2 years of experience. We are going to further hire people for Front-end development.

## Team code repositories
- [Our current codebase.](https://github.com/optimus789/nft-game-machine)