# Open Grant Proposal: `DeFi for Sustainable Supply Chains`

**Proposer:** [Evan Powlowsky](https://github.com/PowVT)

**Table of Contents**

- [Description](#project-description)
- [Value](#value)
- [Deliverables](#deliverables)
- [Milestones and Funding](#milestones-and-funding)
  - [Total Budget Requested](#total-budget-requested)
- [Maintenance and Future Plans](#maintenance-and-future-plans)
  - [Operations](#operations)
  - [Big Picture](#big-picture)
- [Team](#team)
  - [Team Members](#team-members)
- [Adaptive Website](#team-website)
- [Relevant Experience](#relevant-experience)
- [Code Repositories](#team-code-repositories)
- [Support and Funding](#support-and-funding)

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** YES

# Project Description

The global innovation economy depends on components made with critical minerals and metals such as tantalum, cobalt, and gold. Demand for these minerals is expected to rise rapidly over the coming years with expanded battery storage and renewable energy utilization. At the same time, it is common for the individuals who extract these resources, essential to humanity's clean energy future, to face poverty, poor labor conditions, and health and safety risks. The complexity of multi-tiered supply chains also makes it difficult for downstream brands (technology companies, battery manufacturers, jewelers etc.) to contribute to solutions in a meaningful manner.

Adaptive seeks to make supply chains more transparent and fair for producers. The Adaptive protocol is a framework of blockchain smart contracts that generate non-fungible ‘claim tokens’ representing an underlying physical asset. Tokens will be purchased and traded by downstream supply chain actors. Claim creators in this protocol must meet specific responsible sourcing guidelines for onboarding. Claim creators will be rewarded for meeting these standards, creating claim tokens, and using the application.

As a claim token is sold and transferred downstream through the supply chain, the producers of the claim and associated civil society actors - known as “Beneficiaries” - will be compensated for participation in the Claim Application. This can be used to finance mine site improvements, increase worker pay, and drive the adoption of “due diligence” practices that make improvements across the value chain. The beneficiaries along with the physical properties of the asset are recorded in the claim token and stored immutably on the blockchain.

When a claim is purchased on the Adaptive Marketplace, the beneficiaries recorded in the claim token itself are credited with a percentage of the sale proceeds. Upon completion of a claim token sale, the seller of a claim receives a percentage of the claim token’s value. The remaining profit will be divided between Beneficiaries recorded in the claim. The beneficiaries can withdraw their individual proceeds from downstream token sales at any time.

## Value

Currently, the target users of the application largely rely on paper based certificate systems that do not store data in a decentralized and transparent manner. We hope to pioneer the usage of IPFS for supply chain traceability and provide a secure way to store all claim data. Adaptive seeks to expose responsible sourcing stakeholders to the distributed web through IPFS.

We plan to develop tooling around IPFS which makes it easier for auditors on our platform to view important claim information and validate claims. This will take form as a javascript implementation and finalize in a npm package called ‘ipfs-claims’.

Additionally, Adaptive relies on IPFS to pin and retrieve claim documents to/from the network. Adaptive wants to increase its IPFS node swarm with grant funding to decrease reliance on central providers like Pinata and Infura. Further strengthening the IPFS Filecoin ecosystem.

Due to the unique nature of this claim system it is important we have measures in place to train users on setting up their digital wallets and interacting with the application. The more beneficiaries attracted to the platform, the larger the claims ecosystem will become.

## Deliverables

1). ipfs-claims: A npm package of components that we will use to parse IPFS claims data. These tools will help standardize claim forms and help our partners audit the claims.

2). Claims-dashboard: In addition to our current app a set of react components will be built for the tracking of claims after creation. The dashboard will include features like the number of token transfers, IPFS data, the claim creator, auditing history and more. For efficiency, Adaptive will run and maintain multiple IPFS daemons pinning the data created in the app.

3). Beneficiary-dashboard: A set of react components for tracking beneficiary payouts. Similar to the claims dashboard but focusing on the claims payouts, number of payouts, total payout, and all IPFS data for the beneficiary. For both dashboards IPFS data will be fetched through the ipfs-js library.

4). Pilot Test Report: A scientific report detailing the outcome of the pilot implementation. Specifically, how the claims tooling and overall app performed when being used in production. IPFS claims will be generated by the users during the pilot and a report will detail their experience. The report will help Adaptive Resources market IPFS claims and shine a light on using IPFS in this manner.

## Milestones and Funding

Work for milestones will begin on December 1st, 2021

The Adaptive team seeks to pilot the application at selected mine site (gold) and associated supply chain as soon as feasible. During this pilot period development of the application will be ongoing concurrently.

| Milestone | Description                                                                             | Hrs | Cost |
| --------- | --------------------------------------------------------------------------------------- | --- | ---- |
| 1         | npm package for verifying claims data on IPFS                                           | 60  | 4500 |
| 2         | CLI tools for testing npm package and auditing claims                                   | 15  | 1125 |
| 3         | Front end claims dashboard to improve user experience                                   | 30  | 2250 |
| 4         | Beneficiaries dashboard for UX and marketing                                            | 30  | 2250 |
| 5         | Automated testing scripts for dashboards using hardhat.js + IPFS local test environment | 30  | 2250 |
| 6         | Scientific report on IPFS implementation, claims creation, and auditing                 | 15  | 1125 |

### Total Budget Requested

- **Total Funding Amount:** $13,500

## Maintenance and Future Plans

### Operations

The smart contracts are currently deployed and upgradable. There should be little maintenance on the contracts themselves for they have been under development for close to 8 months. Adaptive will be focused on a successful pilot implementation and completing our milestones.

### Big Picture

Adaptive seeks to develop partnerships with private sector companies, industry associations, certification programs, and auditing bodies that will benefit from the Adaptive Claim system. As stakeholders in the region and internationally learn about the positive impact, we hope to rapidly grow the claims system network. Additionally, we will seek additional grant funding and support from development agencies and foundations who seek to drive due diligence and responsible sourcing through supply chains.

## Team

### Team Members

- Software Development - [Evan Powlowsky](https://github.com/PowVT)
- Advisors - Jonathan Ellermann, Dave Snow

## Team Website

Website: [Adaptive Resources](https://adaptiveresources.io)

## Relevant Experience

Evan, the lead engineer, has been working on this project since April 2021, developing the smart contract architecture and front end for the project.

The team has extensive experience in responsible minerals and renewable energy. The team has been involved in supporting ASM sourcing guidance for the gold and 3T industry, including managing teams in Uganda and Rwanda in the responsible sourcing field.

## Team Code Repositories

[Smart Contracts](https://github.com/PowVT/adaptive-smart-contracts)

## Support and Funding

This grant is privately funded.
