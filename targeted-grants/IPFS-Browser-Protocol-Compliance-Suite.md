# Targeted Grant: IPFS Browser Protocol Compliance Suite


**Issuer:** @lidel
**Recipient:** @RangerMauve

## Project Description

<!-- Please fill in details about what you're trying to build. What is the purpose/context? What are the high-level requirements?

This section should be 2-3 paragraphs long. -->

**This project’s goal is to figure out what browser features require IPFS addressing support and to create a comprehensible test page that browser vendors can verify support through.**

IPFS Companion browser extension has been making progress on getting IPFS support into web browsers.

However, the definition of "support" is still ambiguous and it would be good to give browser vendors a definitive test suite to ensure they have compatibility with each other.

There already exist [some tests for IPFS protocol handler](https://ipfs.github.io/in-web-browsers/ipfs-protocol-handler-support-tests.html), but they are not extensive and have gaps such as iframes, different types of XHR requests, and JS modules. Part of this work will be to find the gaps and update the tests to cover everything that's needed for modern web development.

## Value

<!-- Please describe why the work that will come out of this Targeted Grant is valuable for the IPFS ecosystem. -->

There are some features of the protocol that we would like browsers to support which cannot currently be supported using the `registerProtocolHandler` API on the web or via IPFS Companion. 

Defining the needed functionality and expected behaviors will help browser vendors to standardize and implement the needed APIs, and reduce the friction between `https://` and `ipfs://` `ipns://` websites and dapps. A comprehensible test suite will make it easier for browser vendor engineers to guarantee that they are implementing protocol support accurately and that we have compatibility between different browsers.

IPFS team will use the same test suite to prototype new behaviors internally, namely we want to use it for exploring the concept of Writable Gateways being mapped to URI schemes.

## Deliverables

<!-- What are you expecting the proposer to deliver at the completion of this project?-->

- Description of protocol handler functions needed from browser vendors (iframe, script tag, image, etc) (20 hours)
- Extend [Protocol Handler Support Tests](https://ipfs.github.io/in-web-browsers/ipfs-protocol-handler-support-tests.html) to contain tests for all the needed features and make it easy to run them in a way that produces a shareable "compliance report" (40)
- Create additional set of Protocol Handler Support Tests for handling POST/PUT/DELETE messages for `ipfs://` and `ipns://` (for internal use by IPFS team - could be a commented out section, or a separate instance) (20)
- Show the tests as passing in an experimental dweb browser as a proof of concept that could be presented to browser vendors in addition to the dry spec and tests (20)

## Team

<!-- List the skills and experience you are looking for. Teams with this background might be a better fit for this project.-->

- [@RangerMauve](https://github.com/RangerMauve) - (Grant recipient) Active member of the dweb community.
   Done a grant with Protocol Labs before.
   Done multiple grants with DAT and are key member in team that set up the DAT Foundation.

- @lidel - (Protocol Labs) Technical advisor

## Detailed Requirements & Constraints
<!-- You can use this section to detail requirements that the deliverables must include.

Also include any relevant constraints that the implementer should be aware of before beginning this project.-->

Description: This description should ennumerate all the ways that a browser might load data from IPFS in a markdown document. As well, there will be research done to see how other browser compliance tests are presented so that it can inform the test design. This document will be used to make the test

Tests: This will be an HTML document which will contain individual "tests" which will either pass or fail. The tests will be checking the browser's ability to interact with `ipfs://` URLs according to the spec in Milestone 1. Once the tests have run, there will be a summary of the browser's compliance. These tests will be uploaded to IPFS and pinned on a pinning service in addition to being abailable in a GitHub repository.

POST/PUT: This will be a second HTML document which will use the same format for tests and complaince as in Milestone 2, but it will focus on the ability to use `POST`/`PUT`/`DELETE` methods which are currently not strongly defined. This will also be uploaded to a GitHub repository and pinned on IPFS.

Passing in Experimental Browser: This will consist on patches to the Agregore browser which has support for `IPFS` via Electron's protocol handler API. The patches will bring Agregore to the point of complying with the test scenarios so that other browser vendors can see an example of passing compliance.

## Milestones & Funding

**Total Funding Amount:**  $6500 <!-- List the total proposed funding amount (currently in USD, eventually can be a distribution between USD/FIL)-->

**Milestones:** (working 10-20 hours a week)<!-- Make sure that the values in the Funding column add up to the Total Funding Amount listed above.-->

| Milestone No. | Milestone Description | Funding | Estimated Timeframe |
| --- | --- | --- | --- |
| 1 | Research/Description | $1300 | ~20h  |
| 2 | Test Page with Compliance Report | $2600 | ~40h  |
| 3 | Second page with POST/PUT | $1300 | ~20h  |
| 4 | Passing coplinace in experimental browser | $1300 | ~20h  |

## Acceptance Criteria

<!-- What are the acceptance criteria for each milestone and for the final deliverables? These should be as objective as possible. They will be used to determine whether or not a grantee will receive payment for work completed for a milestone. -->

TODO

## Resources

<!-- Link any resources that might be helpful for an implementer who is working on this project.-->

https://ipfs.github.io/in-web-browsers/ipfs-protocol-handler-support-tests.html
https://github.com/olizilla/dweb.link/issues/7

## Support and Funding

<!-- Who is backing this project? How will they pay the implementers? If you have not already added your information to [FUNDING](../FUNDING.md), you can do so now and link it here. Include a legal entity name if possible.

Any other organizations that choose to add their support to this Targeted Grant will do so in this section.
-->

This grant is funded by Protocol Labs.  
Technical guidance will be provided by @lidel.
