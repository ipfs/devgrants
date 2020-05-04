# Open Grant Proposal: `Memex + IPFS/Filecoin + Textile`

**Name of Project: `Memex + IPFS/Filecoin + Textile`**

**Proposer:** @blackforestboi @shishkabab @andrewxhill 

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** 
Yes

**Potentially interesting for**
- Protocol Labs
- IPFS 
- Filecoin

# Project Description

### Problems:

1. WorldBrain's [Memex](https://getmemex.com) is a browser extension for full-text history search, annotations and web archiving. This data is valuable to store on IPFS or Filecoin, but an integration is missing. What can be shared:
  - Collections (Curations of websites, annotations and (soon) web archives)
  - Annotations
  - Tagged pages
  - Bookmarks

2. For app developers there are frictions in experimenting with IPFS because the entire architecture needs to be built on top of it, or suitable abstraction layers need to be considered from the start. 

### Solutions

1. At WorldBrain we developed StorexHub, [an offline-first Zapier](https://medium.com/@WorldBrain/storexhub-an-offline-first-open-source-zapier-f8841810fd9c). It's original purpose is to enable developers/users to integrate Memex with any app or technology flexibly. However it also allows to connect any app with each other and has a database abstraction layer allowing for flexible usage of database technologies and transport protocols like IPFS.
Adding a IPFS/Filecoin plugin gives users the ability to selectively store their data on IPFS/Filecoin 

Example use case: 
A user curates a list of articles, annotations and web archives with the most useful articles about the COVID crisis. They set up the IPFS integration to automatically sync this collection, and also everything that is tagged with "IPFS". 

Developers can also experiment more flexibly with IPFS since they can start with more traditional databases and then gradually migrate to IPFS without rewriting their application logic  or just use IPFS for some of their functionality. A gradual decentralisation- and infrastructure migration process becomes possible.
As an example: Memex's (or other apps) sharing functionality can be done with IPFS/Filecoin, while the rest of the system uses the browser internal database. 
Migrating Memex entire application logic from IndexedDB (browser extension) to TypeORM (mobile) took 1 day. 


## Value
- What are the benefits to getting this right?
Having an IPFS/Filecoin integration would lead to **increased adoption among developers** and **knowledge professionals**. Both are critical audiences to further IPFS's mission statement to *preserve and grow humanity’s knowledge* Memex can provide that because its main users are developers, (investigative) journalists, 2nd Brainers and overall knowledge workers. 
It would also make important bits of knowledge available on the network, like (parts) of browsing histories, bookmarks, annotations, curated lists, tagged content & (soon) web archives. 
Through StorexHub, a more risk free experimentation with IPFS/Filecoin may lead to higher adoption down the line. 


- What are the risks if you don't get it right?
  - Important knowledge will have one way less for being distributed
  - IPFS/Filecoin will not be able to tap into the community of a mainstream user product
  - Less adoption potential for IPFS/Filecoin

- What are the risks that will make executing on this project difficult?

Nothing major we can think of. The only thing is that we are working with Textile.io's stack for the first time. 
With Andrew we have the right advisors on board to make the integration smooth. 


## Deliverables
### Definition of done
- There is a StorexHub Plugin for IPFS/Filecoin powered by Textile's Threads that enables developers and users to store Memex data on IPFS.
- There is a database operations abstraction layer that allows any app to use Textile/IPFS/Filecoin APIs to store data
- There is a Developer & User focused documentation on how to setup the IPFS/Filecoin integration.

## Development Roadmap

**Milestone 1:**
Implemented IPFS/Filecoin plugin for StorexHub with Textile's Threads

Lead: Vincent den Boer 
Advisor: Andrew Hill
Time: 2 days á 600€/day = 900€

**Milestone 2:**
Added database abstraction to enable any app connected to StorexHub to use the IPFS integration.

Lead: Vincent den Boer
Time: 2 days á 600€/day = 1200

**Milestone 3:**
Written documentation for developers and users on how to use IPFS integration

Lead: Oliver Sauter
Advisor: Vincent den Boer
Time: 1 day á 600€/day = 600


## Total Budget Requested

2700€


## Maintenance and Upgrade Plans

This integration will be kept up-to-date with Textile's Threads latest versions. 
The work provides a forkable reference implementation that can be maintained by the community.

The next step after this proposal is to add an end-user-friendly, Wordpress-like interface to setup, configure and maintain this plugin. This is potentially part of another proposal though.
See for more: https://www.notion.so/worldbrain/StorexHub-Interface-3a6024e9538e404ab4df41771302de3f

# Team

## Team Members

- Oliver Sauter @blackforestboi
- Vincent den Boer @shishkabab
- Andrew Hill @andrewxhill


## Team Website

https://getmemex.com
https://textile.io

## Relevant Experience

We're the developers of Memex, StorexHub and Textile and offer all relevant product and technical experience to finish this project in a timely manner. 


## Team code repositories

https://github.com/WorldBrain
https://github.com/textileio


