# Open Grant Proposal: Almonit Decentralized Website Generator

**Name of Project:** Almonit Decentralized Website Generator (DWG)

**Proposer:** Almonit

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?**: Yes

# Project Description

The aim of this project is to create a tool for building personal ENS+IPFS websites. In the rest of document we call such websites, "Dwebsite" (Decentralized websites). 

The result is simple, CV-style, easily-generated Dwebsites. These Dwebsites are meant to be easy-to-create "visit cards" for those who own an .eth name but did not link it to a Dwebsite.

This project approaches two problems. The first is the relatively low number of Dwebsites built on top of IPFS. The other is that more than 99% of purchased .eth names have no Dwebsite linked to them.

According to our data, received from ENS, there are around 310,000 .eth names registered, not including subdomains, which increase the number even more. However, our research shows that no more than a few hundreds of those .eth names are linked to a Dwebsite. Most of those linked to a Dwebsites offer little value if any, often being simple "hello world" experiments. In [our index](http://almonit.eth.link/#/discover/) we counted so far just over a hundred polished Dwebsites. This shows the existence of a few hundred thousand .eth names waiting for a Dwebsite to link to.

Our end goal is that any entity owning an ENS name would link it to a Dwebsite. We imagine a future where people exchange .eth names instead of visit cards. We derive inspiration from the increasing popularity of using .eth names instead of wallet addresses.

Our solution provides an easy interface to quickly create a personal IPFS website and connect it to an ENS name. Using simple UI, the process can be as fast as a few minutes.

We intend to provide a full solution, including not only the building part of the personal Dwebsite, but also registering it in ENS and connecting it to an IPFS pinning service. 

## Value
We see Dwebsites build on top of IPFS as one key use-case of IPFS technology. 

However, as IPFS Dwebsites require slightly different design and routing than server-served websites, common tools do not support the creation of Dwebsites, keeping their numbers low at the moment.

If DWG gains popularity, the ecosystem benefits by a significant number of additional Dwebsites. As we aim for those websites to be used as "visit cards", we hope for it to become a popular use-case of IPFS.

If DWG does not become popular, it still exists as a base tool to develop future more sophisticated Dwebsite builders on top of, such as blogs or e-commerce Dwebsites. As long as one believes in the potential of Dwebsites, there is a value for creating DWG.

The project is built using technologies we have experience with, hence we do not expect any technical difficulties in executing it. 

## Deliverables
For this project we deliver two items. 

1. DWG Software. Using this software people can create a service for building personal Dwebsites. 
2. DWG platform. We will operate a service for building Dwebsites based on the DWG software for a period of at least one year.

We already created a mock-up demonstrating the functionality of the software and service being delivered. See [details in Milestones](#Milestones). 

## Development Roadmap
The project contains six different components. We first describe the different components, following by breaking them down into roadmap and milestones.

The components composing the project are:
1. Progressive WebApp (React, NodeJS, Hugo).
2. Static website framework (Hugo framework).
3. Backend (node.js).
4. Web3 component (Metamask etc.).
5. ENS component.
7. IPFS backend (Rust or node.js).

### Milestones
**Remark on the division of work**: We are a team of four people, all do a bit of everything. The names written here are of the person leading each specific milestone, but please keep in mind the whole team contributes in all stages of the project.

The project contains four milestones. We list them in the order of delivery. Next to each milestone we list the development time. The real date will be determined based on the starting date of the project.
1. Progressive WebApp and Static website framework , first part of backend (5-7 weeks): led by *Muhammed Tanrıkulu*.
2. Web3 and ENS components (1-2 weeks): led by *Paul Peregud* and *Muhammed Tanrıkulu*.
3. IPFS component (1-2 weeks): led by *Eyal Ron*.
4. Integrating the components into DWG (2 weeks): led by *Eyal Ron* and *Krzysztof Lewosz*.

The total development period is 9-13 weeks.

### Detailed description of every milestone

#### Progressive WebApp and Static website framework, first part of backend (5-7 weeks):
This milestone can be considered as the heart of the project.

The Frontend is a series of screens developed using React. These screens guide the user in the process of creating a Dwebsite.

The Dwebsites are created using Hugo framework for generating static websites, hence this component must be developed at the same time as the UI. Note that in the future it is possible to add other frameworks, such as Jekyll, to the DWG. Hugo is chosen since in our experience it is a perfect fit for both building Dwebsites and for integrating with the rest of the DWG components.

The backend (NodeJS) in this part manages the transition between the different UI screens including communication with the Hugo framework.

Below is the functionality in details, including mock-up pictures to demonstrate it.
- **Welcome screen**. In this screen users connect to their Ethereum wallet, enter their .eth name and validate it. The page links to instructions for purchasing .eth names in case the users have none.
<kbd><img src="http://almonit.club/application/1Welcome.png" /></kbd>
- **Theme selection screen**. In this screen users select a theme for their Dwebsite. We intend to support initially at least four different Hugo themes.
<kbd><img src="http://almonit.club/application/2theme.png" /></kbd>
- **Details filling screen**. In this screen users enter data needed to build the Dwebsite. The form depends on the Hugo template chose in the previous step, and will be different for each template.
<kbd><img src="http://almonit.club/application/3details.png" /></kbd>
- **Build screen**. In this screen users see an overview of the data they entered. If they authorize the data, they choose to build the website.
<kbd><img src="http://almonit.club/application/4publish.png" /></kbd>
- **Preview screen**. In this screen the users see a preview of the Dwebsite. If they choose to publish, DWG will use the ENS and IPFS components to publish the Dwebsite.
<kbd><img src="http://almonit.club/application/5result.png" /></kbd>

#### Web3 and ENS components (1-2 week)
This milestone is used in the first step of the DWG, verifying users ENS domain, and in the last step, setting the IPFS CID as the contenthash of the ENS domain of the user.

The integration to wallet (Metamask etc.) is done via web3.js. Based on the Ethereum account we add an identicon to the upper right corner of DWG (see mock-up pictures above) to indicate user account in charge.

The interaction with ENS is done via web3.js using ENS contract ABI.

We create for the development process a local Truffle environment to test this component and the next one.

#### IPFS component (1-2 week)
This milestone connects DWG to IPFS, offering two functionalities. 
1. Calculating the Dwebsite IPFS CID.
2. Pinning the Dwebsite using an existing IPFS pinning service (Infura, Pinata or other) or possibliy a pinning service we provide.

It will be decided at a later stage if this component is written in Rust or node.js.

#### Integrating the components (2 weeks)
This proposal is for a complex project containing many different components. While we intend to do on-going integration of the components during the whole development process, we expect the final stage to take additional two weeks due to the complexity.

This stage also includes polishing the project and preparing for publication.

## Total Budget Requested
The budget requested is 20,000 USD. We plan to use it as follows:
1. **18,000 USD**. Compensation for team members for their working time.
2. **2,000 USD**. Expenses, such as server costs, team meetings costs, Dweb meetups we organized to promote DWG and so on.


## Maintenance and Upgrade Plans

**Operation**. Almonit will run DWG as a service for a period of at least 12 months.
**Maintenance**. Almonit will maintain the codebase for at least 12 months.
**Upgrade**. Almonit plans to extend DWG functionality with time, depends on users feedback after the release.

# Team

## Team Members

- Eyal Ron [[Github](https://github.com/eyalron33/), [Linkedin](https://www.linkedin.com/in/eyal-ron-002358131/)]
- Muhammed Tanrıkulu [[Github](https://github.com/mdtanrikulu/dwg), [Linkedin](https://www.linkedin.com/in/muhammedtanrikulu/)]
- Paul Peregud [[ENS+IPFS](http://pepesza.eth), [Github](https://github.com/paulperegud), [Linkedin](https://www.linkedin.com/in/paulperegud/?originalSubdomain=pl)]
- Krzysztof Lewosz [[Linkedin](https://www.linkedin.com/in/krzysztoflewosz/)]

P.S. we hope future versions of open grants proposals will include links to personal Dwebsites.

## Team Website

https://almonit.club or https://almonit.eth

## Relevant Experience
#### Almonit Project Experience

As a team Almonit exists since more than half a year already. We published Dwebsite Browser Extension for both [Mozilla](https://addons.mozilla.org/en-US/firefox/addon/almonit/) and [Google Web store](https://chrome.google.com/webstore/detail/almonit/adobfkcnfkodjfobnndpfipdanhdcafm). Those extensions allow users access Dwebsites via their browser. 

We recently published our second big project, a Decentralized Search engine for Dwebsites. The search engine is a Dwebsite itself, see https://almonit.club or https://almonit.eth.

#### Personal Experience
**Eyal Ron**. PhD in Mathematics, co-founder of Cryptom, author of two DIN (German national organization for standardization) Blockchain specifications, previous core developer of Bisq (under the alias *Neiman*), a peer-to-peer Bitcoin exchange.

**Muhammed Tanrıkulu**.  Senior Software Engineer at Golem Factory, experienced React and blockchain developer.

**Paul Peregud**. Software Engineer at imapp.pl; Working on OmiseGO, worked in the past on Golem Factory.

**Krzysztof Lewosz**. SST Manager in Egmont Polska, Supervisor in Vaultex UK Ltd. Experience in management roles gained from history in the Financial Services industry.

## Team code repositories
[Almonit team github repository](https://github.com/almonit). 
[Almonit browser extension](https://github.com/almonit/almonit-plugin).

The code of Almonit Search Engine will be open in the future once it reaches maturity.

# Additional Information

We would like to stress that as DWG is a complex project containing a large number of different components, its development is time consuming and the sum requested does not cover the full cost of the project. However, since we would like to implement this project as part of over vision for the internet, we will do the extra working hours on our account.
