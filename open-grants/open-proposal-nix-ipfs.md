# Open Grant Proposal: Nix × IPFS

**Name of Project:** Nix × IPFS

**Proposer:** John Ericson ([@Ericson2314](https://github.com/Ericson2314)) on behalf of Obsidian Systems

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes, except where it is not possible due to existing licenses.

All work will be open sourced, and MIT and APACHE2 used where possible, but Nix is LGPL 2.1 (as stated in https://github.com/nixos/nix#license) and so the changes to Nix itself must be under that license.

# Project Description

Nix and IPFS are a match made in heaven.
Nix has been using its own Merkel-style hashing scheme for package management since its debut in 2003, and has risen to prominence in recent years, with over 220,000 commits on its [main repository](https://github.com/NixOS/nixpkgs).
Users of Nix see benefits like reproducible, immutable builds and the guarantee that packages installed side-by-side will never conflict.
Some of the primary problems that users of Nix encounter are:

1. Package cache servers are annoying to configure, require a high level of trust, and do not benefit from network locality
2. Reproducible builds break down when original sources disappear from the internet
3. Nix tends to use more disk space than other package managers

We believe that IPFS is the perfect solution to all of these issues.

1. By providing a cache through IPFS, it will become self-configuring, trustless, and peer-to-peer
2. IPFS's pinning capabilities give organizations an easy way to ensure sources don't get lost
3. An improved caching and pinning system will increase storage flexibility and robustness, allowing users to more aggressively trim their storage usage on devices with limited storage

This proposal outlines a plan to make open-source contributions which will allow Nix and IPFS to fully interoperate, yielding all of these benefits.
Since Nix's logical approach is already so deeply compatible with IPFS, this can be done without major reworking of the Nix codebase, and without breaking Nix's existing user experience.

At Obsidian, we use Nix for all of our production software pipelines as well as developer computing environments.
Although we're thrilled with Nix in comparison to other alternatives, we have been looking for solutions to the problems mentioned above for quite some time.
Based on our discussions with other members of the Nix community, we believe that many Nix users will embrace an IPFS-based solution, leading to a substantial influx of user and data into the IPFS ecosystem.

## Value

### Milestone 1: Distribution with IPFS

Existing mechanisms for data distribution in Nix suffer from a variety of persistence and availability issues that IPFS would solve, bringing a large and active community into the IPFS ecosystem.

#### Source Code Distribution with IPFS

At the conclusion of this milestone, Nix users will be able to share and distribute source code with IPFS.

Nixpkgs has tens of thousands of packages, so over time as the Nix-specific hashes are replaced, the result is as many new pin-worthy CIDs being part of the IPFS ecosystem.

Currently, it is possible but cumbersome for IPFS to be used with Nix to share sources.
By adding support in Nix for using IPFS content addresses, this will be greatly simplified, encouraging Nix users to make use of IPFS.
In return, Nix users will be able to easily ensure that sources will never disappear.

#### Deployments and DevOps with IPFS

This milestone will make it possible to deploy finished builds via IPFS, with IPFS either being a means to move the data to deployment systems or an IPFS FUSE layer being the backing filesystem for deployment systems itself.

This will substantially improve the experience for deploying large clusters, due to IPFS's ability to do peer-to-peer (BitTorrent-style) transfers.

### Milestone 2: Building with IPFS

Once Milestone 1 has enabled the use of IPFS as a distribution mechanism for source code and finished builds, the logical next step is to bridge the gap so different parties can leverage IPFS to collaborate.

Nix's end-to-end build plans, together with IPFS's availability, can make Nix × IPFS the dominant way to get complete 1-click development environments to new devs, no clunky non-composable VMs needed.

#### Sharing build artifacts

This milestone will eliminate the current false choice between content-addressing (but needing to know the content address ahead of time) and not content addressing at all.
Nix build steps—not just retrieval steps—will also produce content-addressed build products out of the box.

This milestone will allow build plans to automatically use IPFS-compatible data every step of the way.
This produces perhaps the first complete decentralized building solution.

#### Adjudicating between sources of builds

Build plans will be shared on IPFS.
Build farms will publish the mapping from build steps to output hashes.
The trustless and trust-needed parts of build caching will be cleanly separated.

The trust mapping from build steps to output hashes can be published on IPFS just like the builds themselves, and subscribed with IPNS.
Users can compare trusted mapping to ascertain the existence of lingering non-determinism or reevaluate their trust.

The entire sources -> build plans -> build products -> deployables lifecycle will be tightly integrated with IPFS.

## Deliverables

### Milestone 1: Data with IPFS

- **Hashing**: Hash files with git tree hashes

- **Retrieval**: Give `builtins.fetchgit` and friends git tree hash support

- **Git-IPLD**: Ensure git tree hashes with IPLD are implemented

- **Store**: Nix IPFS store implementation

- **Export**: Nix export to IPFS, with pinning support

- **Itemize**: IPFS-compatible content-addressed store items with references

### Milestone 2: Building with IPFS

- **Content-addressed derivations**: Build steps ("derivations") which produce outputs that are both content-addressed but don't have a predetermined content address

- **IPLD derivations**: Build steps are in an IPFS native format for easy consumption

- **Publishing**: Publish resolved IPLD derivation -> outputs table on IPFS **(Stretch Goal)**

- **Subscribe**: Subscribe to trusted peer's output maps with IPNS **(Stretch Goal)**

- **Remote Building**: Trustless remote builders can take requests from any client **(Stretch Goal)**

***Stretch Goals represent 'nice-to-haves' that will be completed in sequence with any surplus capacity.**

## Development Roadmap

### Milestone 1: Data with IPFS

**Estimate:** 160 Developer hours

**Staffing:** 3 Developers, 1 PM, 1 QA

**User Stories:**

- *A user can deterministically fetch from git using no Nix-specific hashes, so that anything they fetch is ready to be shared over IPFS without manual effort.*

- *A user of Nix can expect Nix to use IPFS to fetch any fixed output data they want in the IPFS network, so that they can efficiently download the sources they need with less risk of bit-rot.*

- *A user can export sources they've already downloaded to share with IPFS, so that the data won't bit rot*

- *A user can manually convert any (potentially non-content-addressed) store time into a content-addressed store item shareable with IPFS, so that they can use IPFS to deploy builds in creative ways.*

#### Hash files with git tree hashes

Nix currently either hashes a single file (flat mode), or files and directories in a format only it uses (NAR — nix archives).

Nix should instead use something standard.
IPFS has its UnixFS (https://docs.ipfs.io/guides/concepts/unixfs/) but it is evolving and currently allows metadata that Nix purposely does not.
Given that the overwhelming source for source code in Nixpkgs today is git, and the filesystem metadata support does align, git tree hashes are the safer option, and something IPLD also intends to support.

#### Give `builtins.fetchgit` and friends git tree hash support

Nix already has some special built-in retrieving support for Git, in addition to regular user-written arbitrary retrieval steps, newly factored out in a  `libnixfetchers`.
We will give that library tree hash support too.

#### Ensure git tree hashes with IPLD are implemented

Git hashes can be turned into CID hashes, but we were unable to confirm how to get data from git into IPFS to be referenced with one of those hashes.

If this is in fact unimplemented, we are happy to implement it in IPFS.
(Either just the Go implementation which we'll use, or both the Go and JS ones for sake ecosystem consistency).

#### Milestone 1 Nix IPFS store implementation

With the above improvements to Nix, we can, with relative ease, create a new implementation of Nix's Store interface which uses IPFS to obtain content-addressed data that uses git tree hashes from the network.
Nix just needs to download data for now—we can store it twice on both the IPFS and Nix sides to both easily reshare with the network and prevent leeching, keeping this first milestone as simple as possible.

Beyond changing Nix itself, we will adjust all the relevant NixOS modules to ensure the Nix daemon can communicate with the IPFS daemon.

#### Deliverable: Nix export to IPFS, with pinning support

Until now, the IPFS store was something we could only "read from".
We will implement the other methods so we can "write to" IPFS.
Exporting may or may not pin on the IPFS side as the user chooses.

#### Deliverable: IPFS-compatible content-addressed store items with references

Previously, we added git tree-hash support to Nix.
Git tree hashes, however, provide no way to deal with references to other store paths.
Nix currently does support content-addressed store paths with references but uses a variation of its bespoke NAR file format for this.

We'll combine git tree hashes, the references to other store items, and a boolean for whether there is a self-reference in an IPLD wrapper.
We can reuse much of the existing implementation, with only the NAR components being replaced with the underlying file ingestion method (git tree hash, etc).

### Milestone 2: Building with IPFS

**Estimate:** 260 Developer hours

**Staffing:** 3 Developers, 1 PM, 1 QA

**User Stories:**

 - *A user can build a derivation and have its output be content addresses, so it is efficient to share and use as a dependency in downstream builds.*

 - *A user can use the IPFS network as a binary cache for non-fixed output builds.*

#### Deliverable: Floating content-addressable derivations

With this change, derivations (individual build steps in the build plan graph) can produce content-addressed data directly, without requiring a separate conversion step as before.

This is currently being discussed in [Nix RFC #62](https://github.com/NixOS/rfcs/pull/62).
Some details will be further informed by actually writing an implementation, but this can be taken as evidence of the interest in this feature.

For Nix + IPFS, this is required so that regular unknown-output build products can be content addressed just like fixed-output derivations, which will allow them to be shared on IPFS too.

#### Deliverable: IPLD derivations

With entirely new-style derivations (fixed and floating content-addressed derivations) the exact derivation format is less important as it is not used to calculate any paths containing build outputs—all data is content-addressed.
As such, we can freely make big changes without worrying about major backwards compatibility hazards.

Taking advantage of this, we can make a new IPLD-based derivation format modeled after the json output that `nix show-derivation` uses.

#### Deliverable: Publish resolved IPL derivation -> outputs table on IPFS **(Stretch Goal)**

We will publish the rows of the resolved derivation -> outputs table that use IPLD derivations — those rows themselves have an IPLD of a list of pairs (CID values) — or better, a map, if the restriction that keys are strings is ever lifted.

This will likely make use of IPNS to manage the map's growth.

#### Deliverable: Subscribe to trusted peer's output maps **(Stretch Goal)**

When looking up a non-content addressed key such as the output of a derivation, we will consult the output maps of trusted peers and use that to choose content addressed to download from IPFS.

In general, when downloading a number of things that are interdependent, multiple choices for a build translate into decision trees as they constrain dependencies.
We have to be coherent so that the same `drv!output -> content address` choice is made for all dependencies.
No building against one version and then being substituted with another.

Optimal choosing is quite difficult, as discussed in the Nix thesis, but we don't need to aim for optimality, It is sufficient to be strictly path dependent based on what was previously built/downloaded.
The user can evict entries in the store if there is unavoidable conflict and then try again to effect a human-in-the-loop backtracking search algorithm.

#### Deliverable: Trustless Remote Building **(Stretch Goal)**

**Estimate:** 20 developer hours

**User Stories:**

- *A user should be able to use a remote build server without the server trusting the user's machine, so that build farms can take build requests from employees, customers from the general public, etc.*

This step is strictly not necessary for IPFS.
However, it is also:

 1. A useful intermediate milestone in what is otherwise the longest and highest-risk gap between deliverables

 2. Very little marginal extra effort (roughly 3 days)


##### Deliverable: Trustless remote store build protocol

A client should be able to use a remote build server without the server trusting the client's Nix cache.
Currently, it has to trust the client for data it cannot verify.
We will make the server compute the data for itself, and compute it using less client-provided data than was previously thought possible, maintaining equal performance.

## Total Budget Requested

### Total Budget

| Milestone | Developer Hours | Hourly Rate | PM + QA Overhead | Total |
|-|-|-|-|-|
| Milestone 1 | 160 | $125 USD | 15% | $23,000 USD |
| Milestone 2 | 280 | $125 USD | 15% | $40,250 USD |
| **Total** | **440** | | | **$63,250 USD** |

### Obsidian Grant Funding
As an interested party, Obsidian Systems will contribute funding to this grant in the amount of **$10,000 USD**.

### Total Requested

**$53,250 USD**

## Maintenance and Upgrade Plans

We will upstream all changes to Nix, breaking out changes into PRs and writing [RFCs](github.com/nixos/rfcs) as needed.

Changes may be requested during the RFC process, in which case we will make those changes, but we do not expect outright rejection as we think these features will be extremely popular.

Once everything is upstreamed we will continue, as a major industrial user of Nix, to help maintain Nix and the surrounding ecosystem—but the large and active community as a whole will ultimately be responsible for upstream stewardship.

# Team

Obsidian Systems will staff this project with 3 Developers, one Project Manager, and one Quality Assurance Engineer.

## Team Members

Obsidian Systems is a software consultancy with many skilled team members who will contribute to this project.

Our efforts will be led by [John Ericson (@Ericson2314)](https://github.com/Ericson2314), a prominent member of the Nix community.
Other Nix and NixOS maintainers on our team who will be involved include [Ryan Trinkle (@ryantrinkle)](https://github.com/ryantrinkle) (who is also a co-founder of Obsidian Systems) and [Matthew Bauer (@matthewbauer)](https://github.com/matthewbauer).

## Team Website

https://obsidian.systems/

## Relevant Experience

Obsidian Systems has been using Nix for both production systems and developer computing environments since it was founded in 2014.
We've been substantially involved in the Nix community, contributing hundreds of patches, maintaining or co-maintaining key codebases, and presenting at conferences such as NixCon.

Our team lead, John Ericson, has been using and contributing to NixOS and Nixpkgs for the last 7 years, with almost 500 PRs merged to date.
He is also is a shepherd for [Nix RFC #62](https://github.com/NixOS/rfcs/pull/62), a proposal that has already built some consensus for the work contemplated in this proposal.
John is also the primary maintainer of Nixpkgs' cross-compilation infrastructure, which allows developers to easily port their code to a wide variety of computing systems, including embedded and IoT devices.

## Team code repositories

 - https://github.com/nixos/nix/pulls/Ericson2314

   @Ericson2314's existing pull requests, many of which are relevant to both milestones.

 - https://github.com/haskell-nix/hnix

   An interpreter and analysis tool for the Nix package description language with extensive contributions from Obsidian engineers.

# Additional Information

None at this time.
