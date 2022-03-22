# Open Grant Proposal: `Emergent Reputation`

**Name of Project:** Emergent Reputation

**Proposer:** `@ckartik`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

## Problem Statment
**Cyberspace** can abstractly be seen as a means of infomation distribution.
In a general sense, most applications can be broken down to two key objects: 
**Users & Content**. The focus of current network infrastructure (layers below Application on OSI the Model)
 has been **content**, ensuring the content is _Authenticated (Certificates),
and holds Integirty (Hashes)_. However, it failed to provide any similar cryptographic provisions for the **Users** 
creating & consuming this content leading internet engineers to overload this into the Application Layer.
The provisions relevant to Users are _Reputation & Trust_. Because of these being held at the application layer, 
monoplistic organizations _(Twitter, Meta)_ have gained **intitutionalized control** over these attributes without governance.

The **monoplistic** nature of these organizations has lead them to create suboptimal solutions to _Reputation & Trust_ for users
and, they lack any incentive to improve the state of Trust.


I purpose that the instablility this creates leaves significant slack left for leveraging the Internet as large-scale social coordination system.
This RFC presents a solution to this problem through the development of a **distributed graph data-structure** that mimics
single-degree trust relationships held in the physical world for each user. This would help emerge a larger a web-of-trust that is highly composable
at the application layer of traditional applications. Through the development of IPLD as a basis for distributing a decentralized data-structure
such as the social graph, and the proliferation of wallets & blockchains as a mechanism for providing signing capabilities to browsers, this 
is the first time that a viable solution that could be adopted with low friction has ever been possible.

There are three key components to the imlementation of the solution, for which a working [POC (here)](https://github.com/ckartik/Emergent-Reputation) has been enabled on testnet.
1. The **edges** of the graph will be stored on IPLD, we will call these attestations.
2. The **nodes** will be as a keys to a map stored on a Smart Contract, and will be drived from the wallet account number.
3. An **engine** will be provided in the library to provide the following functionality:
    - Addition of nodes & attestations
    - Revocation of attestations
    - Graph algorithims for driving proxy determinations of trust (Shortest Path, K-connectedness, etc)
    - If possible, we would also like to conduct research into mechanisms for zero knowledge transfer of trust information.
        - Particularly research conducted to judge the usefulness of hyperedges as a method for providing privacy


### What are the benefits to getting this right?
With the right execution, this technology could remove the propensity of sybil attacks currently seens on Social Media platforms.
It would also lead to community driven censorship, rather than a centralized control of deplatforming that can be abused.
The technology is inherently composable with other platforms that can build on top of it.
### What are the risks if you don't get it right?
A failed execution could lead to a fragmented development of trust on Web 3.0. Ensuring the architecture can be built with forsight
in mind is also important.
### What are the risks that will make executing on this project difficult?
Difficult to get inflection point adoption to get value out of network effects

## Deliverables

Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.

## Development Roadmap


|                          Milestone                           |                           Details                            | Hours & Expected Completion |         Assignees          | Funding | 
| :----------------------------------------------------------: | :----------------------------------------------------------: | :---: | :------------------------: | :-----: |
|                   Library Architecture                   | Look into high-level architecture for the final library. This stage will help in determining access patterns for the core social graph. It will entail usability research.|  50 hours - May 10, 2022 |       `ckartik`        |  $3000  |
|                       Composable Library V0                   |       Convert POC into easily useable npm module architecture    |  30 hours - May 25, 2022  | `ckartik` |  $1500  |
|                       Composable Library V0.1                 |       Add several graph algorithims for proxy determinations of reputation   |  50 hours - June 28, 2022 | `ckartik` |  $3000  |
|                       Composable Library V1.1                 |       Deploy contract to Testnet & Provide mechanisms to easily connect.    |  30 hours - July 28, 2022  | `ckartik` |  $1500  |
|                       Composable Library V1.2                 |       Deploy the contract to mainnet, and allow library to connect to both Testnet & Mainnet    |  50 hours - August 28, 2022   | `ckartik` |  $2000  |
|                     Cryptonomics Research                    | Complete research around the cryptonomics that would drive meaninful attestations and mechanisms for incentivising business to compensate the graph for usablilty. Publish this research into public domain. |  150 hours - June 28, 2022    |       `ckartik`        |  $8000  |
|                Hypergraph Research for ZK                | Hypergraphs are a generalization of a graph where the edges can be of arbitrary size. An edge in a typical graph is restricted to two. There is intutively a credible mechanism for providing levels of privacy by turning highly connected regions of this social graph automatically into hyperedges. |  180 hours - July 15, 2022   | `ckartik`|  $8500  |


# Team

## Team Members

- Kartik Chopra [Linkedin Profile](https://www.linkedin.com/in/mathbiz/) | [Github Profile](https://github.com/ckartik)


<!-- ## Value
TODO: @ckartik

This section should be 1-3 paragraphs long.



## Total Budget Requested

Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.

## Maintenance and Upgrade Plans

Specify your team's long-term plans to maintain this software and upgrade it over time.

# Team

## Team Members

- Team Member 1 [profile]
- Team Member 2 [profile]
- Team Member 3 [profile]
- ...

## Team Website

Please link to your team's website here (make sure it's `https`)

## Relevant Experience

Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.

## Team code repositories

Please provide links to your team's prior code repos for similar or related projects.

# Additional Information

Please include any additional information that you think would be useful in helping us to evaluate your proposal. -->
