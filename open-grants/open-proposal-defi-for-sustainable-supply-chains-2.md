# Open Grant Proposal: `DeFi for Sustainable Supply Chains 2`

**Proposer:** [Evan Powlowsky](https://github.com/AdaptiveResources)

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

Adaptive seeks to make supply chains more transparent and fair for the upstream producers. The Adaptive protocol is a framework of blockchain smart contracts that generate non-fungible ‘claim tokens’ representing an underlying physical asset. Tokens will be purchased and traded by downstream supply chain actors. Claim creators in this protocol must meet specific responsible sourcing guidelines for onboarding. Claim creators using the Adaptive protocol will be rewarded for meeting these standards, creating claim tokens, and using the application.

As a claim token is sold and transferred downstream through the supply chain, the producers of the claim and associated civil society actors - known as “Beneficiaries” - will be compensated for participation in the Claim Application. This can be used to finance mine site improvements, increase worker pay, and drive the adoption of “due diligence” practices that make improvements across the value chain. The beneficiaries along with the physical properties of the asset are recorded in the claim token and stored immutably on the blockchain.

When a claim is purchased on the Adaptive Marketplace, the beneficiaries recorded in the claim token itself are credited with a percentage of the sale proceeds. Upon completion of a claim token sale, the seller of a claim receives a percentage of the claim token’s value. The remaining profit will be divided between Beneficiaries recorded in the claim. Beneficiary accounts tied to a claim token’s ‘metadata’ can withdraw their individual proceeds at any time.


## Value

Adaptive has created an approach to store Claim information in a decentralized and transparent manner. This allows supply chain data to be shared and transferred from one tier of the supply chain to the next.  Adaptive’s first Filecoin foundation grant allowed us to build tooling for auditing Adaptive claim tokens through an external package. Additionally, we created multiple dashboards for tracking the claim token lifecycles and various parameters related to beneficiary pay-outs. These were major steps in moving our platform through the alpha development phase into the beta stage. Our next set of work focuses on necessary UI/UX improvements and usability testing, to ensure the product is ready for pilot testing. A major UX improvement includes developing a crypto to fiat off-ramp for our users.  In addition, we will automate our Know Your Customer (KYC) process to onboard potential users into the application, as unique user types. Our process will follow United States and international requirements around know your customer, vendor, and counterparty regulations. 

Further updates anticipated during this grant include the development of a “corrective action plan” as part of our risk management tools. The corrective action plan component will be connected to risk reporting tools, so that claim token buyers are provided the status updates around the risk treatment areas detailed in claim tokens. The data generated using corrective action plans are crucial in measuring the success of the risk treatment interventions and measuring the protocol's impact on the users of the application. We will also expand our interactive map component, which has been placed on the landing page of the application. The risk map shows different production locations supported and risks identified in those locations. The map will provide users with additional insights into areas where claim token revenue can be mostly valuably directed.


## Deliverables

1). Adaptive Risk Map: A web app feature built using MapBox components will be expanded. The map will overlay production areas with risk data from 3rd party providers and Adaptive risk assessment data. Risk data will be used to further refine focus areas for Adaptive Claims.  

2). User Types and KYC Onboarding for New Users: Establish official know your customer (KYC) procedure and standards for onboarding users to the Adaptive platform along all tiers of the supply chain. This includes the development of an automated form to collect required KYC information from users store non-sensitive information in a cloud database. We will ensure the architechure is aligned with payment processing standards requiremented by banking and financial services partners. We will explore the benefits and need of partnering with a Compliance as a Service (CaaS) provider.

3). Corrective Action Plan for Risk Management:  As part of the Adaptive platform, we will develop a “Corrective Action Plan” feature that is integrated with our Beneficiary Risk Reporting features. As beneficiaries report on their progress the information will automatically flow into the corrective action plan, providing claim token buyers with up to date status of risks for specific claim tokens they have purchased. 

4). Traceability Tool and Data Carrier Development: The Adaptive Trace tool will be developed in a manner that allows users to maintain an “identity preserved” chain of custody from mining location to point of export. This includes the development of a mobile scanning tool and a secure/sealable shipping package with Adaptive QR Code. Exporters using Adaptive will be asked to scan QR stickers, using the Adaptive application, during the Claim Creation process. 


## Milestones and Funding

Work for milestones will begin on July 1st, 2022

| Milestone | Description                                                                             | Hrs | Cost |
| --------- | --------------------------------------------------------------------------------------- | --- | ---- |
| 1         | “Adaptive Risk Map” expansion showing various risk indicators in a primary set of mining locations. Includes cost of 3rd party data sets. | 30  | 3000 |
| 2         | User Types and the Design and build a KYC onboarding process for new users of the application. | 90  | 9000 |
| 3         | Corrective Action Plan                                                                  | 45  | 4500 |
| 4         | Traceability Tool Integration with Data Carrier                                         | 60  | 6000 |

### Total Budget Requested

- **Total Funding Amount:** $22,500

## Maintenance and Future Plans

### Operations

The smart contracts are currently deployed and upgradable. There should be little maintenance on the contracts themselves. Adaptive will be focused on preparing for pilot implementation, user onboarding, and completing our milestones.

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

-[Smart Contracts](https://github.com/PowVT/adaptive-smart-contracts) (solidity files)
-[ipfs-claims](https://github.com/AdaptiveResources/ipfs-claims) (npm package)

## Support and Funding

Previously supported by funding [grant](https://github.com/ipfs/devgrants/pull/120) accepted by Filecoin.
