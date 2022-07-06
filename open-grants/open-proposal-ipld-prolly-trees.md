# Open Grant Proposal: IPLD Prolly Trees

**Name of Project:** IPLD Prolly Trees

**Proposal Category:** `app-dev`

**Proposer:** KEN Labs, ch3, Mauve

**Technical Sponsor:** Dietrich, Mikeal

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

<!--
Please describe exactly what you are planning to build. Make sure to include the following:
- Start with the need or problem you are trying to solve with this project.
- Describe why your solution is going to adequately solve this problem.

This section should be 2-3 paragraphs long.
-->

The IPLD ecosystem contains many sources of data and many ways to represent said data. However, when dealing with large datasets, it's important to have a way to quickly search through them in an efficient manner. The present state of IPLD based applications such as blockchains requires data to be indexed with external database engines in order to make it efficient enough to query. We propose creating an IPLD-native data structure which will enable projects to build database indexes without needing to rely on external database engines.

This grant will take previous work on [Peer to Peer Ordered Search Indexes](https://0fps.net/2020/12/19/peer-to-peer-ordered-search-indexes/) / [Prolly Trees](https://github.com/mikeal/prolly-trees) and formalize it into a standard data structure within the IPLD ecosystem including specs for a new IPLD ADL (advanced data layout), an official implementation in golang and one in JavaScript, and a library which builds on top of the tree structure to create automatic indexes for IPLD data based on the [hyperbeedeebee](https://gist.github.com/RangerMauve/ae271204054b62d9a649d70b7d218191) indexing scheme.

This grant will also take steps to formalize the performance implications of using this data structure for indexing in the context of merging indexes between peers, and read/write throughput. The findings will be published online along side the source code.

## Value

<!--
Please describe in more detail why this proposal is valuable for the IPLD ecosystem. Answer the following questions:
- What are the benefits to getting this right?
- What are the risks if you don't get it right?
- What are the risks that will make executing on this project difficult?

This section should be 1-3 paragraphs long.
-->

The main benefit from this grant will be to make it easier for applications to work with large datasets of IPLD data in efficient ways. Blockchains and local-first applications currently need to run local databases on semi-centralized "full nodes" in order to make data available to end users which imposes a limit on users ability to work with and access data directly between each other.
With an easy to use indexing library, applications will be able to be built which generate indexes for users data locally on their machines/networks and to efficiently combine indexes into larger datasets without requiring full replication of data between peers (very important for performance and UX).

Due to the foundational nature of decentralized indexes, they will be valuable for a veriety of applications in the IPLD/IPFS/FIL ecosystem fom general purpose databases, search indexes, and CRDT synchronization mechanisms.


### Risks

We will need to pay extra attention to developer UX so that it potential users of the spec will be able to pick it up with little effort. Similarly we will need to pay attention to the wording in the spec and the distribution of the spec IPLD Schema so that future implementations in other languages or environments will be able to remain compatible with the initial implementations.

We need to evaluate the impact of different Rolling Hash algorithms and window size on performance. This could lead to variation in the the performance of the final implementation and will be important to study.
* Rabin Karp
* Buzhash

## Deliverables

- IPLD Based ADL Spec for Prolly Trees in a similar format to the [HAMT ADL](https://ipld.io/specs/advanced-data-layouts/hamt/spec/) along with an MVP implementation in golang
- Golang implementation of the ProllyTree ADL similar to the [HAMT ADL](https://github.com/filecoin-project/go-hamt-ipld)
- Implementation of library that builds IPLD based indexes on top of the tree ADL + contains a high level query language in Golang
- Example application which enables smart contract interact with Prolly tree IPLD indexing.
- Accompanying research that will show the strengths and limitations of the approach as well as the feasibility of different applications and use cases for the data structure.

## Development Roadmap

<!--
Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).

For each milestone, please describe:
- The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.
- How many people will be working on each milestone and their roles
- The amount of funding required for each milestone
- How much time this milestone will take to achieve (using real dates)
-->

### Milestone 1 - IPLD Schema and MVP implementation

Outputs: A detailed specification for IPLD Prolly Trees complete with an IPLD Schema for how the data should be structured, documentation describing how to create and balance these trees, and an initial Golang implementation using the schema and balancing to create trees in memory. A document comprising the research materials that were used to come up with the implementation.

Engineering: People working on this: 5

- Initial research on Prolly Trees: 120 Hours, 3 Weeks * 3
    - noms & doltdb project study:https://github.com/attic-labs/noms 
    - Hyperbee-deebee project study:https://github.com/RangerMauve/hyperbeedeebee 
- IPLD Schema for Prolly Trees: : 40 Hours, 1 Weeks * 3
- Initial Go library for constructing Prolly Trees based on schema: : 160 Hours, 4 Weeks * 3
- Share knowledge with KEN Labs/ Julius on research papers and scientific details: 70h / 7 weeks
- Do a formal writeup of what was learned in researching the implementation: 80 Hours / 4 Weeks
- Documentation for spec (how trees are constructed) / explainer on algorithmic complexity: 40 hours 2 weeks
- Project management: 80h/ 10 weeks
    - Submit PR to ipld/ipld with spec and get reviews

Subtotal: 320 Hours, 8 Weeks * 3 + 190 Hours, 12 weeks + 80h, 10 weeks = 1230 hours, 12 weeks

ETA 2 months

### Milestone 2 - Golang implementation of Prolly Tree spec

Outputs: A high-level Golang library which implements an IPLD ADL based on the initial implementation along with unit tests and documentation on how to use the library. A set of benchmarks for the 

People working on this: 3

- Use the go-ipld-prime ADL and IPLD APIs for initial implementation: 160 Hours, 4 Weeks
- Unit tests for creating / updating / merging Prolly Trees: 120 Hours, 3 Weeks
- Add bencmarks for common operations: 40 Hours, 1 Weeks
- Documentation for using the library: 40 Hours, 1 Weeks
- Project management: 90h/ 10 weeks

Total: 360 Hours, 9 Weeks * 3 + 90h, 9 weeks = 1080 + 90 = 1170 hours, 9 weeks

ETA 2 months

### Milestone 3 - Golang IPLD indexer library

Outputs: A golang library for creating indexes from IPLD objects based on fields to index as well as an API for searching through said indexes. This will come with unit tests and documentation that describes how the indexes work and how to use the library.

People working on this: 4

- Library for indexing fields from an IPLD object into an prolly tree index: 120 Hours, 3 Weeks + 30h, 3 weeks from Mauve
- Research and choose query syntax (MongoDB style, SQL, other): 40 Hours, 1 Weeks, 10 Hours / 1 Weeks from Mauve
- Library for searching through the index: 120 Hours, 3 Weeks, 30 Hours, 3 weeks from Mauve
- Unit tests for creating / updating / merging indexes, benchmarks： 40 Hours, 1 Weeks, 10 hours, 1 week from Mauve
- Documentation for using the library: 40 Hours, 1 Weeks, 10 hours, 1 week from Mauve
- Project management: 80h/ 10 weeks

Total: 360 Hours, 8 Weeks * 3 + 80h, 8 weeks + 80h, 8 weeks = 1080 + 80 + 80 = 1240

ETA 2 months

### Milestone 4 - Example app to integrate with smart contracts

Outputs: An example app using smart contract with IPLD Prolly Tree Indexing

People working on this: 1

- build showcase component for filecoin lotus to make data stored on Filecoin（on-chain or off-chain）to be query-able: 160 Hours 4 Weeks
- build showcase smart contract to inteact with layer2 IPLD data store via IPLD prolly tree indexing: 160 Hours, 4 Weeks

Total: 320 Hours, 8 Weeks

Note: We may be implementing this milestone in parallel with Milestone 3

### Milestone 5 - Research needs in the (mostly web3) ecosystem

Outputs: A report that covers potential use cases as seen by different people from different positions and projects within the ecosystem.

People working on this: 1

- Survey people in ecosystem to ask about use cases (on-chain/offchain, inside/outside PL teams, talk to FVM folks): 30h, 2 weeks
- Prepare survey and reach out to stakeholders: 60h, 3 weeks
    - FIL on-chain and off-chain data storage
    - FVM integration
    - Developer needs from indexing and whether we can satisfy them
    - Would DAOs have uses for this?
    - Can this work with NFTs? 
- synthesize results of survey and interviews into a report: 30h, 3 weeks

Total: 120h, 8 weeks

### Milestone 6 - Research Applications and Feasibility

Outputs: Report describing the capabilities of prolly trees on a more abstract level, partially by covering the academic literature. It delves into the limitations with respect to ressources, alternatives and the value of potential applications.

People working on this: 1

- Overview over use cases and areas of application from academic literature: 20h, 1 week
- Discover alternative solutions (different primitive, different layer, different approach): 10h, 1 week
- General communication complexity, run time complexity -> limitations (per function): 50h, 3 weeks
- List of open issues in academic literature: 10h, 1 week
- Potential value for the IPFS-ecosystem: 30h, 2 weeks

Total: 120 Hours, 8 Weeks

## Total Budget Requested

<!--
Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.
-->

Hourly Rate = 65 USD/h

Milestone 1: 1230 Hours, 8 Weeks : 79950 USD
Milestone 2: 1170 Hours, 9 Weeks : 76050 USD
Milestone 3: 1240 Hours, 8 Weeks : 80600 USD
Milestone 4: 320  Hours, 8 Weeks : 20800 USD
Milestone 5: 120  Hours, 8 Weeks : 7800 USD
Milestone 6: 120  Hours, 8 Weeks : 7800 USD

Total : 4200 Hours, 49 Weeks : 273000 USD

## Maintenance and Upgrade Plans

<!--
Specify your team's long-term plans to maintain this software and upgrade it over time.
-->

We plan to build more software libraries and applications on top of this spec in the future which will ensure the codebase will be in use and will recieve periodic maintenance.

There are also plans for a JavaScript implementation of the spec shortly after this devgrant is completed.

# Team

## Team Members

- Taosheng Shi:15+ years of experience in distributed systems, former Principal Researcher of IPFSForce. Previous work experience mainly includes senior engineer of DXChain (Bay area), Cloud platform architect of Nokia (China), etc. Currently, He is a researcher and founder of KEN Labs (kencloud.com), dedicated to build trustless Cloud of Web3.
- William Yang:15+ years of experience in Internet development. He was an architect of Nokia's wireless and an senior engineer of AOL. He is currently the co-founder & CTO of KEN Labs(kencloud.com).
- ch3: Just aborted a computer science PhD and now wants to get into the IPFS ecosystem, looking for interesting research to be done.
- Mauve: Decentralzied Software consultant.

## Team Member LinkedIn Profiles

- Taosheng Shi:https://www.linkedin.com/in/taoshengshi/
- William Yang:https://www.linkedin.com/in/william-yang-40047910/
- ch3: - n/a
- Mauve: https://www.linkedin.com/in/mauve-s-47697579/

## Team Member GitHub Profiles

- Taosheng Shi:https://github.com/taoshengshi
- William Yang:https://github.com/sugarforever
- ch3: https://git.gnunet.org/gnunet.git/tree/src/rps (most published contributions can be found here)
- Mauve: https://github.com/RangerMauve

## Team Website

<!--
Please link to your team's website here (make sure it's `https`)
-->

[KEN Labs](https://kencloud.com/)
[Mauve Software Inc.](https://software.mauve.moe/)

## Relevant Experience

<!--
Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.
-->

- Taosheng Shi:
    - Worked on Filecoin-lotus as chief engineer
    - Working on IPLD database:Pando
    - Experience on large scale distributed system
    - Rust/Golang/etc experience
- William Yang:
    - Working on Pando side chain database
    - Rich Experience on Internet application development
    - JS/Golang/etc experience
- ch3:
    - Work on GNUnet  ([gnunet-rps](https://git.gnunet.org/gnunet.git/tree/src/rps))
    - MSc. in computer science/informatics (focus on networks and security, p2p)
    - C, python, rust, lua, Java, PolyML, ... (no js, no go)
- Mauve:
    - Working on p2p software (IPLD and otherwise) as a consultant
    - Built search indexes on top of P2P B+ trees
    - Experience scaling sharded/replicated NoSQL datbases like MongoDB
    - JS/Golang/etc experience

## Team code repositories

<!--
Please provide links to your team's prior code repos for similar or related projects.
-->

- [Pando database that uses IPLD data](https://github.com/kenlabs/pando)
- [Hyperbeedeebee: p2p indexed database](https://github.com/RangerMauve/hyperbeedeebee)

## Additional Information

<!--
Please include any additional information that you think would be useful in helping us to evaluate your proposal.
-->

We have potential users of the indexing system in the [WebRecorder](https://webrecorder.net/) community (another devgrant recipient) which is interested in using this spec to build searchable indexes of web archives hosted on IPFS.

KEN Labs is also working with groups that are building IPLD/Blockchain based applications which could make use of this indexing functionality.
