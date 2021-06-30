# Open Grant Proposal: `Creatives`

**Name of Project:**  Creatives

**Proposer:** `copious-world`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

We are building web based and decenteralized tools that allow creatives to own their work and profit from their work from conception to consumption.

### Need

People, creatives, create media for the enteraintment, edification and utility of others. This intellectual property that they create derives from the creators many years of life expiences and education. A single act of creation may be sudden and short, lasting minutes. But, the creation when fixed, polished, and produced may be used for many years. 

One would think that those who witness an act of creation would appreciate the quantity of life experience that engenders the creation and provide some remuneration for the creation to the creator. But, that is not often the case. In fact, this is an ongoing problem in many media industries. The author has personnaly provided material to many famous, wealthy perfomers all of whom were happy to receive a gift and then go live their paparazzi worthy lives. The author has attended ASCAP conferences, where the topic is talked about every year. Last week, the author sat in on an SCL (Society of Composer and Lyricists) webinar discussing digital rights and heard the message again.

Two areas of concern may be grouped as follows: 1) creation and split; 2) royalties collection.

At the industry events, people are lectured to about split sheets and facing the uncomfortable discussions about it. The digital rights discussions go on about the less than impressive payouts that the streaming companies provide. The payouts never add up to what the large centralized streaming organizatios seem to offer. There is a lot of confusion over streaming entitlement. A concern is always raised that the largest industry organization are the most likely to make it difficult for original creators to keep their property.

### Solution

The author envisions a solution that has to do with generic media, from machine design to songs. Specific application areas should follow.

Several components of this project may be unified with the basic supposition that media may be stored in a P2P file system, such as IPFS, in an encrypted form and that parties may obtain keys to the data as a result of entering into trust relationships or by verified purchase. Besides access, the process by which the assets come into existence may be tracked by hashing original data, chaining hashes, and recording edit operations (replayable) and storing records of these operations with at least a nonrefutable identifier of a chain of operations stored on a lightweight, rapid, consensus based blockchain.

Tools for managing and finding the assets should be facile interfaces for data management and editing. Or, perhaps existing editing tools such as DAWs can have plugins interfacing a system such as IPFS. Tools should associate the owner of the media with the media at each stage of creating it and editing it.

Since data will be stored encrypted and most likley will not be textual, meta data searching has to be well developed. Further, since an original creation, such as the first recording of a song (bathroom session), will morph in idenity it would help to track the change of media by tracking editing operations and also tracking media replacement operations. Compositing assets from components should also be a part of this system.

When a final, published, asset is put to use, e.g. a play or a print or an assembly, contributors (the creatives who make parts) should be payable for each use or block of uses. So, for a song, a song writer, a trumpet player, a singer, a bass player, etc. should each get their payement. For a machine, the gear designer, the capacitor maker, etc. should be paid. The processes of editing and composing should generate this list of payees, collect it into a creatives contract as a map of idenities to percentages. Then, counting services should execute on the contract any time anyone so much as clicks on a link that makes the asset consumable.

Of course, the idea here might be a little extreme. But, we are closer to it than we have ever been. We are close enough that people are beginning to wish for some verions of it. During the SCL webinar people started talking about how streaming services don't list all the contributors of a piece. People reminisced about following artists from album to album in the days when people still used records, or at least CDs. Who are these people who find streaming services lacking? Folks who write for the movies, Disney, Netflix, Amazon, Warner Brother, etc.


## Value

At this moment, one of the worlds richest singers could walk into a coffee shop with a piano and ask a lonely sole there for a song. The singer can impress the song creator with his or her status and tell the creator that he is lucky to be in the other's presence. The singer can say, "thank you" and jump for the door as soon as the song is sung. The creator can then get state welfare if he is lucky. In the end, a large media company will retain most of the profit gained by selling the creation. This is business as usual.

A benefit of this project will be that people will be able to use IPFS based tools to identify the inception of intellectual property (time and place) and track change in terms of edit operations on non-textual media, keeping a ledger of operations in terms of parameters. (For example, an operation applies a filter to sound, but an update of the sound does not have to be stored. Then, we can ask who applied the filter, such as a mastering agent.)

Another benefit to the IPFS ecosystem that will arise out of the project will be a formalization for managing asset delivery through a cipher pipeline. Counting services can be defined for counting uses of intellectual property, for releasing keys for use, and for interacting with payment oracles in such a way that all creators are justly paid. Here, all creators may include those who edit or those who provide componets (e.g. a gear for a machine) as well as originators.

We get that creation can happen any place on earth and the registration of creation does not have to go through a single service, but can begin locally with the creator and with nearest nodes of a P2P system, which will enhance the security for the creator.

Those who provide the publication of final forms of a creation may be anyone who provides a conformant interface that interacts appropriately with oracles and counting services. We can envision a market of individual asset delivery proprietors who might be drawn from fans, enthusiats, free agents. Asset delivery services might be streaming services or they might be soft panel providers for robot interfaces. In all, collections of links to enciphered data will be played out on a machine, which might be, for example, a laptop's audio or a drone launcher. We expect that an appropriate library foundation will enable proprietors to assemble their concerns easily.

There is a hope for building out a team to complete all the aspects of this work. It will take more than one person to free humanity from the usual way of doing business.

## Deliverables

1) Formalization for managing asset delivery through a cipher pipeline. Code for this will be in libraries and modules. This should include a reference project for a counting service and reference implementations for oracles.

Currently, the author is working on using IPFS based identity to start a session with a blog. Copious-world has code which outlines components in the following:

>  With the user identity fixed within ***web page*** code, the page should be able to contact an ***oracle*** (blockchain oracle e.g. Iota, etc.) with a token for the session. Then the page should be able to contact an ***asset provider*** (e.g. streamer) with the same session token, the user identity, and the requested asset identity. The streaming service should be able to contact a ***counting service*** with collected identities and keys that enable transfer of cipher keys to unlock media for media exposition (e.g. streaming). Blogs and other search and listing services, refered to as ***link services***, contain some modular code for searching meta data and for presenting links (IPFS links) and a view of meta data to users who request media exposition.

2) Pages providing blogging interfaces are static (currently using Svelte) and may be pulled from IPFS or a web server (nginx). These pages provide an interface to asset discovery (meta data searching). And, they will allow for collecting assets into ***link packages*** (e.g. play lists, reading lists, machine components, soft panel components). These link packages may also be assets. Services capable of associating assets with user identites, indicating ownership, should provide meta data management for assets to make it easy for identifying contributors and to make searching easy as well.

Work in this area has already begun and should result in the following:

> A clear definition in specification and code artifacts for metadata and metadata based searching. Dashboads and desktop interfaces (Electron app for one). Topic clustering for clustering links. In older code (Copious CMS), physical parameter search was addressed. A reboot of physical parameter searching could be part of this project.

3) Web interfaces (and perhaps device interfaces e.g. watches) for capturing asset creation. A web interface already exists for taking in sound recording, hashing the media and chaining BLOBs of the data. The hash chains are signed and sent to a service. Edit operations can be captured from the interface and cataloged with the hash chains. This code does not yet use IPFS or other blockchain services.

This project should include the following:

>Complete the sound capture interface (web version), integrating it with IPFS and blockchain oracles. Integrate management of the assets created by this application with dashboards and blog interfaces which interact with IPFS.


## Development Roadmap

1) Bring up the revised web sites for copious.world and popsong.now. This includes the following:

* Integrate contact and identity pages (copious.world/interplanetary-contact) with session authorization (login/registration) using IPFS CID's for identity references. Use interplanetary-contact for contact forms.
* Upgrade the dashboard interface for creators using sessions. It comes up and uses IPFS. It could look better. Services need to be on a stable, worry-free machine. **Phase 1** (current): up again and a little nicer (basically an upload interface); **Phase 2** (later): work with an interface developer for reactivity, style, the inclusion of editing tools, better code organization.
* Popsongnow.com includes a lazy loader link for the recorder tool which hashes sound BLOBS and chains hashes and captures editing operations. Turn it back on, bringing up its server. Make it ready for IPFS integration.

**Time and cost (1)**: \$3K Up to 3 Weeks. 

2) Counting Service, Link-packages, Exposition Services, Oracles

* **Counting Service**: A basic counting service has been coded (awaiting testing) in node.js and is quite abstract. It assumes that modules will be loaded according to a configuration file, and that these modules will provide interfaces to payment oracles to obtain funds from consumers and to pay creatives. The service uses unique IDs (assumed to be CIDs) to identity assets and users and assumes all contract activity is between UIDs. It is a TLS service with no web service. A very small JSON command set is provided. After mock testing, modules will be developed. The county service is implemented off-chain in order to provide rapid counting. It will refer to oracles for monetary transactions.

>**Time and cost (2.a)**: \$6K Up to 3 Weeks.

* **Link Packages**: Interfaces for consumers supplied by link providers (blogs with custom search engines) will have means of requesting the utilization of a link-package (e.g. a play list). Copious-world has a Svelte based blog interface that includes link-package creation (link collecting). Users, in session, may inject their link-package into their dashboard for editing (TBD) and obtain a CID for the final package or they may obtain a CID for the package at the blog interface (TBD). They may then send the link-package CID, coupled with their session token, to an Oracle in order to release funds for use by a counting service. The counting service may then release plays via Expositions services.

>**Time and cost (2.b)**: \$2K Up to 1 Week.

* **Exposition Services**: Copious-world is now utilizing its prototype streaming service (copious-streamers) to deliver an asset or two.(node.js) The service pulls an encrypted asset (song) from IPFS and uses and AES key to decrypt and send the stream to the player on the blog interface (svelte-blogs/streams). This is a prototype and uses one key that has been made public for noodlers. These simple servers can be expanded with a module that interacts with the blog web page and the counting service. (**Exposition Business Module**) The module is responsible for exchanging keys with the counting service, relaying the state of usage permisions, and providing the deciphered stream to the streamer delivery system.

>**Time and cost (2.c)**: \$2K Up to 2 Weeks.

* **Oracle**: Code for an oracle is to be done (TBD). The oracle unlocks funds for the exposition of assets and releases them to vetted counting services. The oracle will assert the state of release in a blockchain transaction and make the counting services be aware of the transaction. The oracle will buffer against the delay of transacting on the blockchain, providing rapid permission to the blog page (link provider pages). The transaction for consumption (low priced expositions) will be immediately available on request from a counting service or will be broadcast to counting services in response to receiving a session token. The state of permission may be rescinded if funds are not available (which may interrupt plays). The transaction for consumption (high priced exposition) will wait for contracts to resolve prior to transmitting any state of permission. (***At the moment, considering an IOTA based oracle for low price transactions***).

>**Time and cost (2.d)**: $3K Up to 3 Weeks.

**Time and cost (2)**: \$18K Up to 9 Weeks.

3) IPFS for Recording and Chain Integration

* Use IPFS to store the enciphered version of orginal media. (Currently, a copy is stored in IndexDB. Currently, media is just short sections of sound.) Integrate IFPS with the backend.
* Create an Oracle for storing editing sequences and CIDs of checkpoint media. On-chain data is chained editing operations and CIDs.
* Improve user interfaces

>**Time and cost (3)**: \$8K Up to 4 Weeks.

Currently, one person is allocated for everything. We are especially interested in finding contributors in stage 2. For this, we will begin with bounties, and will reach out to those who contribute to packages found in the dependencies of existing copious-world node.js projects.

Assume this starts July 15, 2021

* 1) 3 Wks: Jul 15, 2021 - Aug. 5, 2021
* 2) 9 Wks: Aug 6, 2021 - Oct 1, 2021
* 3) 4 Wks: Oct 4, 2021 - Oct 28,2021

## Total Budget Requested

**Total**: \$29K

**Breakdown:**

* Basic Survival (one person): \$3K per month = \$9K
* Basic Operations: \$500.00 per month = \$1.5K
* Additional Equipment Costs: \$3K
* Bounties (team building): \$8K
* Taxes: \$7.5K

## Maintenance and Upgrade Plans

The author hopes to grow a team and create a community of users around the tools developed by this project. Part of the aim in making the software is to support future development related to IoT, DAWs with AI, remote work, etc. Link clustering and payout should find a way to become stable and in common use.

After initial project work, there is great need to support efficiency and a growth of applications. So, contributing to IPFS enhancements would be part of the future, with node software taken close to the machine with code in C or perhaps hardware acceleration. Narrowing pub/sub pathways and providing ways of learning which nodes would be most stable for supplying content related to types of meta data might also be part of the future. Maintaining libraries for a community of applications having different interfaces, search modules, etc. would be part of the future as well.


# Team

## Team Members

- Richard Leddy
(rleddy@copious.world) -- www.github.com/rleddy
[linked-in](https://www.linkedin.com/in/richardaleddy/)


## Team Website

[copious.world](https://www.copious.world)

## Relevant Experience

Richard Leddy has been working for many years developing software for all kinds of concerns. Please see this GitHub sponsor page: [sponsor copoius-world](https://github.com/sponsors/copious-world)

## Team code repositories

* [copious-world](www.github.com/copious-world)

* [copious-transitions](www.github.com/rleddy/copious-transitions)

# Additional Information

Please contact.
