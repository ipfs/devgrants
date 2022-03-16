# Open Grant Proposal: `Emergent Reputation`

**Name of Project:** Emergent Reputation

**Proposer:** `@ckartik`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

## Problem Statment
**Cyberspace** can abstractly be seen as a means of infomation distribution.
In a general sense, most applications can be broken down to two key objects: 
**Users & Content**. The focus of current network infrastructure (layers below Application on OSI the Model)
 has been **content**, ensuring the content is _Authenticated (Certificates), Available,
and holds Integirty (Hashes)_. However, it failed to provide any similar cryptographic provisions for the **Users** 
creating & consuming this content leading internet engineers to overload this into the Application Layer.
The provisions relevant to Users are _Reputation & Trust_. Because of these being held at application layer, 
monoplistic organizations _(Twitter, Meta)_ have gained **intitutionalized control** over these attributes without governance.

The **monoplistic** nature of these organizations has lead them to create suboptimal solutions to _Reputation & Trust_ for users.
The instablility this creates leaves significant slack left for leveraging the Internet as large-scale social coordination system.
This RFC presents a solution to this problem through the development of a **distributed graph data-structure** that mimics
single-degree trust relationships held in the physical world for each user. This would help emerge a larger a web-of-trust that is highly composable
at the application layer of traditional applications. Through the development of IPLD as a basis for distributing a decentralized data-structure
such as the social graph, and the proliferation of wallets & blockchains as a mechanism for providing signing capabilities to browsers, this 
is the first time that a viable solution that could be adopted with low friction has ever been possible.

There are three key components to the imlementation of the solution, for which a working POC has been enabled on testnet.
1. The **edges** of the graph will be stored on IPLD, we will call these attestations.
2. The **nodes** will be as a keys to a map stored on a Smart Contract, and will be drived from the wallet account number.
3. An **engine** will be provided in the library to provide the following functionality:
    - Addition of nodes & attestations
    - Revocation of attestations
    - Graph algorithims for driving proxy determinations of trust (Shortest Path, K-connectedness, etc)
    - If possible, we would also like to conduct research into mechanisms for zero knowledge transfer of trust information.

## Value

Please describe in more detail why this proposal is valuable for the IPFS ecosystem. Answer the following questions:
- What are the benefits to getting this right?
    - Will breed broader adoption for IPFS in most systems, as this idea is 
    useful as a foundational technology for a variety of technologies.
- What are the risks if you don't get it right?
- What are the risks that will make executing on this project difficult?

This section should be 1-3 paragraphs long.

## Deliverables

Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.

## Development Roadmap

Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).

For each milestone, please describe:
- The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.
- How many people will be working on each milestone and their roles
- The amount of funding required for each milestone
- How much time this milestone will take to achieve (using real dates)

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

Please include any additional information that you think would be useful in helping us to evaluate your proposal.
