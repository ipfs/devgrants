# Open Grant Proposal: `Emergent Reputation`
 
**Name of Project:** Emergent Reputation
 
**Proposer:** `@ckartik`
 
**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes
 
# Project Description
 
## Problem Statement
**Cyberspace** can abstractly be seen as a means of information distribution.
In a general sense, most applications can be broken down into two key objects:
**Users & Content**. The focus of the current network infrastructure (layers below Application on OSI the Model)
has been **content**, ensuring the content is _Authenticated (Certificates)
and holds Integrity (Hashes)_. However, it failed to provide any similar cryptographic provisions for the **Users**
creating & consuming this content leading internet engineers to overload this into the Application Layer.
The provisions relevant to Users are _Reputation & Trust_. Because of these being held at the application layer,
monopolistic organizations _(Twitter, Meta)_ have gained **institutionalized control** over these attributes without governance.
 
The **monopolistic** nature of these organizations has led them to create suboptimal solutions to _Reputation & Trust_ of users
and, they lack any incentive to improve the state of Trust.
 
 
I purpose that the instability this creates leaves significant slack left for leveraging the Internet as a large-scale social coordination system.
This RFC presents a solution to this problem through the development of a **distributed graph data structure** that mimics
single-degree trust relationships held in the physical world for each user. This would help emerge a larger web-of-trust that is highly composable
at the application layer of traditional applications. Through the development of IPLD as a basis for distributing a decentralized data-structure
such as the social graph, and the proliferation of wallets & blockchains as a mechanism for providing signing capabilities to browsers, this
is the first time that a viable solution that could be adopted with low friction has ever been possible.
 
There are three key components to the implementation of the solution, for which a working [POC (here)](https://github.com/ckartik/Emergent-Reputation) has been enabled on testnet.
1. The **edges** of the graph will be stored on IPLD, we will call these attestations.
2. The **nodes** will be a key to a map stored on a Smart Contract, and will be driven from the wallet account number.
3. An **engine** will be provided in the library to provide the following functionality:
   - Addition of nodes & attestations
   - Revocation of attestations
   - Graph algorithms for driving proxy determinations of trust (Shortest Path, K-connectedness, etc)
   - If possible, we would also like to conduct research into mechanisms for zero-knowledge transfer of trust information.
       - Particularly research conducted to judge the usefulness of hyperedges as a method for providing privacy
 
 
### What are the benefits of getting this right?
With the right execution, this technology could remove the propensity of Sybil attacks currently seen on Social Media platforms.
It would also lead to community-driven censorship, rather than centralized control of censorship that can be abused.
The technology is inherently composable with other platforms that can build on top of it.
### What are the risks if you don't get it right?
A failed execution could lead to a fragmented development of trust on Web 3.0. Ensuring the architecture can be built with foresight
in mind is also important.
### What are the risks that will make executing this project difficult?
Difficult to get inflection point adoption to get value out of network effects
 
## Deliverables
 
Please describe in detail what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.
 
## Development Roadmap
 
 
|                          Milestone                           |                           Details                            | Hours & Expected Completion |         Assignees          | Funding |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :---: | :------------------------: | :-----: |
|                   Library Architecture                     | Look into high-level architecture for the final library. This stage will help in determining access patterns for the core social graph. It will entail usability research. |  50 hours - May 10, 2022 |       `ckartik`        |  $2000  |
|                   Composable Library V0                    | Convert POC into easily useable npm module architecture.    |  40 hours - May 25, 2022  | `ckartik` |  $2000  |
|                   Composable Library V0.1                  | Add several graph algorithms for proxy determinations of reputation.   |  50 hours - June 28, 2022 | `ckartik` |  $2000  |
|                   Composable Library V1.1                  | Deploy contract to Testnet & Provide mechanisms to easily connect.|  40 hours - July 28, 2022  | `ckartik` |  $2000  |
|                   Composable Library V1.2                  | Deploy the contract to mainnet, and allow the library to connect to both Testnet & Mainnet. |  50 hours - August 28, 2022   | `ckartik` |  $2000  |
|                   Cryptonomics Research                    | Complete research around the cryptonomics that would drive meaningful attestations and mechanisms for incentivizing businesses to compensate the graph for usability. Publish this research into the public domain. |  150 hours - June 28, 2022    |       `ckartik`        |  $4000  |
|                   Hypergraph Research for ZK               | Hypergraphs are a generalization of a graph where the edges can be of arbitrary cardinality. An edge in a typical graph is restricted to be a subset of two objects from the vertext set. There is intuitively a credible mechanism for providing levels of privacy by turning highly connected regions of this social graph automatically into hyperedges. |  180 hours - July 15, 2022   | `ckartik`|  $4000  |
 
 
# Team
 
## Team Members
 
- Kartik Chopra [Linkedin Profile](https://www.linkedin.com/in/mathbiz/) | [Github Profile](https://github.com/ckartik)
 
## Team Website
- [Link](https://showcase.ethglobal.com/buildquest/tki-trust-key-infrastructure-er66f) to ETHGlobal showcase.
 
## Relevant Experience
- Kartik has a junior background in Applied Cryptography & Network engineering.
- Kartik previously worked:
   - As a Programmer for the Canadian Military
   - A Network Security Developer at [ISARA Corporation](https://www.isara.com/) with a focus on Network Cryptography & authentication systems like PKI.
   - Currently works at FinTech as a backend engineer, researching cryptocurrencies.
   - Has an academic background in Computer Science from the University of Waterloo with a focus on Network Security & Cryptography
 
## Team code repositories
- Here are some of Kartik's Repositories:
   - [Emergent Repuatation POC](https://github.com/ckartik/Emergent-Reputation)
   - [A system for tracking CIDs to implementing Versioning on IPFS](https://github.com/DougAnderson444/HydroFile)
   - [Enterprise NFT platform](https://showcase.ethglobal.com/roadtoweb3/nft-bridge)


