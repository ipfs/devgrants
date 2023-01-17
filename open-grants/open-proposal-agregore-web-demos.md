---
name: Agregore P2P Web Tutorials
about: Teaching how to make p2p web apps by example
title: 'Agregore P2P Web Tutorials'
labels: Open Grant
assignees:

---

# Open Grant Proposal: `Agregore P2P Web Tutorials`

**Name of Project:** Agregore P2P Web Tutorials

**Proposal Category:** Choose one of `integration-adoption`

**Proposer:** @RangerMauve

**(Optional) Technical Sponsor:** @autonome

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT, APACHE2, or GPL licenses?:** YES

# Project Description

<!-- Please describe exactly what you are planning to build. Make sure to include the following: -->
<!-- - Start with the need or problem you are trying to solve with this project. -->
<!-- - Describe why your solution is going to adequately solve this problem. -->

<!-- This section should be 2-3 paragraphs long. -->

Peer to peer protocols like IPFS have been gaining traction on the web, and fully p2p distributed apps are now possible in web browsers like Agregore which work along local-first software principles to give users agency and developers ease of distribution.
However, due to the novel nature of the p2p web, information how to actually build apps is hard to find, and there are many unknowns on what can and cannot work well in this setting. As a result there is also a lack of fully p2p web apps available for users to experiment with.

We aim to address these issues by doing a series of small p2p web app tutorials where we will be developing small apps, creating tutorials for others to follow along, and doing retrospectives to identify pain points that we discovered during the process.

Our goal is to use web application primitives such as HTML/CSS/JavaScript without any extra build tooling or frameworks needed other than a peer to peer web browser like Agregore. With this we aim to reduce the barrier to entry for creating new peer to peer apps and enable more people to make use of the technology for their own needs.

## Value

<!-- Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions: -->
<!-- - What are the benefits to getting this right? -->
<!-- - What are the risks if you don't get it right? -->
<!-- - What are the risks that will make executing on this project difficult? -->

<!-- This section should be 1-3 paragraphs long. -->

The challenges to advancing a nascent technology include enhancing education, encouraging adoption, and demonstrating value. Our main exercise will be to create apps that people can use, but our primary deliverables will be tutorials and retrospectives; we're hoping to go through the exercise that dweb creators may go through in learning what we can do with the protocols and technologies available, and document the process as we go along, uncovering the same issues along the way that newcomers might run into.

We've structured this process into multiple rounds of work and checkpoints to reconvene. By having retrospectives we can understand where we may have gotten stuck, lost, or unable to accomplish what we wanted to, and what immediate/further work may be needed throughout the underlying tech stacks. We'll publish our findings in order to share these challenges with the larger community. We've timeboxed the milestones as well, in order to provide a look into what multiple developers of different experience levels and development paths can get done with the tech available.

## Deliverables

<!-- Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished. -->

We will do an initial two week sprint of scoping out what is and isn't possible to do, as well as putting together templates on how one can follow creating tutorials/webapps/retrospectives. During this time we will also have a person working on putting together documentation for the IPFS protocol handlers that others may use to copy example code into their apps during development.

Then, we will do 3 sprints of having several developers working on small p2p web apps in parallel, writing tutorials for how others can make those web apps, and doing retrospectives on what we learned and future work that could be done on said apps.

## Development Roadmap

<!-- Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section). -->

<!-- For each milestone, please describe: -->
<!-- - The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables. -->
<!-- - How many people will be working on each milestone and their roles -->
<!-- - The amount of funding required for each milestone -->
<!-- - How much time this milestone will take to achieve (using real dates) -->

Development will be broken down into two week milestones, with the first milestone being devoted to laying the groundwork for the following 5 milestones which will consist of one week of planning and development of simple web apps, and another week of writing tutorials and doing retrospectives.

The goal is to work from the start of November 2022 to the end of January 2023.

### Milestone 1 - Scoping + Initial Documentation

The goal of this milestone is to scope out the process for the next milestones, as well as some initial work on documentation which will enable people to ramp up more quickly.

Weeks: 2

- Mauve: 5 h / week = 10 h
	- Coordinate meetings
	- Plan potential patterns that can and cannot be used
	- Scope which apps we could work on
- Caprice: 25 h / week = 50h
	- Write initial docs for IPFS fetch protocol handlers
	- Add copy paste-able examples for common operations
- Ankeet: 10 h / week = 20h
	- Create and document process for following sprints
	- Plan potential patterns that can and cannot be used
	- Scope which apps we could work on
- Judy: 10 h / week = 20h
	- Create and document process for following sprints
	- Plan potential patterns that can and cannot be used
	- Scope which apps we could work on
- Dirk: 10 h / week = 20h
	- Create and document process for following sprints
	- Plan potential patterns that can and cannot be used
	- Scope which apps we could work on

Total: 5 people = 120 hours

Outputs:
- Document outlining process to take to scope out apps, how tutorials should be structured, and how retrospectives on the process should be written up / acted upon.
- Documentation on the Agregore website describing the protocol handler APIs
- Basic copy-paste-able examples on the Agregore website for common use cases
- Blog post on the Agregore blog announcing the plans and process.

### Milestone 2 - Initial apps

This will be the first milestone where we will develop three apps and tutorials in parallel.
The main goal is to test the process and iterate on it as well as fill out important formation for the retrospectives.
We are purposefully timeboxing development time so that potential dead ends will be captured and will be used to inform the retrospective.

Weeks: 3

- Mauve: 5 h / week = 15 h
	- Coordinate meetings
	- Fix issues with p2p protocols
- Caprice: 25 h / week = 75h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Ankeet: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Judy: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Dirk: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective

Total: 5 people = 180 h

Outputs:
- 0-4 p2p web apps published on the Agregore website
- 0-4 tutorials guiding people to create the web apps themselves
- 4 retrospectives on pain points and strengths that were found during the development of apps as well as suggestions for improvements + future work on top.
- Blog post summarizing milestone efforts

### Milestone 3 - More apps

This milestone will be similar to to the previous one with three apps being developed in parallel.
Milestone 2's retrospectives will be used to inform the process on this round.
Similarly, the main goal is to create more retrospectives along with tutorials.

Weeks: 3

- Mauve: 5 h / week = 15 h
	- Coordinate meetings
	- Fix issues with p2p protocols
- Caprice: 25 h / week = 75h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Ankeet: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Judy: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective

Total: 4 people = 150 h

Outputs:
- 0-3 p2p web apps published on the Agregore website
- 0-3 tutorials guiding people to create the web apps themselves
- 3 retrospectives on pain points and strengths that were found during the development of apps as well as suggestions for improvements + future work on top.
- Blog post summarizing milestone efforts

### Milestone 4 - Final apps

This final round of apps will follow what was learned in previous milestones.
Again, the main goal is to create more retrospectives along with tutorials.

Weeks: 3

- Mauve: 5 h / week = 15 h
	- Coordinate meetings
	- Fix issues with p2p protocols
- Caprice: 25 h / week = 75h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Ankeet: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Judy: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective
- Dirk: 10 h / week = 30h
	- Create a p2p web application from the options scoped in milestone 1
	- Create a tutorial for creating the web application
	- Write up retrospective

Total: 5 people = 180 h

Outputs:
- 0-4 p2p web apps published on the Agregore website
- 0-4 tutorials guiding people to create the web apps themselves
- 4 retrospectives on pain points and strengths that were found during the development of apps as well as suggestions for improvements + future work on top.
- Blog post on summary of retrospectives / what was accomplished over the whole timeline

## Total Budget Requested

<!--Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds. -->

Rate: 80 USD/h

- Milestone 1: 120 hours * 80 = $ YY
- Milestone 2: 180 hours * 80 = $ YY
- Milestone 3: 150 hours * 80 = $ YY
- Milestone 4: 180 hours * 80 = $ YY

Total: 630 hours * 80 = $ 50400

## Maintenance and Upgrade Plans

<!-- Specify your team's long-term plans to maintain this software and upgrade it over time. -->

We plan to use this as a kickoff to create more focused workshops and training materials for using p2p web tech and to partner with existing communities to spread digital and p2p web literacy.

We will also be updating the created tutorials and docs when changes to the protocol handlers are made.

Longer term this fits in with Agregore's larger effort of making local-first p2p web applications accessible to people and to enable community networks use cases in the face of legacy infrastructural limittions.

# Team

## Team Members

<!-- - Team Member 1 -->
<!-- - Team Member 2 -->
<!-- - Team Member 3 -->
<!-- - ... -->

- Ankeet: @sudocurse - Development / Writing
- Dirk: https://github.com/dirkcuys/ - Development / Writing
- Caprice: @capriceesmas - Development / Writing
- Judy: @judytuna - Development / Writing
- Mauve: @RangerMauve - Coordination

## Team Member LinkedIn Profiles

<!-- - Team Member 1 LinkedIn profile -->
<!-- - Team Member 2 LinkedIn profile -->
<!-- - Team Member 3 LinkedIn profile -->
<!-- - ... -->

- Ankeet: https://www.linkedin.com/in/ankeetpresswala/
- Dirk: https://www.linkedin.com/in/dirk-uys-4273578/
- Caprice
- Judy: https://www.linkedin.com/in/judytuna/
- Mauve: https://www.linkedin.com/in/mauve-s-47697579/

## Team Website

<!-- Please link to your team's website here (make sure it's `https`) -->

## Relevant Experience

<!-- Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc. -->

- Ankeet: Breaking things for decades and making things on good days
- Dirk: Web developer working in edu tech. Built IPFS based markdown blog for previous grant. Other work in online education with www.p2pu.org
- Caprice: Computer Science student at Carleton University. Has experience in teaching digital skills.
- Judy: Web developer and organizer. 
- Mauve: Consulting on p2p web tech for years. Built Agregore, working with PL on IPFS protocol handlers. Ran several workshops on creating p2p web apps. Successfully coordinated several PL/FIL devgrants to completion.

## Team code repositories

<!-- Please provide links to your team's prior code repos for similar or related projects. -->

- Agregore Browser: https://github.com/AgregoreWeb/agregore-browser/
- Example workshop on making a p2p web app: https://blog.mauve.moe/slides/making-a-text-editor/README.md

# Additional Information
<!-- How did you learn about the Open Grants Program? -->
<!-- Please provide the best email address for discussing the grant agreement and general next steps. -->
<!-- Please include any additional information that you think would be useful in helping us to evaluate your proposal. -->

We have applied to and successfully completed several open grants in the past.

The primary contact email to use is contact@mauve.moe
