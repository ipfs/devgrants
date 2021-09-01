# RFP: `Implement Handshake "fallback" resolver`

**Issuer:** `@johnnywu-namebase`

## Project Description

The distributed web community is exploring ways to remove the complexity of addressing IPFS and other content-addressed protocols with distribtued name spaces like Handshake, and one way is by implementing a fallback resolver like the one proposed below for Handshake.

For context, Handshake is a naming project focused on decentralizing the root zone (to decentralize control of domain names from ICANN) with the goal of replacing Certificate Authorities (to rehaul Internet security and privacy).

Given the goals of:
- IPFS doesn’t want to choose winners
- IPFS wants to decouple from ICANN and support non-ICANN namespaces
- IPFS wants to avoid introducing privacy and security risks in implicit defaults
- IPFS wants the alternative namespaces to be DNS compatible. Preferably they can use DoH endpoints

IPFS can accomplish these goals while supporting non-ICANN namespaces by adding a “fallback” resolver option to DNS.Resolvers that points to a list of DoH endpoints. (See `Detailed Requirements & Constraints` below for more info)

## Value

By implementing a fallback resolver to distributed namespaces like Handshake, IPFS makes the decentralized web massively more accessible to anyone already using an IPFS-compatible application, which in turn accelerates the adoption of a fully distributed web.

## Deliverables

A merged PR for implementing a fallback resolver that successfully resolves Handshake names like http://namebase/.

## Recommended Team

Any developer comfortable with everything listed in the below `Resources` section.

## Detailed Requirements & Constraints

Each DoH endpoint can point to a different decentralized naming system. When a query fails to resolve through the “.” resolver, query all of the “fallback” resolvers. If one of the resolvers has a match without conflict, then proceed with fetching the IPFS file. Otherwise if there’s a conflict, return an error code (ie HTTP 409 conflict).

The “fallback” setting can be set by default to [“https://query.hdns.io/dns-query”] which is HDNS.io’s Handshake DoH resolver (note that HDNS.io doesn’t log or store IP addresses or any other personal information, as specified in the privacy policy linked on the website). Polkadomain.org, butterflyprotocol.io, and other decentralized naming systems which issue TLDs can be added as well when they create their own DoH resolvers and issue a PR.

Before starting implementation, one should post the proposed design as a comment here (how config would look like, what implicit default would be, and what needs to be changed to make that possible). Please also ping @lidel and myself (@johnnywu-namebase) to ensure the proposed design is included during IPFS's weekly triage session. By getting confirmation on design and config bikeshed first, we avoid investing time into approach that can't be accepted into the main branch and have more confidence moving forward.

## Milestones & Funding

**Total Funding Amount:** 20,000 HNS ($5,000+)

**Milestones:** 

| 1 | Propose the best design as specified in `Detailed Requirements & Constraints` | 2,000 HNS |
| 2 | Completion of PR (is merged and live) | 18,000 HNS |

## Acceptance Criteria

Handshake names like http://namebase/ should resolve in IPFS-compatible applications like the IPFS Companion extension, Brave browser, and Opera browser, etc.

## Resources

- go-ipfs 0.9 was not released yet, but the code is in master branch and the docs for DNS config are at: https://github.com/ipfs/go-ipfs/blob/master/docs/config.md#dns
- "Ongoing work" in https://github.com/ipfs/go-ipfs/issues/6532 is a good list of code paths that were touched while adding the DNS support, so reading linked PRs there should be enough to build mental model of how DNS in go-ipfs works now.
- Additional tldr: config is in go-ipfs-config, generic DNS logic is in go-multiaddr-dns, and the defaults hardcoded in go-ipfs are in
https://github.com/ipfs/go-ipfs/blob/3b254a631f57d6290ab8179c0cacd72f24ca7dea/core/node/dns.go#L14-L16


## Support and Funding

Namebase is funding this project and our engineers are readily available for assistance with HDNS.io and Handshake resolvers as well.
