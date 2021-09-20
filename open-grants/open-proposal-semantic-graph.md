# Open Grant Proposal: IPSG

**Name of Project: IPSG - Interplanetary Semantic Graph**

**Proposer:** Adrian Maurer [(@maurerbot)](https://github.com/maurerbot) on behalf of [Proof Zero](https://github.com/proofzero)

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

Pinning content on IPFS is very easy. However, individual users need to track and maintain a list of CIDs and their contents. This isn't a very convenient user experience and limits how quickly IPFS can be adopted. This issue is exacerbated by IPLD.

IPFS is missing a distributed semantic layer that provides an open system for defining and working with ontologies that describe content for users, plugins, and other systems. With this semantic layer built on top of IPFS, content can be organized into a graph and partitioned for individual users or groups of users for discoverability and collaboration.

Once applied, these building blocks can facilitate novel ways of working and building applications.

## Value

A semantic layer on IPFS would improve the user experience for individuals by providing a familiar way of storing and retrieving content bound to their context. Within their context, users can describe content in arbitrary ways including relationships that link to other content. These links create semantic graphs.

These graphs can be added to and retrieved across the network. Over time, a global ontology will begin to emerge within the distributed graph. This distributed graph effectively forms an index of IPFS data that would allow novel ways of building applications and extending IPFS with custom plugins:

* Imagine a financial institution defining an append-only IPLD node type called "account" that can be retrieved by third-party fintechs for more secure open banking.
* Data scientists linking WASM-powered notebook node types to schema-powered dataset node types to collaborate.
* Data engineers assembling data pipelines with idempotent and append-only schema-powered intermediate objects for faster and more stable transformation pipelines on a distributed data lake.
* A p2p email service compliant with IM2000 that enables a new ecosystem of encryption-first email clients.
* Distributed, decentralized, open commentary systems on blockchains, torrents, git repositories, traditional web sites, etc. 
* Standardized CRDTs that are translatable across applications.
* etc.

Most/all contemporary SaaS applications can be re-architected to use common data formats to allow for greater data portability with consistent, strong guarantees of privay and security. IPSG is an attempt to bridge Web 2.0 applications and ways of working (centralized) to a decentralized web3 model, by providing the next level of abstraction -- open, standard, building blocks -- required for wider adoption.

The risks of not getting this right are the ongoing poorly maintained, centralized datasets containing private information being shared with multiple parties with no controls other than one-sided terms and conditions and privacy policies. This means decentralization breaks down at the corporate/legal level. We need better alternatives and reasonable standards that support web3 scale beyond technology.

What makes this project difficult is choosing the right interfaces, models, and patterns to make this project scale effectively. Not getting this right may mean a poor user experience and therefore poor adoption. Working on small enough scope to demonstrate broad utility will be a challenge that needs community feedback to address.

## Deliverables

### IPSG

An open source library aacting as a configurable extension/plugin embedded into or wrapping the IPFS daemon (TBD). We'd like to work closely with ProtocolLabs on this project to make meaningful decisions that align with existing projects and provide utility to existing users.

#### Components

The below will be implemented with an existing graph database engine that targets IPFS/IPLD storage, along with configurable-but-opinionated RDF representations and cryptography. Current implementation is inspired by, and compatible with, IPLD Prime LinkSystems and multiformats.

#### Functionality

At a high level, this library will add several new functional areas to IPFS:

##### Multikey / Multicontext

Cryptograaphic identity, signing, and encrypted storage is core to IPSG. Building on our existing [`go-multikeypair`](https://github.com/proofzero/go-multikeypair) work (see below, upstreaming intended) we want IPSG to provide a configurable, flexible cryptosystem on top of IPFS.

The semantics that describe content on IPSG can be specific to individuals, groups, or global. Allowing users of IPSG to create and select contexts when working against IPSG will provide users the ability to organize their content according to work/application environment. For example, someone can run a local node for both personal and work purposes, working on the same CIDs, and segment their work personally and professionally.

Configuring a context is the same as creating a set of keypairs used to partition your view of the content stored on IPFS. Contexts help inform IPSG on how to partition, join, and search the semantic graph and are linked to an IPNS address.

##### Ontologies / Naming

The ontologies used in any semantic graph are assembled into "kinds" which are organized into higher-order "kinds" through linking in the graph. On a use-case basis, a kind can then terminate to a set of CIDs containing any value/content. We intend to support standard ontologies that the community expresses interest in, for example [schema.org](https://schema.org).

For example, a "person" kind can be standalone and linked to a CID that represents a json blob describing a person. Alternatively a "person" can link off to a "first name" and "last name" kind that terminate to strings containing the names -- the choice is up to the user/application implementation. This method of terminating to values is similar to creating an instance/node of that kind. Every instance is assigned a name by the user and indexed to its context.

This allows IPSG to be wrapped with plugins, extensions or other tools for working with kinds.

##### Distribution / Partitioning

For practicality, these ontologies and semantic indexes are stored globally to IPFS as RDF quads and indexed though IPNS linked contexts. Indexes stored by context allows every IPSG node to operate a partition of the index that is reasonably sized and contains content only relevant to that peer. IPNS update time, efficient index sizing with respect to block packing, etc., are factors entering into our determination of reasonable defaults, however are also intended to be configurable.

Joining or merging of these ontologies happen within an IPSG peer node after retrieving one or more contexts before re-added to IPFS.

##### Pathing / Search

Nodes and links within the semantic graph contain relevant metadata for search by property or path queries. IPSG will provide an interface for making these queries.

#####  Extras

Stretch goal is to support a naming service, (e.g. IPNS+ENS) and gossipub for subscribing to changes in partitions of the graph.

## Development Roadmap

**NOTE:** Due to the size of the project, this roadmap is focused on clear next steps to demonstrate community value, then becomes broader when discussing general work to be performed for a complete version of IPSG.

### Milestone 1 - Interface & Prototype
**Estimate**: 1-2 Months
**Team**: All members

This phase will be about defining the proper interface and integrations for IPSG. We will need support from ProtocolLabs on this design as it will be the foundation for the entire project.

#### Deliverables
- A whitepaper for reference on design goals, purpose, and functionality.
- Interface specification, ideally in a form suitable for code generation.
- Prototype published demonstrating major functional areas described above. 

### Milestone 2 - v0.1.xalpha
**Estimate**: 2-4 Months
**Team**: All members

This phase will be about building out the first version of IPSG as a standalone library with the minimum amount of functionality to provide utility to any early adopters in order to get fast feedback.

#### Deliverables

- A working version of IPSG that can be installed and configured to work as a library, plugin, or as an IPFS fork.
- Potentially includes a high-pass analysis of the cryptosystem.

### Milestone 3 - v0.1.xbeta (integration)
**Estimate**: 3-6 Months
**Team**: All members

This phase will be about hardening the IPSG and integration the project.

#### Deliverables

- A release candidate of IPFS (fork, library, plugin, etc. as above) with IPSG integrated.

## Total Budget Requested

| Milestone | Total |
|-|-|
| Milestone 1 | 5,000 USD |
| Milestone 2 | 10,000 USD |
| Milestone 3 | 15,000 USD |
| **Total** | **30,000 USD** |

**NOTE:** We are asking for the maximum amount to accelerate the development of an existing work stream and fund the work required to maintain the project as an open source project. We intended to match allocated funds.

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

The team has 50+ years of software development experience spanning small to large gaming studios, marketing, media, startups, financial institutions, telecom, and consulting. Through this experience they've observed the rise of Web 2.0 and highly centralized technology. In recent years, due to the lack of innovation, we believe the industry has reached peak Web 2.0. 

The team has worked together multiple times in their career and are all web3 enthusiasts. We all agree that the semantic web remains largely unrealized and now is the right time to deliver on its promise.

## Team code repositories

- [go-multikeypair](https://github.com/proofzero/go-multikeypair)
- [go-ipld-linkstore](https://github.com/proofzero/go-ipld-linkstore)
- [org](https://github.com/proofzero)

# Additional Information

Proof Zero (operating as kubelt) is a funded startup with a model of building open source tooling for the community and extending that to larger organizations and teams with commercial offerings. As a for-profit business, we will also be seeking additional funding to increase our rate of open source contributions.

IPSG is core to our business and we want to make sure we are making the right decisions that align with the core IPFS, IPLD, IPNS, and Filecoin projects (and possibly IPFN).
