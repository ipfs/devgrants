# Open Grant Proposal: `Defluencer`

**Name of Project:** Defluencer

**Proposer:** Simon-Pierre Vivier ([@SionoiS](https://github.com/SionoiS))

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description
Social medias are centralized data silos right now. I want to build social.defluencer.eth, a web3 social media website using the [decentralized influencer toolkit](https://github.com/SionoiS/dit). It would help me improve the protocol and give a taste of what web3 can do.

Imagine a fully decentralized social media experience that can do;
- Live streaming.
- Live chat with moderation tools.
- Video streaming.
- Micro-blog or long articles.

All this data on IPFS, interoperable by default.

## Value
Crypto/web3 communities could decentralize all their means of communication. IPFS usage would increase as would Filecoin. It would be fertile ground for new businesses; archiving, serving content, transcoding video, AI moderation & filtering, content indexing, etc...

This project is highly dependant on browser integration for; IPFS, IPLD & PubSub.
The current environement is unsuitable for mass adoption as it require too much configuration.
Waiting for fully fonctional IPFS APIs in browser is unproductive as both can be work on in parallel.

## Deliverables
Users can;
- Create identities with avatar and name.
- Follow each others to get updates on new content.
- Scroll a feed of all the content/comments they and the people they follow created.
- Live stream or watch other user's streams and chat live with the audience.
- Post videos, micro-blog, photos, articles and comments.

## Development Roadmap
Start date would be around new year.
### Milestone 1: Libs
Needed crates (rust libs) for the project.
Would allow the crate in the next milestone to be compiled to any rust supported targets including WASM.
- Create and publish a fully featured ENS crate to crates.io
    - Tests.
    - Docs.
    - Code. (mostly done already, just need to fix some bugs)
- Update [reqwest](https://github.com/seanmonstar/reqwest)
    - WASM support for byte streams
    - WASM support for multipart/form
- Update [rust-ipfs-api](https://github.com/ferristseng/rust-ipfs-api)
    - WASM support

Due date 1 March 2022. (2 Months)

### Milestone 2: Fonctionalities
Create and publish a crate (lib) with theses features.
- User Management.
    - Create a new user.
        - Optional linking to ENS domain name.
    - Manage multiple users.
    - Export IPNS keys.
    - Import IPNS keys.
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
    - Blockchain timestamping.
    - Cryptographic signatures.
- Social Web Crawling.
    - Find new content.
    - Find new friends.
- Content Agregation.
    - Crawl the web or open a channel to receive content.
    - Filter content.
    - Clearly display content you do not own.

Build a CLI with it.

Due date 1 September 2022. (6 months)

### Milestone 3: UI

A fully featured social media web app.

Due date 1 January 2023. (4 months)

## Total Budget Requested

Life cost for a year. 25k CAD.

## Maintenance and Upgrade Plans

A protocol does not need maintenance. The website would receive bug fixes but no new features. Building new website and apps on the same protocol would be preferable. The rust ENS crate would require mininal maintenance as the smart-contract does not change much.

The main crate (lib) would hopefully attract contributors, lessening the load on myself as it would be used by multiple apps and websites.

# Team

## Team Members

- Simon-Pierre Vivier ([@SionoiS](https://github.com/SionoiS))

## Relevant Experience

I've been working on the protocol, in my spare time, since HackFS 2020, a lot has been done already but as they say 90% done 90% to go.

## Team code repositories

[Decentralized Influencer Toolkit](https://github.com/SionoiS/dit)

