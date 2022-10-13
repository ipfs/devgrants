# Open Grant Proposal: `IPNS Pinning Service`

**Name of Project:** Fierro

**Proposal Category:** `app-dev`

**Proposer:** `mrodriguez3313`

**(Optional) Technical Sponsor:** @lidel

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Please respond with either "Yes" or "No"

`Yes`

# Project Description 💬

<!-- Please describe exactly what you are planning to build. Make sure to include the following: -->
<!-- - Start with the need or problem you are trying to solve with this project. -->

Fierro is a web API implemented in Go that enables developers to create, publish, re-publish, and track IPNS records. Adin from Protocol Labs wrote a synopsis on the on the status of IPNS here: [IPNS Overview & FAQ - Notion](https://pl-strflt.notion.site/IPNS-Overview-and-FAQ-071b9b14f12045ea842a7d51cfb47dff). In this synopsis, he clearly states the problems to address, with the intent to create community dialogue, to bring wider adoption of IPNS. Adin concisely shows the main problems with IPNS are: slow resolution times of records, JS support (without delegating work to a go node outside the browser), third party republishing, & "safe" vs "old" content (reffering to content retrieved after a record has expired). Fierro would solve many problems including: resolution time, browser support, and third party republishing. As a central api, users would be able to publish to our node with their own key or one provided to them. This will allow users to resolve the content much faster as well as allow third party republishing. As an API, inputs and outputs can be operated by most languages, thus allowing support for js in browser and most backend lanugages. Fierro's main purpose will be to enable devs to make use of the IPNS library through the API, but also allow users to publish content directly through the site.

### Why an IPNS Pinning Service ? 💁
**Currently, there is no way to "pin" IPNS records. IPNS pinning is more of an umbrella term because the idea is that a user wants their content to be available when they go offline**. This means either they want to authorize someone else to republish the content or they want to have a remote node simply track the latest version (as explained by Jorropo in this [discuss.ipfs.io thread | ipns-beyond-the-basics-no-ipns-pinning-service-any-docs-on-this](https://discuss.ipfs.io/t/ipns-beyond-the-basics-no-ipns-pinning-service-any-docs-on-this/13424/2)). In this thread, Jorropo and others offer reasons why there has yet to be an IPNS pinning service. The reasons include a variety of problems with the library including: multiple nodes publishing to the same record causing nonce collisions and any user to potentially recieve incorrect content (if two nodes have the same private key, a problem caused by sharing a key) and horrible propagation time on a single local node.

To create the first third party IPNS Pinning service, IPNS record following and third party republishing are critical. This will allow current users of IPFS to pin their mutable content like websites, dapps, dynamic NFTs, software, et cetera to an easily find-able place. Making it quicker to retreive others' content. Of course, if some content gets popular enough, then going through the service wouldn't be needed as the record would be easily discoverable.

To enable user development, Fierro will let a client request keys from a go-ipfs node and publish IPNS records through the node with those keys. Current users of IPFS will also be able to hand over control of their records; say they have to go offline for extended period of time or simply don't want to maintain their node anymore. 

Implementing these features will enable third party republishing of records, follow/track records to maintain up-to-date content on our node, and enable users to operate IPNS completely without operating their own IPFS node. This is something many users have asked for, for example: [discuss.ipfs.io/ipns-use-cases-what-is-dragging-down-ipns](https://discuss.ipfs.io/t/ipns-use-cases-what-is-dragging-down-ipns/9817). The most simple reason why people haven't made an IPNS pinning service seems to be that it would be just too big an inconvience to create. But Fierro is already at the MVP stage.

## Value :scroll:

<!-- Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions: -->
<!-- - What are the benefits to getting this right? -->
<!-- - What are the risks if you don't get it right? -->
<!-- - What are the risks that will make executing on this project difficult? -->

>While something like [pinata](https://www.pinata.cloud/) can pin IPFS hashes, there [apparently](https://discuss.ipfs.io/t/is-there-any-website-provide-ipns-service/9721) is no service that can “pin” IPNS records.
[quote="pmorch, post:1, topic:13424" site="discuss.ipfs.io"](https://discuss.ipfs.io/t/ipns-beyond-the-basics-no-ipns-pinning-service-any-docs-on-this/13424)

IPNS uses a nodes' public key to create a static address that can point to different IPFS Content Identifiers (CIDs). Consider this situation, a user wanting to take advantage of what IPFS has to offer, but they don't want to own their a node because they (the Original Publisher (OP)) know it will not always be possible to be online. Now, if they want to publish a website on IPFS they will have to direct users to the specific CID where they can download the site. If the OP makes any changes to that site, they will get a completely different CID. And now their prior CID is out-of-date, thus necessitating the need to tell their users of the new CID. 

The same goes with the problem of dynamic NFTs, if they wish to change a CID in a smart contract, that is a costly operation in more ways than one. With IPNS, the OP can publish their images and corresponding metadata to individual IPNS records, and simply update the CID when they want to change the image or metadata content. This could be based on certain contidions in contract or dependent on some other creator constructs. **With Fierro, they could publish and keep their content alive all in one place.**

IPNS is an underutilized library of IPFS. Not only would this project bring more awareness to the library and IPFS as a whole. Getting this right would give the community their first option for storing IPNS Records remotely. No other service is currently allowing IPNS record tracking or republishing. These features would enable all kinds of applications and if anyone wanted to also host their own IPNS publishing nodes for faster retrieval. They would be able to spin up their own server from this project repo. Not only that, but it would create discourse in feature requests for the protocol upstream. Currently, many issues have to be worked around, regarding IPNS, with a project like this and others. Getting this right would allow myself and team members to focus on and help out with core protocol problems. 

The biggest roadblock will be addressing the shared keys problems (nonce collisions, security of shared private keys, medium of sharing keys) and "safe" vs "old" problem. There are certain situations where retrieving the "old" content of an expired record would be the best solution. While in others, it would be safer to not get anything back. For example in software, where a logic bug is a prevalent risk.

Sharing keys is not a problem, there is functionality in go-ipfs to permit that; there are ways to share keys without others knowing what they are. The problem arises when you are permitted to publish on behalf of others. It can lead to a multitude of attacks. The problem we can avoid in Fierro is the security risk of transmission of keys and permissions to use those keys. With the introduction of User Controlled Authorization Networks (UCANs) pioneered by Fission, we have a web3 authentication method of permitting another entity to access secret data that we own. Consider this scenario, a user wants to transfer to us the ability to republish their record on their behalf. They would have to share with us their private key and with that (theoretically) comes unrestricted access to publish at any time for however long we want. But with UCANs, the user is in control of their shared key still and can revoke the service's access to it at any time. This is a plan we have in mind for a subsequent deliverable.

## Deliverables :envelope:

<!-- Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished. -->

The final deliverable for this project will be a web API that is being hosted in the cloud. The product will consit of these features: 

Backend - Basic API service that works better and more secure than current mvp:
   - Viewing published IPNS records
   - Record tracking
   - All following upgraded pinning service specification

Frontend - to interact with records pinned with a GUI:
   - Sign up for API
   - Form to view records tracked on Fierro

Documentation - to give support in video and text format to developers:
   - add IPNS support to current [IPFS pinning service specs](https://ipfs.github.io/pinning-services-api-spec/) 
   - extended IPNS API to create a custom docs for extended features Fierro API supports
   - Docs website complete with examples

## Development Roadmap :world_map:

<!-- Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section). -->

<!-- For each milestone, please describe: -->
<!-- - The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables. -->
<!-- - How many people will be working on each milestone and their roles -->
<!-- - The amount of funding required for each milestone -->
<!-- - How much time this milestone will take to achieve (using real dates) -->
### Phase 1 - A thousand words and a picture

1. Documentation
   * Docs site generated from github docs
   * Add on IPNS pinning documentation to existing [pinning specifications](https://ipfs.github.io/pinning-services-api-spec/)
   * Extend above pinning service api spec with endpoints Fierro offers
   * Examples:
       * Video and written docs on how to publish content to IPNS through Fierro using Curl examples
       * "     " using frontend
       * Docs on how to get your own node up and running
       * All in one page for resources on IPNS

Marco Rodriguez, Lead Engineer will be working on Phase 1 milestone 1. This will be a 2 month long milestone.

2. Implement API spec in Fierro
   * Pin and PinStatus objects
   * Error responses
   * Fix all endpoints to work with changes
   * Testing code
      
Marco Rodriguez, Lead Engineer will be working on Phase 1 milestone 2. This will be a 3 month long milestone.

### Phase 2 -  A web2 story
1. Front end
   * Follow and stop following page
   * Login page 
   * Design and implementation
   
Marco Rodriguez, Lead Engineer will be working on Phase 2 milestone 1. This will be a 2 month long milestone.

2. Finish development on API
   * Implement API keys
   * Security:
       * client and server
       * input validation
   * Marketing push and announcements
   * Medium posts, other blog posts, twitter spaces, 
   
Marco Rodriguez, Lead Engineer will be working on Phase 2 milestone 2. This will be a 3 month long milestone.

3. QA testing & Deploy
   * Deploy on cloud service
      - Cloud service security permissions
   * Test endpoints
     - unit testing
     - stress tests
   * Debugging
   
Marco Rodriguez, Lead Engineer will be working on Phase 2 milestone 3. This will be a 2 month long milestone with server costs. With a budget of $7,000.

4. Beta
   * Open beta to 100 users
   * Customer feedback & debugging loop
   * Documentation
   
Marco Rodriguez, Lead Engineer will be working on Phase 2 milestone 4. This will be a 2 month long milestone with server costs.

## Total Budget Requested

<!--Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds. -->

Total= $7,000 for server costs

Breakdown:
* Api spec: living costs & expenses
* Implementation: living costs & expenses
* Front-end: living costs & expenses, development
* Documentation: ":point_up:", and learning materials
* API Development: ":point_up:", and human resources
* QA Testing & Deployment: ":point_up:", and server costs
* Beta: living costs & expenses, development, human resources, and server costs

## Maintenance and Upgrade Plans

<!-- Specify your team's long-term plans to maintain this software and upgrade it over time. -->
### Phase 3 - :rocket: to web3 (Future work, in no specific order, out of scope of grant)

1. UCANs
   * Gain a deeper understanding of UCANs
   * Get a users private key from go node to UCAN jwt
   * Permit Fierro access to key from UCAN
   * Document process for users to follow
   * test publishing with UCAN
2. Ground up
   * Strip off web2 security and authentication
   * Login & identify a user by their UCAN and which records they can manipulate on remote node
   * Create new endpoints to support same functions so to not break anything. OR rework endpoints to support both
3. Support both API implementations
   * Roll in support for UCANs to service
   * Add UCAN education and documentation to site
   * unit & stress test new system
4. Tackle native trustless solutions for go-ipfs
   * Research and collaborate with community and core developers
   
The goal for the deliverable is to get feedback and data from the beta phase and use that to be able to create a paid option for the API. The goal for future plans is to address user's worry of sharing private keys explicitly. Ultimately, I would use the new information gained to help in contributing to the IPNS protocol. 

# Team

## Team Members

Marco Rodriguez-Salinas

## Team Member LinkedIn Profiles

https://www.linkedin.com/in/marco-a-rod/

## Team Website

https://www.fierro.io/

## Relevant Experience

<!-- Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc. -->

I have spent the last 4-5 months involving myself in the community everyday and finding out what the people want in an IPNS pinning service. Even if I don't participate in every conversation, I am reading the comments of every user wanting IPNS support. I am a recipient of the next-steps microgrant, I have been working on this project Jan-March. The project is at the mvp stage and after milestone 3 it will be beta ready. Since I have been the one to tackle the problem, I need to see it through. I am an adept learner and socialize well. Since graduating college two years ago, my passion for distributed/decentralized systems has grown and led me to participate and win prizes in many hackathons, participate in a web3 fellowship to develop my first project on IPFS, and meet many amazing people around the world. I worked with the Fission team to contribute to the redirects project for go-ipfs. The task was to follow Netlify's redirects spec, thus allowing gateways on IPFS to not error out on page refreshes.

## Team code repositories

https://github.com/mrodriguez3313

# Additional Information
I have applied for LLC status in California as Fierro-Labs, LLC. And I created a youtube channel to post my first video which you can find here: [How to publish a website with Fierro](https://youtu.be/LN4dXO6sYe4).
