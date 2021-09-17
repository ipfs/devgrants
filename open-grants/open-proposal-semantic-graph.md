# Open Grant Proposal: IPSG

**Name of Project: IPSG - Interplanetary Semantic Graph**

**Proposer:** Adrian Maurer [(@maurerbot)](https://github.com/maurerbot) on behalf of [Proof Zero](https://github.com/proofzero)

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

Pinning content on IPFS is very easy. However, individual users need to track and maintain a list of CIDs and thier contents. This isn't a very convenient user experience and limits how quickly IPFS can be adopted.

IPFS is missing a transportable semantic layer that provides an open ontology of content for users, plugins, and other systems. With this semantic layer built on top of IPLD, content can be organized into a graph and partitioned for individual users or groups of users for discoverability and collaboration.

Once applied, this content can facilitate novel ways of working.

## Value

Early value of a semantic layer on IPFS would, at the very least, improve the user experience for individuals by providing a familiar way of storing and retrieving content bound to their context. Within their context, users can describe content in arbitrary ways including relationships that link off to other content creating a semantic graph. 

These graphs can be added and retrieved across the network meaning, over time, a global ontology will begin to emerge as a distributed index. The utility of this index would allow novel ways of building applications and extending IPFS with custom plugins and more.

Imagine a financial institution defining an append-only IPLD node called an "account" that can be retrieved by third-party fintechs through authorization via account holder signing keys and multikey encryption for more secure open banking. Or data scientists linking WASM powered notebooks to datasets with static schemas across governance boundaries and only yielding the results to a new node. Or data engineers assembling data pipelines with idempotent and append-only intermediaries with schema on read and write for stable transform pipelines on a distributed data lake. Or a p2p email service....the list goes on.

The risks of not getting this right are the ongoing poorly maintained, centralized datasets containing private information being shared with multiple parties with no governance other than one-sided terms and conditions and privacy policies.

What makes this project difficult is choosing the right interfaces, models, and patterns to make this project scale effectively. Not getting this right may mean a poor user experience and therefore poor adoption.

## Deliverables

### IPSG

An open source library as a configurable extension/plugin embedded into or wrapping the IPFS daemon (TBD). We'd like to work with ProtocolLabs closely on this project to make meaningful decisions that align with the existing projects.

#### Functionality

At a high level, this library will wrap new functionality into IPFS with:
- A means of configuring a local context using IPNS and multikey to partition a subset of the graph.
- An interface for managing contexts.
- An interface for linking CIDs to the graph and their node types.
- An interface for adding ontologies in a format that can be translated to RDF trites/quads.
- An in-memory graph for swapping in/out one or more graph partitions.
- An interface for searching and referencing of nodes.
- A means of adding/retrieving partitions of the RDF graph to IPFS via IPLD.

Stretch goal is to support a naming service, (e.g. IPNS+ENS) and gossipub for subscribing to partitions.

## Development Roadmap

**NOTE:** Due to the size of the project, this roadmap is a bit "hand wavey" but covers the general work to be performed to get a working version of IPSG published.

### Milestone 1 - Interface & Prototype
**Estimate**: ~1 Months
**Team**: All members

This phase will be about defining the proper interface and integrations the IPSG will take. We will need support from ProtocolLabs on this design as it will be the foundation for the entire project.

#### Deliverables
- A whitepaper for reference on design goals, purpose, and functionality.
- Interface specification, ideally as code for code generation.
- Prototype published demonstrating major functionality described above. 

### Milestone 2 - v0.1.xalpha
**Estimate**: ~2 Months
**Team**: All members

This phase will be about building out the first version of IPSG as a standalone library with the minimum amount of functionality to provide utility to any early adopters in order to get fast feedback.

#### Deliverables
- A working version of IPSG that can be installed and configured to work with a forked version of IPFS.


### Milestone 3 - v0.1.xbeta (integration)
**Estimate**: ~3 Months
**Team**: All members

This phase will be about hardening the IPSG and integration the project.

#### Deliverables
- A release candidate of IPFS with IPSG integrated.

## Total Budget Requested

| Milestone | Total |
|-|-|
| Milestone 1 | 5,000 USD |
| Milestone 2 | 10,000 USD |
| Milestone 3 | 15,000 USD |
| **Total** | **30,000 USD** |

**NOTE:** We are asking for the maximum amount to accelerate the development of an existing work stream and fund the work required early on to maintain the project as an open source project.

## Maintenance and Upgrade Plans

Ontologies will be, for the most part, provided by the community but, as a operating business we will be maintaining and contributing to the project continuously to ensure a good experience with the right level of functionality and squashing bugs.

# Team

## Team Members

- [Robert Medeiros](https://github.com/crimeminister)
- [Alexander Flanagan](https://github.com/alfl)
- [Adrian Maurer](https://github.com/maurerbot)

## Team Website

[https://kubelt.com](https://kubelt.com)

## Relevant Experience

The team has 10-20+ years of software development experience each working in small to large gaming studios, marketing, media, startups, financial institutions, telecom, and consulting. Through this experience they've observed the rise of Web2.0 and highly centralized technology and in recent years, due to the lack of innovation, believe we have reached peak Web2.0 tech. 

The team has worked together multiple times in their career and are all web3 enthusiasts. We all agree that the semantic web is "remains largely unrealized" and now is the right time for innovation.

## Team code repositories

- [go-multikeypair](https://github.com/proofzero/go-multikeypair)
- [go-ipld-linkstore](https://github.com/proofzero/go-ipld-linkstore)
- [org](https://github.com/proofzero)

# Additional Information

Proof Zero (operating as kubelt) is a funded startup with a model of building open source tooling for the community and extending that to larger organizations and teams with commercial offerings. As a for profit business, we will also be seeking additional funding in to grow both the open and commercial software.

IPSG a is core to our business and we want to make sure we are making the right decisions that align with the core IPFS, IPLD and Filecoin projects and possibly IPFN. 
