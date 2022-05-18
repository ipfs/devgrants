# Open Grant Proposal: `OpenRegistry x IPFS`

**Name of Project:** OpenRegistry

**Proposer:** Jasdeep Singh - [Github - jay-dee7](https://github.com/jay-dee7) on behalf of OpenRegistry

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes
We are already building under Apache2.0 License

# Project Description

OpenRegistry is a decentralised container registry fully compliant with OCI Distribution Specification. The specification provides similar capabilities as that of the Docker Registry HTTP API V2 protocol and more.

For the longest time Docker has run DockerHub (their hosted container registry) and it’s been the most popular platform by far. Majority of the people rely on Docker’s Container Registry, even in the WEB3 world where every component must be decentralised and the need for centralised platform should be as little as possible.
Here are a few reasons why **THIS** project comes to life:
- Docker Hub is run by a corporate, who’s biggest (but not only) goal is to make profit.
- When DockerHub goes down, it causes a lot of service degradation for it’s peers, we can show the tech industry how resilient and robust OpenRegistry can be, with the support of decentralised and Web3 native protocols like IPFS.
- `DockerHub’s new Rate Limiting` makes if even harder to use DockerHub. (We’ve worked with Fortune500 Clients in the past and we were literally forced to use AWS’ Container Registry). When you're building continuously and your deployment process is frequent, the rate limiting can really be a pain in the neck.
- With OpenRegistry, we want to establish a trust factor among tech communities that it doesn't have to be centralised to build a powerful product like DockerHub.
- Run by the Open Cloud, powered by Open Technologies. We’re planning to add IPFS support soon after the initial launch.

Currently, OpenRegistry is being built on top of Skynet for the storage backend but the OCI Distribution Spec defines the backend to be pluggable simply by satisfying the `storage.StorageDriver` backend. Now that our MVP is ready, we'd like to add IPFS storage backend to make OpenRegistry more flexible to the demanding world of technologies.

### Usage

**Q.** How difficult it would be to use this OpenRegistry as our Container Registry of choice?
**Answer:** OpenRegistry is fully compliant with The OCI Distribution Spec, and we've received the Certification from the Open Containers Initiative Organisation as well, check it out on the [Official OCI Conformance Website](https://conformance.opencontainers.org/). This means that your existing workflow would remain exactly how it is.

## Value

Containers are the building blocks of modern infrastructure and distributing them efficiently is a critical part of deploying applications (even more so, at scale). 

We believe that a Container Registry is one of the best use cases for a decentralised storage system like IPFS. OpenRegistry with IPFS has potential to be used by millions of developers everyday, which would roughly translate to Terrabytes of data being transferred daily. This makes it a perfect collaboration/opportunity to highlight the scalability and resiliency of the IPFS Network.

Developers can use OpenRegistry to share their private code-bases, secrets, and other sensitive information while still being in full control of all the data they share. Knowing it all is protected, and being distributed reliably with a transparent system of decentralised storage, all without the involvement of any centralised entitiy.

**- What are the benefits to getting this right?**
If OpenRegistry is a success (which we're gonna make sure it is), Web3 will have it's own Container Registry, fully compliant with OCI Distribution Conformance Spec, which literally means you can do anything that you would do on DockerHub,GHCR,etc. Owned and operated completely by the Open Source Web3 Communities.

**- What are the risks if you don't get it right?**
We hope we never come to this but however if in some alternate reality this does happen, we'll always be listening to our users and the communities we participate in and try to rectify any issues or obstacles that might be in the way OpenRegistry vision.

**- What are the risks that will make executing on this project difficult?**
The biggest risk so far is that we do not have enough funds to run and manage OpenRegistry. Along with that, we also want to hire another engineer to work with us. We want to start incentivizing developers that build OpenRegistry so that they don't have to think about full-time job or contracting somewhere to make ends meet.
We want to pursue this dream aggressively

## Deliverables

1. OCI Distribution Specification comliant backend and get the certification from them.
2. Web interface with search autocompletion, GitHub OAuth2.0 support, and 3 blogs.
3. Collaboration with IPFS and Filebase. WebAuthN, Vulnerability scanning for container images, PASTEO and SPIFEE based access management.

## Development Roadmap

### Milestone 1 - Q4 2021

> After successful completion of this **Milestone**, a user should be able to: Push, Pull, Search and Manage their container images on OpenRegistry. Any container engines (like nerdctl or docker cli) should also be able to use HTTP Basic and JWT Authentication. A basic form of Web Interface will also be ready to use. In addition to this, We should have received Certification from Open Containers Initiative Organization for implementing Distribution Spec.

|OCI Disttribution Spec Implementation|AuthN & AuthZ|APIs, Web Interface, & Integration|
|----|----|---|
|✅ Push Container Images|✅ Implement Registry Spec Compliant Authentication Protocol|✅ Catalog API for Listing Container Images|
|✅ Push Container Manifests|✅ Server Side Network and bandwidth Optimization|✅ System Wide Logging|
|✅ Pull Contianer Images |✅ Migrate KV Store to PostgreSQL|✅ List Tags API|
|✅ Pull Container Image Manifests|✅ JWT Support|✅ Basic Web Interface|
|✅ Content Discovery & Management|✅ HTTPS - Basic Authentication|✅ Release Closed Beta Program|
|✅ OCI Conformance Ceritification|||

**Engineers Working on this:** Gunjan Valecha & Jasdeep Singh <br>
**Funding Requested: $30k USD**

### Milestone 2 - Q1 2022

> After successful completion of this **Milestone**, we'll have a brand new designs implemented. A state-of-the-art Web Interface will be released along with personalised blog posts, Login With Github, Autocompletion for searching container images and an Uptime status page to monitor OpenRegistry's uptime.

|Web App Development|Workflows & Developer Experience|New Release and the way forward|
|----------|--------|----------|
|✅ Design Logo & Web Interface |✅ Logs & Metrics collection \w FluentBit and Grafana|◻︎ Cut a new release|
|✅ New Home Page for OpenRegistry|✅ Uptime Status Page|✅ Integrate Email Service with OpenRegistry|
|✅ OpenRegistry Dashboard View|✅ OAuth2.0 /w GitHub|✅ Enable Sign In & Sign up on Web Interface|
|✅ Settings & Profile Page|✅ New Blogs about OpenRegistry & collaborations|◻︎ Load & Performance Testing|
|✅ Search With Autocomplete|✅ Documentations|◻︎ Collect Feedback|

**Engineers Working on this:** Gunjan Valecha & Jasdeep Singh <br>
**Funding Requested: $30k USD**

### Milestone 3 - Q2 2022

> Upon successful completion of this **Milestone**, OpenRegistry will have multiple storage backends, thorough collaborations with IPFS and Filebase. These backends will be configurable by the end user. We'll also build an OpenSource TUS Protocol Client Library, which helps with uploading large files efficiently to servers that support TUS. We're looking forward to bring WebAuthN to OpenRegistry as it will eliminate any need to collect PII. Along with this, we're also expecting Vulnerability scanning, Bring your own encryption keys and more.

|Web3 integrations|New Features & Enhancements|Ecosystem Building|
|------|--------|-------|
|◻︎ TUS Protocol Client Implementation|◻︎ Vulnerability Scanning for Container Images|◻︎ SPIFEE based resource access|
|◻︎ Collaborate with IPFS|◻︎ WebAuthN - Passwordless Access|◻︎ Run Freemium for 2022|
|◻︎ Collaboration With Filebase|◻︎ Bring your own Skynet Key (BYOSK)|◻︎ Contribute back to Skynet, IPFS, and Akash Network|

**Engineers Working on this:** Gunjan Valecha & Jasdeep Singh <br>
**Funding Requested: $30k USD**

### Milestone 4 - Q3 2022

|OpenRegistry Core|Enhancements|Web App|
|------|------|---------|
|◻︎ Organization Mode|◻︎ gRPC APIs for OCI Distribution Spec APIs|◻︎ Cut a new release|
|◻︎ Container Image Analytics|◻︎ Platform Agnostic Security Tokens (PASETO)|◻︎ Design Origin Illustrations|
|◻︎ Private & Encrypted Container Images|◻︎ OCI Distrbution Spec Extensions support|◻︎ Animations for Web App and Blob|
|◻︎ P2P Container Image Distribution|||

**Engineers Working on this:** Gunjan Valecha & Jasdeep Singh <br>
**Funding Requested: $30k USD**

## Total Budget Requested

Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.

| Milestone   | Developer Hours | Total |
|-------------|-----------------|-------|
| Milestone 1 | 420 | $30,000 USD |
| Milestone 2 | 500 | $30,000 USD |
| Milestone 3 | 500 | $30,000 USD |
| Milestone 4 | 420 | $30,000 USD |
| **Total**   | **1840** |**$120,000 USD** |

## Maintenance and Upgrade Plans

We've already laid out our plan for next 2 quarters but it doesn't end there. We want to build a complete ecosystem around OpenRegistry and add a bunch of complimentry features and products. We're currently running a Open Beta Program to join and check OpenRegistry out.

We're soon to release OpenRegistry for Public use and once OpenRegistry is stable enough, We'd like to shift focus towards building a Desktop App along the lines of Docker Desktop and Rancher Desktop. With this product, we'll be able to make real use-case of P2P container image distribution, with fine grained ACLs.

# Team

## Team Members

- Jasdeep Singh - [Github](https://github.com/jay-dee7) - [Twitter](https://twitter.com/_jsdp)
- Gunjan Valecha - [Github](https://github.com/guacamole) - [Twitter](https://twitter.com/guacaemole)

## Team Website

https://app.openregistry.dev/about

## Relevant Experience

Our team is small but versatile. We have combined experience in multiple technologies like Blockchain, Backends, UI/UX, DevOps and more. We're passionate about Web3 and want to make a dent in the large world of corporate data stealing.

- I (Jasdeep) have over 5 years of experience in Go, SvelteKit, TailwindCSS, TypeSript, Blockchain, DevOps and Cloud Technologies.
I've also done couple of bounties with Protocol Labs in the past, noticiably **CLI Tutor Mode** in the IPFS WebUI [Link](https://github.com/ipfs/ipfs-webui/pull/1572). Along with that, I've donated an OpenSource Library to ENSDomains, it's a lightweight JavaScript Lib, which is used for encoding/decoding different blockchain addresses (https://www.npmjs.com/package/crypto-addr-codec)

- Gunjan Valecha (Guacamole) has more than 6 years of Enterprise Networking, UI/UX, SvelteKit, TailwindCSS, Backends with Go and PostgreSQL. Along with that, she has a natural  talent for Designing beautiful Animations, Illustrations, UX and Merch.
She's has contributed to Hashicorpt Vault, been a member of Community Awards Board at Akash Network (which works towards funding projects that build on and help Akash Network grow) and is part of their Akash Insiders Program. She's quit her job to help build OpenRegistry full-time.

## Team code repositories

- OpenRegistry - https://github.com/containerish/OpenRegistry.git 
- Parachute (current Web UI) - https://github.com/containerish/parachute-ui.git 
- OpenRegistry Web (New Web Interface) - https://github.com/containerish/openregistry-web.git

# Additional Information

We're part of Akash Community Awards Board (CAB). A proposal for $100k USD in AKT has already been approved and is staged for OpenRegistry. This fund gets disbursed for OpenRegistry in Milestones.

**Details:**

| Organization | Amount                                                                 | Received |
| ---- |------------------------------------------------------------------------| ------ |
| Akash Network - Open Cloud Hackathon Winners | $10k USD in AKT                                                        | ✅ |
| Akash Network - CAB Funding Round 1 | $1k USD in AKT                                                         |  ✅ |
| Akash Network - CAB Funding Round 2 | $10k USD in AKT                                                        | ✅ |
| Akash Network - CAB Funding Round 3 | $100k USD in AKT (Received 72,454 AKT) | In-progress|
