**Open Grant Proposal**

**Name of Project:**  ERC721 contracts with IPFS (GLSX)

**Proposer:** @GalaxyXLogan

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?**

Yes, although as we progress in our product testing with users, we plan to develop pro features and custom integrations where we will charge a fee. This potential future revenue would be used to fund infrastructure costs, and on-going maintenance costs. 

**Project Description:**

Companies need a secure, cost effective, & reliable way to authenticate & manage data as the costs of ensuring trust in the digital world are very high. GalaxyX is building software that makes data resilient & verifiable by leveraging Web 3.0 technology like IPFS, & Ethereum (ERC-721) through an easy to use web-ui in JS. We are focused on simplicity in both the backend & frontend of the application. Our plan is to build efficient methods to link IPFS hashes with other forms of data for normal companies to cost-effectively secure their data at scale.

For this grant proposal, our client is an independent art gallery in Haiti/Miami, Gallery le Studio (GLS). 

https://www.artsy.net/partner/galerie-le-studio/works
https://www.instagram.com/whereislestudio/?hl=en

The GLSX project is to provide an application for GLS to authenticate physical paintings using the resiliency/censorship resistance of IPFS + Blockchains. They want to demonstrate a new standard for combating fraud in their business by digitizing physical Certificates of Authenticity (COA) and allowing collectors to hold their digital COAs. GLS needs an easy to use web app for internal tokens use as well as for collectors to hold/manage their painting certificates. There will be a simple app login for managing COAs in an easy to use UI + Bitski wallet.


**Value:**

We are lowering the level of difficulty, complexity, & security needed to use IPFS as a reliable tool for managing & securing data. The world wants to save data using the censorship resistance of Blockchain, but is struggling with cost, usability, security, & scalability concerns. The goal for our application is to demonstrate IPFS working with Blockchains like ETH to help address major data management problems for web 2.0 & 3.0 companies (by hashing data inputs into the network). Getting this right helps move the world to P2P based data management systems reducing entropy in the expensive, confusing, & unfair internet environment. 

**What are the risks if you don’t get it right?**
- Someone using the code on the main ETH chain instead of the testnet and wasting ETH gas. (All of our Github examples will be done on the testnet). 

- We could risk making a customer’s private data public by accident. We will test in phases with non-mission critical data first to avoid mistakes. 

**What are the risks that will make executing on this project difficult?**
- Keeping our UI light. With using a Web-ui, we will need to keep elements on the page to a minimum.
- Dealing with blockchains when their slow. Getting metadata to sync with contracts within a reasonable amount of time (we can change blockchain networks to our choosing if ERC721 is not the best option).


**Deliverables/Development Roadmap:**

1) Research & experimentation with IPFS node, ERC-721, as well as other token formats (Logan Lentz, Vraj Patel)
- Saving data on an ETH token
- Pinning Data in IPFS
- Compiling report on feasibility & usability
- How could we do this with IPFS alone?


2) Udpate company website: galaxyx.zil (Logan Lentz & Vraj)
- Why use IPFS and the Bitski wallet
- Project Description


3) V.03 (Logan & Vraj)
- ERC-721 with IPFS hash within metadata for document location(5hrs)
- [ERC-721 Contract Factory for GLSX]
- Creation of ERC-721 Token sent to Bitski Wallet and/or Metamask(5hrs)
- WebUI built with client ID authentication and token storage through Bitski(40 hrs)
- Click hash to download a Certificate of Authenticity PDF for the token(ipfs link)
- 

4) Filecoin contract for document data(5-10hrs)
- Configure Lotus
- Pinata can be used as well 


5) Documentation for project, performance enhancements, bug fixes (Logan Lentz & Vraj)
- Github read-me
- What are the reasons you want to use this system
- Here is how you can set this up for yourself checklist 	


6) Deployment with GLS (Logan Lentz)
- Launch software with GLS internally 
- Launch software with 1 to 4 GLS collectors 


7) Updates, & support (Logan, Vraj)
- Possible Github Repo Migrations
- Library Updates
- User On-boarding

**Total Budget Requested:**

1) Research & development with IPFS & ERC-721 other ERC candidates 
- Compiling report on feasibility & usability
- 35 hrs
- $3,150

2) GalaxyX Website
- About, Team, Project
- 15 hrs 
- $1,350

3) Updated GalaxyxLogan repository to further formalize GLSX specifications
- IPFS usability
- 10h hrs
- $900

4) V.03 
- ERC-721 with IPFS hash within metadata(5hrs)
- [Contract Factory for GLSX]

- Creation of ERC-721 Token sent to Bitski Wallet and/or Metamask(5hrs)

- WebUI with client ID authentication through Bitski(40 hrs)

- Filecoin contract for document data(5-10hrs)
- 60 hrs 
- $5,400

5) Documentation for GLSX
-Performance, changes, bug fixes  
- 20 hrs
- $1,800

6) Deployment, Updates, & Support 
- 10 hrs
- $900

7)  GLSX monthly costs (2) 
- Servers
- Crypto (FIL, ETH, LINK - $200 each)
- Email hosting
- Website hosting
- Drive 
- $1,500
**
Total Hours = 150
$90/Hr (15-20 hrs/week)

= $15,000**

**Maintenance & Upgrade plans:**

Maintain our system with GLS and with at least 1 of their collectors for at least 6 months.

Maintaining Repos and keeping libraries up to date will help build off this software adding features as necessary. 


**Team:**
Alex Mirran (CEO)
Northeastern University Finance & Entrepreneurship Undergraduate 2018
Experience in technology consulting with many years spent learning in the Bitcoin/Blockchain space 
https://www.linkedin.com/in/alex-mirran-5b8128102/
Weekly DLT/Blockchain News https://alexmirran.substack.com/

Logan Lentz (CTO)
University of South Florida Computer Science Undergraduate with experience in Web Development, specifically AWS, IPFS, ETH
https://github.com/noryev


Vraj Patel (Developer)
https://www.linkedin.com/in/vraj-patel-9b827312a

 
Giorgio Fasoli (VP) 
Hult University MBA International Business 2019
Background in International trade 


**Team website:**

galaxyx.io

galaxyx.zil

**Relevant experience:**

The cost & complexity of running a reliable, secure, & efficient data management system is too high for many businesses to deliver. The GalaxyX team has been participating in the IPFS/Blockchain ecosystem for over 4 years looking for ways to address some of these big data management problems. We believe a large part of the solution is web 3.0 adoption within data intensive web 3.0 & 2.0 companies for security & authentication of data.  

Logan Lentz has been working with IPFS and JS.IPFS for years & has been building models for security, technical efficiency, as well as ease of use. Logan worked at AWS as a junior cloud dev/code reviewer. He also taught an intro to Blockchain course at the University of Southern Florida.

We started creating ERC-20 tokens and sending those out to our clients to signify ownership as well as separately having a certificate of authenticity uploaded on ipfs. After finding that we can point to an IPFS address natively using ERC-721 tokens, we wanted to take advantage of better functionality. 

A client has asked for this software & we need help getting there with some resources. 
