# Targeted Grant: Active local discovery in Brave

**Issuer:** @lidel and @autonome  
**Recipient:** @RangerMauve

## Project Description

<!-- Please fill in details about what you're trying to build. What is the purpose/context? What are the high-level requirements?

This section should be 2-3 paragraphs long. -->

**This project’s goal is to get active local peer discovery working in [IPFS-Companion](https://github.com/ipfs/ipfs-companion) on the [Brave](https://brave.com/) browser when embedded [JS-IPFS](https://github.com/ipfs/js-ipfs) node is used.**

Part of this will be to find out what isn’t working in the current implementation and/or [mDNS spec](https://github.com/libp2p/specs/blob/master/discovery/mdns.md) and to fix it, or propose changes that will enable discovery to work in decentralized fashion.

Secondary goal is to test and refine the Targeted Grant process.

## Value

<!-- Please describe why the work that will come out of this Targeted Grant is valuable for the IPFS ecosystem. -->

This work enables browser-to-browser IPFS connections in local networks, a powerful expression of offline and local collaboration use-cases of IPFS technology.

It will lay the groundwork for interoperable local network discovery between browser and non-browser nodes and also providers a low-barrier way for people to experience the true power of IPFS without installing separate daemon software.

It will also proof-check our existing specs related to mDNS local discovery, making it interoperable across varying runtime environments.

## Deliverables

<!-- What are you expecting the proposer to deliver at the completion of this project?-->

- Local discovery between two JS-IPFS nodes running in Brave is merged to ipfs-companion.
- Upstream fixes to `js-libp2p-mdns`, `libp2p/specs` (if needed)

## Team

<!-- List the skills and experience you are looking for. Teams with this background might be a better fit for this project.-->

- [@RangerMauve](https://github.com/RangerMauve) - (Grant recipient) Active member of the dweb community.
   Done multiple grants with DAT and are key member in team that set up the DAT Foundation.

- @lidel - (Protocol Labs) Technical advisor

- @autonome - (Protocol Labs) Grant advisor

## Detailed Requirements & Constraints
<!-- You can use this section to detail requirements that the deliverables must include.

Also include any relevant constraints that the implementer should be aware of before beginning this project.-->

Our browser extension is whitelisted in Brave to have access to TCP and UDP socket APIs at `chrome.sockets.*`.  
We take advantage of that when "Embedded with chrome.sockets" node type is selected in *Preferences*.

Right now, only the passive discovery of go-ipfs works (via _compat_ submodule from [js-libp2p-mdns](https://github.com/libp2p/js-libp2p-mdns)):  the IPFS node running in Brave is not announcing itself to other peers on the same local network, and a centralized signaling service at `ws-star.discovery.libp2p.io` needs to be used instead.


It is unknown if existing mdns discovery spec can be used in environment with `chrome.sockets`, and depending on the research done as a part of this grant, different solutions can be delivered:

- If `js-libp2p-mdns` can be fixed, but requires changes to [libp2p mDNS spec](https://github.com/libp2p/specs/blob/master/discovery/mdns.md), PRs making changes to the libp2p spec and relevant libraries and app repositories need to be approved and merged before proceeding further.
- If `js-libp2p-mdns` could not be used or fixed, a separate discovery module dedicated for use in runtimes with `chrome.sockets` can be created. If so, it should be:
    -  published on NPM
    -  licensed under MIT+Apache 2.0 ([PL's permissive licensing stack](https://protocol.ai/blog/announcing-the-permissive-license-stack/))
- Whitelisting additional `chrome.*` APIs is on the table, but requires PoC validating the need.

## Milestones & Funding

**Total Funding Amount:**  $3600 <!-- List the total proposed funding amount (currently in USD, eventually can be a distribution between USD/FIL)-->

**Milestones:** (working 10 hours a week)<!-- Make sure that the values in the Funding column add up to the Total Funding Amount listed above.-->

| Milestone No. | Milestone Description | Funding | Estimated Timeframe |
| --- | --- | --- | --- |
| 1 | Research relevant libraries specs and available APIs and prepare a standalone PoC | $1200 | ~35h  |
| 2 | Submit PR changes to respective specs, libraries and projects | $1200 | ~20h |
| 3 | Addressing reviews, all PRs are merged | $1200 | ~10h |



## Acceptance Criteria

<!-- What are the acceptance criteria for each milestone and for the final deliverables? These should be as objective as possible. They will be used to determine whether or not a grantee will receive payment for work completed for a milestone. -->

- Local discovery between two JS-IPFS nodes running in Brave works in a LAN without connection to the internet (no centralized signaling service).
- `js-libp2p-mdns` is in sync with [the spec](https://github.com/libp2p/specs/blob/master/discovery/mdns.md).
- PRs making changes to the libp2p spec and relevant libraries and app repositories are approved and merged.
- JS-IPFS node running in Brave can announce itself to go-ipfs 0.4.23 using `mdns:compat` from `js-libp2p-mdns`, or it is documented why it is not possible to implement it on top of `chrome.sockets` for future work in this problem space.

## Resources

<!-- Link any resources that might be helpful for an implementer who is working on this project.-->


- ipfs-companion issue: [Brave: LAN discovery & announcement](https://github.com/ipfs-shipyard/ipfs-companion/issues/758)
    - [node types in ipfs-companion v2.10.0](https://github.com/ipfs-shipyard/ipfs-companion/blob/v2.10.0/docs/node-types.md)
    - [ Embedded JS-IPFS in Brave](https://github.com/ipfs-shipyard/ipfs-companion/issues/716)
- Local discovery library used by js-ipfs in ipfs-companion: [js-libp2p-mdns](https://github.com/libp2p/js-libp2p-mdns)
  - **Note:** it aims to support existing mDNS discovery service provided by every go-ipfs node (`mdns:compat`) and the new spec that is compliant with  DNS Service Discovery (DNS-SD), as described in  [libp2p/specs/discovery/mdns.md](https://github.com/libp2p/specs/blob/master/discovery/mdns.md).
      - js-ipfs supports both
      - go-ipfs supports only the legacy mdns method (`mdns:compat`)

## Support and Funding

<!-- Who is backing this project? How will they pay the implementers? If you have not already added your information to [FUNDING](../FUNDING.md), you can do so now and link it here. Include a legal entity name if possible.

Any other organizations that choose to add their support to this Targeted Grant will do so in this section.
-->

This grant is funded by Protocol Labs.  
Technical guidance will be provided by @lidel.
