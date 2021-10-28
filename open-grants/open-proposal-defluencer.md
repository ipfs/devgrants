# Open Grant Proposal: `Defluencer`

**Name of Project:** Defluencer

**Proposer:** Simon-Pierre Vivier ([@SionoiS](https://github.com/SionoiS))

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

Social medias apps are centralized data silos right now. I will build social.defluencer.eth, a web3 social media website. It will help me improve my decentralized social media protocol and give a taste of what web3 can do.

I've been working on this project since HackFS 2020. Here's what is fonctional as of now.
 - First we have, adaptative bit-rate live streaming using PubSub, IPLD & IPFS.
 - Second, non-live streaming with adaptative bit-rate is done in a similar way.
 - Third, live chat using PubSub and Metamask (for signatures).
 - Forth, the social web is built with IPNS addresses (ION or ENS could also be used) pointing to a user content and friend list wrapped in an object giving us a CID for every users. (ENS domain names can resolve to this CID)
 - Fifth, IPLD schemas for common social media content.

defluencer.eth the project website W.I.P. -> https://bafybeifuu2njrul54bimwmxhvp6ozz3rwviubwpjutpyixu62allne3nwm.ipfs.dweb.link

I plan to make some part of the protocol more modular. For example, I might use DIDs and different kind of indexing methods. I also want to clarify ownership of content when sharing.

## Value

Crypto/web3 communities could decentralize all their means of communication. IPFS usage would increase as would Filecoin. It would be fertile ground for new businesses; archiving, serving content, transcoding video, AI moderation & filtering, content indexing, etc...

This project is highly dependant on browser integration for; IPFS, IPLD & PubSub.
The current environement is unsuitable for mass adoption as it require too much configuration.
Waiting for fully fonctional IPFS APIs in browser is unproductive as both can be work on in parallel.

## Deliverables

- A decentralized social media website where users can;
    - Create identities with avatar and name.
    - Follow each others to get content updates.
    - Scroll a feed of all the content/comments they and the people they follow created.
    - Watch live streams and chat with the audience.
    - Post videos, micro-blog, photos, articles and comments.
- A report on the scalability of live streaming with IPFS.
- Updates to rust-web3 or an Ethereum Name Service library for Rust.
- Updates to reqwest.
- Updates to rust-ipfs-api.

## Development Roadmap

Start date would be around new year.

### Milestone 1: Libs

Needed crates (rust libs) for the project.
Would allow the crate in the next milestone to be compiled to any rust supported targets including WASM and 90% of the code would be shared between the CLI & website. If the maintainers do not want the changes I propose, I will create forks or new crates with the features I need.

- Pull request to [rust-web3](https://github.com/tomusdrw/rust-web3) with most ENS fonctionalities.
    - Code. (mostly done already)
    - Tests.
    - Documentation.
- Pull request to [reqwest](https://github.com/seanmonstar/reqwest) crate for;
    - WASM support for byte streams
    - WASM support for multipart/form
- Pull request to [rust-ipfs-api](https://github.com/ferristseng/rust-ipfs-api) crate for;
    - WASM support
    - Async IPFS add.

Test the scalability of the live-streaming with [Testground](https://github.com/testground/testground).

Due date 1 April 2022. (3 Months)

### Milestone 2: Fonctionalities

Create and publish a crate (lib) with theses features.

- User Management.
    - Create a new user.
        - Optional linking to ENS domain name.
    - Manage multiple users.
    - Export/Import users crypto keys.
- Content Management.
    - Create new content.
        - Videos.
        - Micro-blog post.
        - Photos.
        - Articles.
        - Comments.
    - Update content.
    - Delete content.
- Content Ownership.
    - Optional Blockchain timestamping. (Bring Your Own Blockchain kinda feature)
    - Optional Cryptographic signatures. (DAG-JOSE)
- Social Web Crawling Tools.
- Content Agregation Tools.

Build a CLI with it.

Due date 1 September 2022. (5 months)

### Milestone 3: UI

Create social.defluencer.eth a decentralized social media website.

Due date 1 January 2023. (4 months)

## Total Budget Requested

| Milestone | Total |
|-|-|
| Milestone 1 | 5,000 USD |
| Milestone 2 | 8,333 USD |
| Milestone 3 | 6,666 USD |
| **Total** | **20,000 USD** |

## Maintenance and Upgrade Plans

The website would receive bug fixes but no new features. Building new websites and apps on the same protocol would be preferable.

The rust ENS crate would require mininal maintenance as the smart-contracts don't change much or be maintained by the rust-web3 community if merged.

The main crate (lib) would hopefully attract contributors, lessening the load on myself as it would be used by multiple apps and websites.

# Team

## Team Members

- Simon-Pierre Vivier ([@SionoiS](https://github.com/SionoiS))

## Relevant Experience

I've been working on the protocol, in my spare time, since HackFS 2020, a lot has been done already but as they say 90% done 90% to go.

## Team code repositories

[Defluencer](https://github.com/Defluencer)

