# Open Grant Proposal: `LegalNFT`

**Name of Project:** LegalNFT (https://github.com/jordan-public/legalnft)

**Proposer:** `Jordan Stojanovski (https://github.com/jordan-public)`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes, upon acceptance of grant.

# Project Description

Please see: [White Paper](https://github.com/jordan-public/legalnft/blob/main/doc/Legal%20NFT%20-%20White%20Paper.pdf)

LegalNFT, a document management, signing and notarization service, which encapsulates legal agreements into Non-fungible Tokens (NFTs). This allows safe electronic storage and communication of the documents, signing and encryption using software and/or hardware devices. The completed agreements are recorded on a public blockchain and immutable decentralized storage, and encapsulated into NFTs which can be appraised and traded on the open market in a centralized or decentralized manner.

Centralized solutions such as DocuSign exist, however, beside their wide acceptance, they are riddled with issues, notably:
- The material to be signed is a single document. A free-form collection of documents, identifications and cryptographic signatures are needed.
- The users are identified by their email address. This could be easily falsified, "hacked" or forged otherwise.
- The documents are stored by the service provider in a centralized manner and its storage safety, security against leakege and content safeguarding is at the mercy of the provider, while the users are forced to trust the provider which in many cases is not capable of accepting the associated liability.
- There is no guarantee that lifetime of the provider will exceede the lifetime of the relevance of the documents.

We are building a system that shall alleviate the above problems, namely:
- The agreements and relevant parts of them can be free-form collections of documents and digital identifications, selectively signed and encrypted by multiple parties as deemed appropriate in each specific case.
- The users are cryptographically identified by their private identities and keys. The document collection is encrypted as desired.
- The documents are stored in an immutable decentralized manner which guarantees tamper proof delivery as well as sovereignty and ownership independent from a vendor.
- Multiple storage options guarantee document availability in an open format even in the case of complete destruction of LegalNFT as an entity.

## Value

For the immutable storage we have chosen IPFS as it allows not only guarantee of originality via content-addressability, but also decentralization of storage with a wide range of options. Most important of the storage options is FileCoin decentralized storage, which would allow longevity and sovereignty of ownership of users' data.

The benefits would be preservation of the following principles:
- No vendor locking - total user sovereignty.
- No third party access to sensitive users' data, as users maintain their own encryption keys.
- Cryptographic identification and firm provability of signature execution.
- Fairness via multiple storage options.
- Longevity of users' data independent of the existence of LegalNFT.

The risks lie mainly in acceptance of the product:
- Marketing: will LegalNFT penetrate the market to become a well known method of usage.
- Legal acceptance: will jurisdictions impede, reject or even just slow down the acceptance of the cryptographic signing and encryption methods used.
- Business model: will the revenue model allow for sustained development, maintenance and marketing to keep LegalNFT alive.

The difficulty lies mainly in the expenditures to gain market and legal acceptance. We do not believe that there is a technical "showstopper" that would make the product impossible. However, once technical development is completed, we will need sufficient funds for legal acceptance and marketing.

## Deliverables

The deliverable is strictly the technical implementation of the product. The funds requested in this proposal are to be used only for development, while for the purpose of marketing and legal acceptance, a separate round of funding shall be sought elsewhere.

So far the project has the following implemented:
- Free-form collection of documents, identifications and digital signatures, stored (pinned) in IPFS.
- Signing of collection of documents using MetaMask and its associated feature to use hardware keys such as Ledger and/or Trezor.

We are seeking funding to implement the following:
1. Upload/storage of large documents (videos, pictures, other media)
2. Encryption of document collections using MetaMask stored keys and/or hardware keys.
3. Secure, private, encrypted peer-to-peer and peer-to-group messaging which would allow exchange of document collection handles and short messages between the involved parties.
4. Anonymous registry of keys/identities.
5. Storage options:
    - 5.1 FileCoin storage presumably using the Estuary
    - 5.2 IPFS Pinning to local server option with easy installation on users' premises
    - 5.3 Two options for third party pinning such as Pinata etc.
    - 5.4 Independent file archiving of IPFS document collections data to local file system
6. Integration with at least one digital identity (DID) standard
7. Pleasant user interface ready for end-user, which would hand-hold the user through the process
8. User documentation

## Development Roadmap

For each above mentioned deliverables:

1. Uploading of documents shall allow continuation after partial upload, checksum display and automatic verification, re-trial options upon interruption/failure. (2 person-week)
2. Generation of session keys and session encryption specific to group of participants. (6 person-weeks)
3. Libp2p style messaging, group management in IPFS-defined groups, encryption of messages. (8 person-weeks)
4. Usage of mutable database implemented via rolling IPFS-stored lists as "file system"-like directories. (4 person-weeks)
5. Details for each...
    - 5.1 FileCoin storage / Estuary, installation and integration instructions (rougly 6 person-weeks; unpredictable - will need mentoring; dependent of the current state of Estuary implementation)
    - 5.2 IPFS Pinning, friendly installation of IPFS service, verification/testing of proper installation and troubleshooting. (4 person-weeks, as components exist)
    - 5.3 Using vendor API to pin, discard and label data. (4 person-weeks; based on looking at Pinata API)
    - 5.4 Serialization of IPFS folders, labeling, removal. (4 person-weeks)
6: MetaMask key identifier injection into DID, signing and verification integration, (8 person-weeks; from looking at Microsoft DID)
7. React/HTML/CSS/UI design work. (12 person-weeks; rough estimate)
8. User documentation, redaction, illustrations (8 person-weeks; rough estimate)

The total developer estimation is: 66 person-weeks, 2 developers are in New York City and 3 developers + 1 documentation writer in Skopje, North Macedonia, all with uneven load
In addition to the above we would allocate a project manager and tester for 20 weeks (40 person-week)
and sysadmin for the duration of 15 weeks (15 person-weeks)

## Total Budget Requested

Estimating a person-week at:
    - US$1000 for developers (66 person-weeks is $66,000 total)
    - US$600 for project manager and tester (40 person-weeks is $24,000 total)
    - US$1000 for sysadmin (15 person-weeks is $15,000)
Total: $105,000 (these numbers include office expenses and equipment)

## Maintenance and Upgrade Plans

After the initial development we shall seek funding for marketing and legal acceptance. 
The legal acceptance work would contain, among other work, creation of suitable template legal agreements and use-case instructions. In this round and before becoming self-suffucient we shall secure funding for the developers, but in reduced numbers (4 => 2 developers in Skopje) and/or possible replacement of developers in New York by less expensive staff. 

# Team

## Team Members

- Jordan Stojanovski, founder, 30+ years experience, Smart Contract, IPFS, React/Java Script developer (https://www.linkedin.com/in/jordan-stojanovski/)
- Andrea Stojanovski, team member, recent Computer Science graduate at NYU Tandon School of Engineering, smart contract and React/JavaScript developer (https://www.linkedin.com/in/ams1704/)
- IWM Network, to provide 4 developers, sysadmin, project manager, tester. We have worked with IWM Network for many years on several project and we have a long term solid trust relationship (https://www.linkedin.com/company/iwm-network-llc/)

Note that staff provided by IWM Network is planned to transfer to the new LegalNFT entity upon completion of the initial technical development phase.

## Team Website

To be developed. Prototype project at: https://github.com/jordan-public/legalnft

## Relevant Experience

Most information is available on LinkedIn.

Jordan Stojanovski has over 30 years of experience in software development, mostly for the financial industry, with recent activities in Blockchain, Smart Contract and Web3 technologies. He has worked as contractor for Credit Suise, as well as created several products for automated trading and high-requency trading, and involved as a partner in two proprietary and high-frequency trading funds. He has lead the development of software for an upcoming centralized cryptocurrency exchange, notably developed in collaboration with IWM Network.

Andrea Stojanovski has been involved in software development during her studies and plans to continue after her recent graduation at NYU. She has worked on Smart Contracts and Web3 front-ends in JavaScript, React and web3.js. 

Recently (in the past 3 months) Andrea and Jordan Stojanovski entered as "Dad and Daughter team" and won first prizes at LatAm Bitcoin/Lightning Network Hackathon and LatAm Algorand Hackathon. In addition they participated in 3 EthGlobal hackathons independently in which Jordan has been awarded prizes in two of them.

IWM Network is a development company with a team of over 20 developers and digital media marketing personnel. In cooperation with Jordan Stojanovski / Logyx Computer Corp. they have delivered completion of several software projects in the past 10 years. They engage in cooperation with proffessors from the local university in Skopje as well as independent contractors in addition to their in-house teams. They have developed several sizable projects for European mobile telecom operators, and U.S. clients such as a chain of medical offices.

## Team code repositories

Jordan, Andrea: https://github.com/nft-lending/nft-lending-algorand, https://github.com/react-lightning-reservation/react-lightning-reservation)

Jordan: https://github.com/jordan-public/legalnft, https://github.com/jordan-public/focus, https://github.com/jordan-public/nft-lending-auction and many more private/proprietary repos

IWM Network: all proprietary (GitHub, BitBucket) as most work is done for commercial clients

# Additional Information

We have a Michigan S-Corp which the founder Jordan Stojanovski owns and has used for contract consulting projects over the past 30 years. Andrea Stojanovski is joining and taking over of some activities. LegalNFT shall be incorporated as separate entity, most likely in Delaware. Even though the project contains Blockchain technologies, there is no handling of funds outside of paying for sercvices / utility. Thus most suitable jurisdiction is USA (a state with good limited liabiliy protection such as Delaware).

We are not only looking for funding, but mentoring, especially in integration of FileCoin / Estuary.
