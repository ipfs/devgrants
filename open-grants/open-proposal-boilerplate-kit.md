# Open Grant Proposal: `Create open, modular and extendable boilerplate kit from go-ipfs monolith`

**Name of Project:*IPFS as a service system boilerplate kit*

**Proposer:** `mar1n3r0`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:*Yes*
# Project Description

Please describe exactly what you are planning to build. Make sure to include the following:
- Start with the need or problem you are trying to solve with this project.
- Describe why your solution is going to adequately solve this problem.

As a monolith go-ipfs is hard to extend in order to cover new use cases without affecting its core functionality.
My proposal is to abstract it to microservices running on local cluster and based on a well maintained modern boilerplate kit such as: https://github.com/vardius/go-api-boilerplate
This would allow anyone to fork the kit and extend it by writing custom microservices, add integrations, and use multiple interoperable projects from the ecosystem.

## Value

Please describe in more detail why this proposal is valuable for the IPFS ecosystem. Answer the following questions:
- What are the benefits to getting this right?
It would allow IPFS to be used as an extendable service system boilerplate kit. A typical use case for this is self-contained wasm apps which do not have access to host resources directly.
- What are the risks if you don't get it right?
There are no risks since it is meant to be a separate project.
- What are the risks that will make executing on this project difficult?
It will require additional maintenance since the go-ipfs monolith will be logically split into microservices by domains.

## Deliverables

It would be well decoupled and defined as per the boilerplate kit I am proposing to be used:
https://github.com/vardius/go-api-boilerplate

## Development Roadmap

Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).
- Split go-ipfs into logical domains such as: unixfs, dagservice, blockservice, abstract blockstore and datastore as repositories, bitswap and a libp2p integration.  

For each milestone, please describe:
- The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.
A complete local cluster that can be up and running with a single command
- How many people will be working on each milestone and their roles
Ideally me full time for a year with the help of 3-4 core developers who know the ins and outs of the system.
- The amount of funding required for each milestone
Hard to estimate about 100k
- How much time this milestone will take to achieve (using real dates)
Hard to estimate around 12 months

## Total Budget Requested

Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.
100 000 usd
## Maintenance and Upgrade Plans

Specify your team's long-term plans to maintain this software and upgrade it over time.
This would be impossible to maintain in the long-term without a dedicated internal team
# Team
1
## Team Members

- Team Member 1 [https://github.com/mar1n3r0]

## Team Website

Please link to your team's website here (make sure it's `https`)

## Relevant Experience

Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.
A senior software engineer with entrepreneurial spirit, product mindset and 10 years of commercial experience. An open sorcerer who leverages community knowledge through kits and boilerplate rather than reinventing the wheel. Specialized in startups, iGaming, platforms, fintech and blockchain. Roles I have been involved with include: developer, scrum master, devops, solutions architect, cto. 
## Team code repositories

Please provide links to your team's prior code repos for similar or related projects.
https://github.com/mar1n3r0
# Additional Information

Please include any additional information that you think would be useful in helping us to evaluate your proposal.
