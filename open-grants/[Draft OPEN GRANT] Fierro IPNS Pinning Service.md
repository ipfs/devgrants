# Open Grant Proposal: `IPNS Pinning Service`

**Name of Project:** Fierro

**Proposal Category:** `app-dev`

**Proposer:** `mrodriguez3313`

**(Optional) Technical Sponsor:** `If you have previously discussed this project with a member of the IPFS or Filecoin project teams and they have agreed to be a technical sponsor, include their name and/or github handle here`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Please respond with either "Yes" or "No"

`Yes`

# Project Description

<!-- Please describe exactly what you are planning to build. Make sure to include the following: -->
<!-- - Start with the need or problem you are trying to solve with this project. -->

Fierro is a web API implemented in Go that enables developers to create, publish, re-publish, and track IPNS records. If someone wants to publish a website on IPFS they will have to direct users to the specific Content Identifier (CID) where they can download the site. If the Original Poster (OP) makes any changes to that site, they will get a completely different CID that they need to redirect their users to. The same goes to the problem of dynamic NFTs, if they wish to change a CID in a smart contract, that is a costly operation in more ways than one. IPNS solves this problem by offering one easy to read CID that can be updated. The records have to be republished by their expiration date to maintain discoverability and security. But it is not always possible for the OP to be online to republish the record. The problem today with IPNS is the revival of IPNS records, discovery time, and library support.

**Currently, there is no way to "pin" IPNS records. IPNS pinning is more of an umbrella term because the idea is that a user wants their content to be available when they go offline**. This means either they want to authorize someone else to republish the content or they want to have a remote node simply track the latest version. Lastly. it is not possible to create IPNS records through the js-ipfs implementation (the browser or node.js) and that is why this project is important. 

Fierro will let a client request keys and publish IPNS records over the web. This way, it can enable dapp development from the browser as well as not needing to run their own ipfs node. They will also be able to hand over control to the API say if they no longer want to maintain their own records and data. These features will enable republishing records, track records to maintain up-to-date content on our node, and enable users to operate IPNS completely without operating their own IPFS node. This is something many users have asked for, for example: [discuss.ipfs.io/ipns-use-cases-what-is-dragging-down-ipns](https://discuss.ipfs.io/t/ipns-use-cases-what-is-dragging-down-ipns/9817). Adin from Protocol Labs has even wrote a synopsis on the topic [here](https://pl-strflt.notion.site/IPNS-Overview-and-FAQ-071b9b14f12045ea842a7d51cfb47dff).

<!-- This section should be 2-3 paragraphs long. -->

## Value

<!-- Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions: -->
<!-- - What are the benefits to getting this right? -->
<!-- - What are the risks if you don't get it right? -->
<!-- - What are the risks that will make executing on this project difficult? -->

>While something like [pinata](https://www.pinata.cloud/) can pin IPFS hashes, there [apparently ](https://discuss.ipfs.io/t/is-there-any-website-provide-ipns-service/9721) is no service that can “pin” IPNS records.
[quote="pmorch, post:1, topic:13424" site="discuss.ipfs.io"](https://discuss.ipfs.io/t/ipns-beyond-the-basics-no-ipns-pinning-service-any-docs-on-this/13424)

IPNS is an underutilized library of IPFS. Not only would this project bring more awareness to the library and IPFS as a whole. Getting this right would give the community their first option for storing IPNS Records remotely. No other service is currently allowing IPNS record tracking or republishing. These features would enable all kinds of applications and if anyone wanted to also host their own IPNS publishing nodes for faster retrieval. They would be able to spin up their own server from this project repo. Not only that, but it would create discourse in feature requests for the protocol upstream. Currently, many issues have to be worked around, regarding IPNS, with a project like this and others. Getting this right would allow myself and team members to focus on and help out with core protocol problems. 

Not getting this right would at least measure real world demand for a project or service like this. This could open up avenues for other companies or devs to leapfrog off of or learn from. In my opinion, there is demand for a service like this and it would let down a huge audience. I have faith in my own abilities as a developer and learner. What I don't know, I can find someone or somewhere to ask. Lack of team members, financial resources, and time, so to capitalize on momentum, are also risks that may affect the project's success. In the end, this project will be sucessful in bringing in more people to the IPFS community and generating more data on the network.

<!-- This section should be 1-3 paragraphs long. -->

## Deliverables

<!-- Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished. -->

The final deliverable for this project will be a web API that is being hosted in the cloud. The product will consit of these features: 

- keystore operands: 
   - key generation 
   - key import and export 
- Adding a file to IPFS network 
- Publishing records to IPNS
- Viewing published IPNS records 
- Record tracking
- Record republishing

- Documentation:
   - OpenAPI specs
   - Docs website complete with examples

## Development Roadmap

<!-- Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section). -->

<!-- For each milestone, please describe: -->
<!-- - The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables. -->
<!-- - How many people will be working on each milestone and their roles -->
<!-- - The amount of funding required for each milestone -->
<!-- - How much time this milestone will take to achieve (using real dates) -->

1. Documentation
   a. Docs site generated from github docs
   b. Open API Spec sheet
   c. Examples:
    - Curl request examples 
    - Use case examples
    - Launch own node
 
Marco Rodriguez, Lead Engineer will be working on milestone 1. This will be a 3 week long milestone. With a budget of $4,000.

2. Finish development on API
   a. Implement API keys
   b. Security:
     - secure key transmission between client and server
     - input validation
     - key encryption
    c. Marketing push and announcements

Marco Rodriguez, Lead Engineer will be working on milestone 2. This will be a 8 week long milestone. With a budget of $10,000.

3. Deploy & testing 
   a. Deploy on cloud service
      - Cloud service security things
   b. Test endpoints 
     - unit testing
     - stress tests
   c. Debugging as needed

Marco Rodriguez, Lead Engineer will be working on milestone 3. This will be a 3 week long milestone. With a budget of $8,000.

4. Beta
   a. Open beta to >100 users
   b. Debugging and Maintaining
   c. Documentation

Marco Rodriguez, Lead Engineer will be working on milestone 4. This will be a 8 week long milestone. With a budget of $28,000.

## Total Budget Requested

<!--Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds. -->

$50,000
Breakdown:
Milestone 1: living costs & expenses, development
Milestone 2: living costs & expenses, development, learning materials, and human resources
Milestone 3: living costs & expenses, development, learning materials, human resources, and server costs
Milestone 4: living costs & expenses, development, human resources, and server costs

## Maintenance and Upgrade Plans

<!-- Specify your team's long-term plans to maintain this software and upgrade it over time. -->

The goal is to get feedback and data from the beta phase and use that to be able to create an paid option for the API. With profits from the API, we will develop the security and features of the project. Ultimately, I would the new information gained to help in contributing to the IPNS protocol.

# Team

## Team Members

Marco Rodriguez-Salinas

## Team Member LinkedIn Profiles

https://www.linkedin.com/in/marco-a-rod/

## Team Website

https://www.fierro.io/

## Relevant Experience

<!-- Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc. -->

I am the right person to lead this project, because I have spent the last 4-5 months involving myself in the community everyday and finding out what the people want in an IPNS pinning service. Even if I don't participate in every conversation, I am reading the comments of every user wanting IPNS support. Since I have been the one to tackle the problem, I need to see it through. I am an adept learner and socialize well. Since graduating college two years ago, my passion for distributed/decentralized systems has grown and led me to participate and win prizes in many hackathons, participate in a web3 fellowship to develop my first project on IPFS, and meet many amazing people around the world. I am a recipient of the next-steps microgrant, I have been working on this project Jan-March. The project is at the mvp stage and after milestones 1 and 2 it will be beta ready.

## Team code repositories

https://github.com/mrodriguez3313

# Additional Information

<!-- Please include any additional information that you think would be useful in helping us to evaluate your proposal. -->
