# Open Grant Proposal: `Distributed Pinning Protocol`

**Name of Project:** Photon

**Proposer:** `@zuriel-photon`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

IPFS is a perfect architecture for the distributed file system, where community members contribute disk capacities. The Web2 companies are beginning to move to Web3, and we can foresee that the demand for distributed data storage will grow to Web2 levels. It will be a significant challenge for IPFS to meet the demand by relying on voluntary contributions. We propose a protocol design to incentivise individuals/groups to run IPFS nodes by providing monetary rewards for their direct contributions.

Our project, Photon, creates a distributed storage marketplace by introducing an incentive layer for IPFS nodes. Storage providers are rewarded for executing data pinning tasks. The rewards are dynamically adjusted based on demands and contributions. As the storage demand grows over time, the network will scale accordingly.

Technically, Photon is a blockchain with dedicated smart contracts to ensure IPFS nodes pinning data is within the contracted period. This proposal only provides a typical workflow within the protocol. More technical detail can be found in our white paper to be published shortly.

Data Owner:
1. Upload the data content to the IPFS network and obtain the CID.
2. Create a signed smart contract including CID, storage period, fee, and upload to the IPFS.
3. Pending contract gets countersigned and committed to the Photon chain by Pinning Node.
4. If data cannot be retrieved on the IPFS, initiate a dispute in the Photon chain.

Pinning Node:
1. Regularly scan the IPFS network and obtain storage contracts of interest.
2. For each contract, download the content by CID and start pinning the contracted data.
3. Countersign the contract, and submit it to the Photon chain.
4. If the data owner initiates a dispute, submit the proof of retrievability to the Photon chain.
5. If a contract is being executed faithfully, reward accumulates accordingly.

## Value

### What are the benefits of getting this right?
1. Create a distributed pinning service, helping IPFS aggregate network capacity.
2. Encourage enterprise/individuals to run stable IPFS nodes 24/7.
3. Avoid centralised pinning service provider’s control of the entry point of IPFS.

### What are the risks if you dont get it right?
The protocol is built above the IPFS, so it will not affect the IPFS network even if the project fails. The only risk it might have is if the protocol becomes successful. Unpinned data can get flushed out quickly from IPFS because all the nodes prefer to pin data with incentives.

### What are the risks that will make executing this project difficult?
We have finished the feasibility verification and have an internal prototype running. The chain can suffer performance degradation if the stored data size grows to zettabyte-level. At that point, scaling solutions such as sharding or zero-knowledge proof can be considered and implemented accordingly.

## Deliverables

The project will be delivered in two phases.
1. Stable Photon protocol with integrated IPFS nodes allows users to use the command-line tool to exercise workflow of the process, including post pinning contact, countersign contract, initiate a dispute, and proofs retrievability.
2. Interactive UX: provide users with a smooth experience pinning data in IPFS. An easy setup bot allows any IPFS node to join the distribution pinning protocol and enjoy pinning to earn.

## Development Roadmap


| Milestone | People | Funding | Period |
| :------: | :------: | :------: |  :------: |
| Deliverables#1 | 5 | $15000 | 10.02.2022 - 18.09.2022 |
| Deliverables#2 | 5 | $15000 | 20.09.2022 - 23.11.2022 |


## Total Budget Requested

We requested $30,000 to accomplish the two milestones. All the budget will be exchanged to the FIL, and use these FILs to stimulate the IPFS community to test the product and assist us with testing and reach the final stable version.

## Maintenance and Upgrade Plans

1. Use sharding or zk-proof to solve the performance issue.
2. Create a cross-chain bridge that supports FIL, ETH, and BTC. Allow using different assets to pay the pinning service fee.
3. Add bandwidth incentive for IPFS nodes to cache the hot data.

# Team

## Team Members

The project is open source, but the team wishes to keep some level of anonymity.

- @zuriel-photon
    - Joined the Bitcoin community in 2012.
    - Served as a CTO for a blockchain company for four years.

- @maxkaneco
    - PhD in CS, ex-Facebook core engineer.
    - Built a mining pool service that can dynamically allocate computation between mining and AI training.

## Team Website
- http://photon.storage/

## Relevant Experience
Except for two co-founders, we have three blockchain engineers with 3+ years of experience. The team has deep expertise in the blockchain, wallet, explorer, mining pool, and Defi. We began researching the Web3 storage field in May 2021 and started coding Photon in Feb 2022

## Team code repositories
- The code is still in active development since Feb 2022. We will be [open source](https://github.com/photon-storage) in September.

## Additional Information
1. For the proof of retrievability, implement the famous paper in Golang: H. Shacham and B. Waters. Compact proofs of retrievability.
2. For the consensus layer, we forked Prysm’s Ethereum beacon chain and refactored nearly 50% of the codebase to fit Photon’s need. An internal running version is established.