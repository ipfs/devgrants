# Open Grant Proposal: `Crystalizer`

**Name of Project:** Crystalizer

**Proposer:** `hhff`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:**

Yes, although we'd like to offer a paid plan to help us support infrastructure costs and provide ongoing maintenance, ie - something like how Sentry works. Given this is a CI style tool, we'd likely offer "parallelization" as a payment option (ie, paying for a "dedicated build queue" rather than waiting for the public queue).

# Project Description

#### Problem: 
Deploying and hosting static files with IPFS is not "beginner friendly" (in our humble opinion!). Developers need to understand a bunch of terminology (like "pinning", etc), and why they (probably) need pay for a pinning service, or spin up their own IPFS node. In addition, managing IPNS or DNSLink along with a DNS provider is confusing for folks who are new to regular DNS in the first place. 

#### Solution: 
A CI style Github integrated pipeline that automates this complexity for the developer. This service would:
- Allow the developer to connect their Github account/org(s), and select project(s) for auto-deploys to IPFS 
- Allow the developer to elect one or more git branches in a project as "pinned" (ie, integration, production, dev)
- Whenever a "pinned" git branch is updated, static assets would be built from the codebase, deployed, and pinned to an IPFS hash
- Allow the developer to debug build logs by surfacing them in a UI
- List all known "IPFS hashes" mapped to previous deploys in the UI
- Automatically manage IPNS/DNSLink on behalf of those pinned branches
- Allow for immediate "rollback" to a previous IPFS hash via IPNS/DNSLink via the UI
- Send a webhooks to another service on successful deploy

## Prior Art

We originally built [https://www.crystalizer.io](https://www.crystalizer.io/) as a way to preview PRs before they are merged, but we were beaten to market by [https://featurepeek.com](https://featurepeek.com/), which is ultimately a better product. As such, we already have in place:
- [ ] A fully integrated CI pipeline working against Github oAuth, written in Ruby on Rails
- [ ] A buildstep & background job queue for building and deploying static assets against multiple frontend frameworks on the fly (in docker containers via Kubernetes)
- [ ] A brand guideline, UI styles, and implemented component library for neat UI (screenshots below)

Changes we'd need to make to repurpose as a zero config IPFS deploy tool:
- [ ] Update all Design, Marketing & Documentation for IPFS concepts
- [ ] Redesign & reimplement build and deployment against IPFS
- [ ] Add IPNS/DNSLink management layer (for automatic + manual rollbacks)
- [ ] Under-the-hood move to using `Now.sh`'s open source builders ([Apache 2.0](https://github.com/zeit/now/blob/master/LICENSE)) to support [all of the frameworks listed here](https://github.com/zeit/now/blob/master/packages/frameworks/frameworks.json) with zero config (currently we use our own logic here)

## Value

In recent years, the JAM (Javascript, APIs, Markup) Stack has become a really popular way of thinking about web apps and deployments. Services like Netlify & Now.sh have popularized these methodologies by adding a bunch of utility around this style of building and hosting. The JAM Stack is taught readily at developer bootcamps, and as such, is something new developers usually lean in to.

In addition, we've already written the core of the user facing app in Ruby on Rails, lowering the bar to external contributors to participate in improving the product.

### What are the benefits to getting this right?
We lower the bar (friction, person time, etc) to using IPFS as a viable deploy target for a really big and diverse group of developers (juniors, and everyone) - thereby increasing IPFS adoption! In addition, we'd simplify the concept of "rollback" deploys to these same developers, as permanent, immutable IPFS deployments are ideal for such a concept.

### What are the risks if you don't get it right?
The main risk is that Netlify & Now.sh add IPFS as a hosting target in response to seeing how we do that (given our code would be open source). This doesn't strike me as likely, but who knows...!

However, in a lot of ways that would mean Crystalizer fulfills it's primary goal: increasing adoption of IPFS.

### What are the risks that will make executing on this project difficult?
The main risk here is that when I last used IPNS, it was quite slow to resolve (upwards of 30 seconds). I understand that DNSLink is a faster way to achieve a similar thing. 

In a worst case scenario, we could run an nginx proxy or Cloudfront Lambda function to improve usability by handling DNS routing to specific IPFS hashes on the fly.

A secondary risk is user acquisition - we are not experts in product promotion. The success of this software is dependent on people actually using it! More volume means more paying customers, and more paying customers means we can afford to dedicate time to maintenance.

## Deliverables / Milestones

#### Redesign & Implement Marketing Page
- 3pts Rewrite content narrative
- 3pts Repurpose existing graphics
- 3pts Design new graphics and animations

~ 1 week of 1 designer's time

Deliverable: New designs for the Marketing homepage

#### Redesign & Implement UI for IPFS (& IPNS/DNSLink) concepts
- 5pts Redesign UI for for IPFS concepts
- 3pts Update ORM Schema to support IPFS hashes and such
- 5pts Update Projects#Index with IPFS details
- 5pts Update Projects#Build with IPFS details

~ 2 days of 1 designer's time
~ 1.5 weeks of a frontend developers time

Deliverable: New designs & a working UI repurposed to work with IPFS hosting concepts

#### Implement Integration Hooks
- 3pts Implement Slack Integration
- 5pts Implement Sending External Webhook on Deploy Completion

~ 1 week of a backend developer's time

Deliverable: The ability to connect a Slack channel to notify users of new deployments, and the ability to post webhooks on this same event, for the sake of breaking caches and triggering other such services.

#### Move to Now.sh Build Step, IPFS Deployment & DNS Management
- 13pts Update Tooling & Build step to use Now.sh CLI
- 13pts Update Tooling & Deploy step to push to IPFS
- 8pts Handle Rollbacks and DNS Management (IPNS/DNSLink)

~ 3 weeks of a backend developer's time

Deliverable: The core technology. A zero-config, framework agnostic buildstep that deploys static assets to a unique IPFS hash, and optionally manages DNS routing, etc.

#### Test, QA and Launch
- 30% of total points

~ team effort, hopefully including the grant committee!

Deliverable: A ready-to-launch web application for users to connect their Github account, and start shipping static assets to IPFS!

## Total Budget Requested

If you'd like to read more about how we quote technology, we've detailed it [here](https://medium.com/sanctuary-computer-inc/how-we-quote-technology-2b0f8e9b627f).

**Please Note:** The numbers here are indicative of "cost" to employ developers here in NYC (with health insurance, payroll taxes, etc). These numbers do not have a profit margin built in: we are fans of the IPFS ecosystem, and would love to be able to afford the time to build something great on top of it!

#### Estimated Cost
69 points * 1.3 (QA & Testing) / 13.5 (our burndown) = 6.6 person weeks

6.6 person weeks * $2800 (average cost to employ a person in NYC per week)
= `$18,480`

#### Estimated Timeline
I plan to work on this (personally) roughly 2.5 days per week. Given the major timeline here is development (design timeline is short and can happen parallel). 

As such, we'd expect a launchable application to be ready roughly 12 weeks from grant approval.

## Maintenance and Upgrade Plans

We'll be using it internally (free hosting for a client is huge!) so we'll ensure it's always in working order as a necessity.

However, we would like to grow this product into a profitable offering for hosting static assets. We'd love to eventually offer some additional services like free SSL via LetsEncrypt, on the fly serverside rendering, and perhaps some CDN integrations. In order to be able to do this work, we'd first need a profit generating product so that we can afford to commit development time to it.

# Team

## Team Members

#### Developers:
- [Hugh Francis](https://github.com/hhff)
- [Joshie Fishbein](https://github.com/joshiefishbein)
- [Christine Kim](https://github.com/chrismekim)
- [Alicia Willett](https://github.com/aliciakw)
- [Harrison Wideman](https://github.com/hwideman)
- [Sebastian Odell](https://github.com/sepowitz)
- [Ellis Marte](https://github.com/ellismarte)
- [Sohee Lim](https://github.com/limsohee1002)
- [Kay Mok](https://github.com/mokaymokay)
- [Conor Davidson](https://github.com/conordavidson)

#### Designers:
- [Brendon Avalos](https://www.brendonavalos.com/)
- [Devin Halladay](https://devinhalladay.com/)
- [Darin Buzon](https://www.darinbuzon.info/)

#### Strategy & Operations:
- [Isabel Munter](https://www.linkedin.com/in/isabelmunter/)
- [Tim Casasola](http://www.timcasasola.com/)

## Team Website

[https://www.sanctuary.computer](https://www.sanctuary.computer)

## Relevant Experience

Our team works with the JAM Stack quite often, for client projects! We're very familiar with CI tools (we use CircleCI a lot, and I've used Travis in my open source work). We currently use CircleCI w/ Docker to build and push to S3, so we're familiar with the quirks of getting single page apps up and serving traffic.

In addition, we're experts in Rails, Docker, Kubernetes, and the like. The software stack we're working with here is a known quantity, through and through.

## Team code repositories

We're a product studio, so most of our client work is private, however we do open source a lot of things [here](https://github.com/sanctuarycomputer/studio), including non-code stuff like financials.

# Additional Information

#### Screenshots of [Existing Product](https://www.crystalizer.io)

![image](https://user-images.githubusercontent.com/2865404/72011616-3eafa300-3228-11ea-8be0-619a277783c0.png)
![image](https://user-images.githubusercontent.com/2865404/72011650-4d965580-3228-11ea-9794-7c1475fd1bee.png)
![image](https://user-images.githubusercontent.com/2865404/72011713-6acb2400-3228-11ea-8e58-0c69c00d7bc4.png)
![image](https://user-images.githubusercontent.com/2865404/72011745-7ae30380-3228-11ea-881d-8cb363a499ab.png)
![image](https://user-images.githubusercontent.com/2865404/72011782-8c2c1000-3228-11ea-96cf-ccdaf6f3fff1.png)
