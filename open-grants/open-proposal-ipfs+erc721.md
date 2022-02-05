# GalaxyX.io
## _Open Grant Proposal_

Name of Project: ERC-721 contracts with IPFS (GLSX)

Proposer: GalaxyXLogan

>Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?

Yes, although as we progress in our product testing with users, we plan to develop pro features and custom integrations that we will charge users for. This potential future revenue would be used to fund infrastructure costs, and on-going maintenance costs.

___________________________________________________________________________________________________________________________

### Project Description:

> Please describe exactly what you are planning to build, problem, & solution.

A software service for art galleries to create and manage digital Certificates of Authenticity (COA) for physical art pieces. The Galaxyx service allows collectors to view ownership of their COAs in a "wallet" as well as prove authenticity of their art through an easy to use web application. When an art gallery sells a piece of art they will take a digital scan of the physical COA as well as take a picture of the art piece. Galaxyx will help them create an ERC-721 token with those two files saved on NFT.storage as the metadata. Then, the token is sent to the coresponding art-collector's Bitski wallet (Bitski.com). Then with a single-page react app (galerielestudio.com), users/art-collectors can view the COAs they own as well as send owned COAs to other wallets.  We are connecting the web3 API to our web application to display the contents of each user's wallet.

Art galleries globally need a secure, cost effective, & reliable way to authenticate & manage Certificates of Authenticity (COA) for physical pieces of art. Currently, most galleries use physical certificates and spend a large amount of money to authenticate art when COAs are lost or held in question. A digital COA using IPFS & Ethereum will cement an immutable ID for each piece of art. This will help to combat fraud, saving the industry time and money in both the long and short term.

The Galaxyx team has the opportunity to help solve this problem for artists in Haiti as well as countries in Central America by gifting this software to Galerie le Studio (GLS). After our pilot with GLS, we plan to launch the software with other galleries as well, starting small and working our way up to larger galleries and more users.  


##### For this grant proposal, we are working with an independent art gallery in Haiti/Miami, Gallery le Studio (GLS).
- https://www.artsy.net/partner/galerie-le-studio/works
- https://www.instagram.com/whereislestudio/?hl=en

## Solution

GLS needs an easy to use web app for internal COA management as well as for collectors to hold/manage their COAs.
Galaxyx will assist GLS in certifying physical art-pieces with digital Certificates of Authenticity (GLSX) minted on Ethereum/Polygon with metadata on nft.storage. Collectors will login to the GLSX app for viewing their COAs using a serverless Auth0 login attached to a one-page react app hosted on AWS.  Upon resale or transfer of ownership, collectors will present a valid ERC-721 token to authenticate their art piece. The ERC-721 will have an IPFS file (Ownership Token's metadata saved in NFT.storage) attached with a unique ID (CID).

##### What can users do on our app?

1. View the certificate or certificates of Authenticity-
2. View what is inside the users registered wallet-
3. Transfer Ownership Token via Bitski-

______________________________________________________________________________________________________________________________________________________________
## More in depth information

A certificate of authenticity is saved on the ERC-721 chain/Polygon Chain and all metadata is saved on IPFS using NFT.storage.
the web-application login is using a serverless Auth0 setup to make the login process convienient and familar for users. Leveraging Auth0 allows GalaxyX to provide industry standard security while maintining semi-decentralized properties.

- User information such as wallet is saved within Auth0 user-metadata.
- NFT-storage call is used to populate the user's stored information.


______________________________________________________________________________________________________________________________________________________________

## Value

>Please describe why the proposal is valuable for the IPFS ecosystem
What are the benefits to getting this right

- We are lowering the level of difficulty, complexity, & security needed to use IPFS and Ethereum as a reliable tool for managing & securing data. 
- Companies want to save data using IPFS and blockchain but is struggling with cost, usability, security, & scalability concerns.
- The goal for our application is to demonstrate IPFS working with Blockchains like ETH to help address major data management problems for web 2.0 & 3.0 companies. Getting this right helps move the world to P2P based data management systems reducing entropy in the expensive and confusing internet environment.

### What are the risks if you don’t get it right?

- Someone wastes ETH when they are minting something: (All of our Github examples will be done on the testnet).

- We could risk making a customer’s private data public by accident. We will test in phases with non-mission critical data first to avoid mistakes.

### What are the risks that will make executing on this project difficult?

- With using a Web ui, we will need to keep elements on the page to a minimum. Many API calls will be more complex so the tradeoff with simplicity is important too.
- Getting metadata to sync with contracts within a reasonable amount of time (can change blockchain networks to our choosing if ERC721 is not the best option).

### Deliverables/Development Roadmap:
> Please describe in detail what your final deliverable for this project will be. Include a specification of the project & what functionality the software will deliver when it is finished.

> The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specifications outlined in the deliverables

> How many people working on each milestone & roles
Time using real dates that it will take to achieve each milestone

Research & experimentation with IPFS node, Erc-20/ERC-721, as well as other token formats (Logan Lentz, Alex Mirran, Vraj Patel) - 28 hrs total

- IPFS & ERC-721, ERC-1155 candidates                           (4 hrs)
- Implementation of Auth0                                       (8 hrs)
- Compiling report on feasibility & usability                   (4 hrs)
- Saving metadata data using IPFS                               (4 hrs)
- Pinning Data in IPFS and NFT.storage                          (8 hrs)

GalaxyX.io Website update and Github documentation writeup/how too (Logan Lentz, Alex Mirran, Giorgio Fasoli, Vraj Patel) - 22 hrs total
- Home Page - About, Software, Documentation (1 hr)
- IPFS information                         (4 hrs)
- Formalize specifications on Github        (6 hrs)
- How-to install/manage docs for GLSX App   (5 hrs)
- User guide for Art collectors             (6 hrs)

V.03 Development (Logan Lentz, Vraj Patel, Alex Mirran) - 40 hrs total
- Creation of ERC-721 token with metadata on nft.storage        (5hrs)
- Token sent to Bitski Wallet and/or Metamask                   (2hrs)
- Website built with client ID authentication and token storage through Bitski hosted on AWS (20 hrs)
- Button to download a Certificate of Authenticity PDF for the token            (4 hrs)
- Bitski App Wallet for JS Application API integration                              (4 hrs)
- API for wallet_addr from web3                                                   (3 hrs)
- Transfer minted tokens to user_wallets                                        (2 hrs)

Documentation for project, performance enhancements, bug fixes (Logan Lentz & Vraj) - 14 hrs
- Github read-me                                                                    (8 hrs)
- Simplification and improvements                                                   (6 hrs)


Deployment with GLS (Logan Lentz- Alex Mirran) - 18 hrs
- Launch software with GLS internally
    -- Set up Login Auth0 Management Account for GalerieLeStudio-                   (2 hrs)
- Implement Domain into application (galerielestudio.com)-                           (2 hrs)
- Launch software with GLS collectors (50-100 users)-                                (4 hrs)
- General Project Management (project communication and feedback)                   (10 hrs)     
- total for a runtime of 6 months minimum. for website hosting, drive. (webapp hosting is within free tier)

Updates, & support (Logan Lentz, Alex Mirran, Vraj Patel) - 16 hrs
- Possible Dependency Modifications                                             (4 hrs)
- Library Updates                                                               (2 hrs)
- Gallery Support/User Training                                                                 (10 hrs)

GLSX monthly costs (12 months - $2200 total)                              
- Crypto (FIL, ETH, LINK - $300 each)
- Email hosting ($300)
- Website hosting ($200)
- Drive ($300)
- MSC ($500)

## Total Budget Requested:
> Milestone, Hours, Cost

### Research & Experimentation
- 28 hours
- $2,520

### (GalaxyX.io) Website update and Github documentation writeup/how too (About, Software)
- 22 hours
- $1,980

### V03-WebUI with client ID authentication through Bitski
- 40 hours
- $3,600

### Documentation for GLSX (Performance, changes, bug fixes, )
- 14 Hours
- $1,260

### Deployment 
- 17 Hours
- $1,530

### Updates and Support 
- 16 Hours
- $1,440

### GLSX Monthly Costs
- $2,000 
> total for a runtime of 12 months minimum. for website hosting, drive.

Total Hours = 138
$90/Hr (15-20 hrs/week)
= $12,620

## Maintenance & Upgrade plans

- Maintain our system with GLS and their 30+ collectors for at least 6 months.

- Maintaining Repos and keeping libraries up to date will be getting done because we plan to use and build off this software adding features as necessary.

## Team
Alex Mirran (CEO)
Northeastern University Finance & Entrepreneurship Undergrad 2018
Experience in technology consulting with many years spent learning in the Bitcoin/Blockchain space
https://www.linkedin.com/in/alex-mirran-5b8128102/
Weekly DLT/Blockchain News https://alexmirran.substack.com/

Logan Lentz (CTO)
University of South Florida Computer Science Undergraduate with experience in Web Development, specifically AWS, IPFS, ect.

Vraj Patel (Front-end Dev)
University of South Florida Data Science & Project Management Undgrgraduate

Giorgio Fasoli (CRO)
Coleads business development & investor relations
Hult University MBA International Business 2019
Background in International trade


#### Team website
https://www.galaxyx.io/

#### Relevant experience
Please describe in your own words your team’s relevant experience, & why you think you are the right team to build this project. You can cite your team’s prior experience in similar domains, doing similar dev work, individual team member’s backgrounds

>The cost & complexity of running a reliable, secure, & efficient data management system is too high for many businesses to deliver. The GalaxyX team has been participating in the IPFS/Blockchain ecosystem for over 4 years looking for ways to address some of these big data management problems. We believe a large part of the solution is web 3.0 adoption within data intensive web 3.0 & 2.0 companies for security & authentication of data.  

>Logan Lentz has been working with IPFS and JS.IPFS for years & has been building models for security, technical efficiency, as well as ease of use. Logan worked at AWS as a junior cloud dev/code reviewer. He also taught an intro to Blockchain course at the USF(University of South Florida).

>The mission of GalaxyX is to help companies and individuals leverage the Open Internet with easy to integrate/use tools. We believe this is a fundamental shift in how data is managed and will have a tremendous impact on the future of humanity over the next 2 decades. Galaxyx is honored to be a part of this community and will continue to further the Open Internet.

A client has asked for this software & we have delivered a base product without any ipfs integration within the app.

### Team code repositories

https://github.com/galaxyxone/auth0_2

Please provide links for prior projects

https://galerielestudio.com/ 
