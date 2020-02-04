# Open Grant Proposal: Rust IPFS
> Category: core-dev | Proposed by: Mark Henderson (MRH.io), Joonas Koivunen (Equilibrium Labs)

Rust, the programming language, has enjoyed a recent spike in popularity. This is due both to
its inclusive community, and also being a safe systems language with performance comparable to
C and C++. An IPFS implementation written in Rust only makes sense.

The IPFS community agrees, and since then has created an astonishing amount of output.
David Craven’s “rust-ipfs”, the work of the multiformats team, and of course Parity’s rust-libp2p. Our aim is to build upon this work, forking only when necessary, and carry the torch across the finish line.

If funded, the IPFS implementation detailed in this proposal would be a properly stewarded Rust
codebase that could stand alongside its Go and JS siblings, and be used successfully in a
variety of contexts: either as a “crate,” a command line interface, or via its familiar HTTP API.

At the very least, we hope that our effort in scoping and planning is useful to any others who
might want to continue - and hopefully complete - this work.

_We agree to license past and future contributions of this proposal under the dual
MIT/Apache-2.0 license, allowing licensees to choose either at their option._

## Table of Contents

* [Project Description](#project-description)
    * [Summary](#summary)
    * [Value](#value)
    * [Survey of Community Efforts](#survey-of-community-efforts)
        * [libp2p + pubsub](#libp2p--pubsub)
        * [IPFS DAG / IPLD](#ipfs-dag--ipld)
        * [IPFS Blockstore](#ipfs-blockstore)
        * [HTTP](#http)
        * [What is missing?](#what-is-missing)
    * [Maintenance and Upgrade Plan](#maintenance-and-upgrade-plan)
    * [Figure 1. Risk Assessment](#figure-1-risk-assessment)
    * [Project Team](#project-team)
* [Project Plan](#project-plan)
    * [Summary](#summary)
        * [Q1 2020](#q1-2020)
        * [Q2 2020](#q2-2020)
    * [Implementation Details](#implementation-details)
        * [IPLD](#ipld)
        * [libp2p](#libp2p)
    * [Metric: Number of HTTP Endpoints Implemented](#metric-number-of-http-endpoints-implemented)
    * [Definition of Done](#definition-of-done)
    * [Out of Scope](#out-of-scope)
    * [Phase 1.0 Interoperability Baseline](#phase-10-interoperability-baseline)
        * [Deliverables](#deliverables)
        * [Development Schedule](#development-schedule)
            * [Figure 2: Phase 1.0 Gantt Chart](#figure-2-phase-10-gantt-chart)
        * [Estimated Budget (Phase 1.0)](#estimated-budget-phase-10)
    * [Phase 1.1: Blockstore](#phase-12-blockstore)
        * [Deliverables](#deliverables-1)
        * [Development Schedule](#development-schedule-1)
            * [Figure 3: Phase 1.1 Gantt Chart](#figure-3-phase-11-gantt-chart)
        * [Estimated Budget (Phase 1.1)](#estimated-budget-phase-11)
    * [Phase 2 and Onward](#phase-2-and-onward)

## Project Description

### Summary

The following proposal details our project plan for the delivery of Rust IPFS. In deciding
which pieces of IPFS functionality to tackle first, we focused on a pair of end use cases:

1. Applications that leverage IPLD, such as OrbitDB and other types of event sourcing
2. Gateway nodes, which enrich the network by making public content more accessible

In preparation for this, the team researched the existing community contributions and, by
way of a diligent gap analysis, have charted out the path to delivery. During execution,
the team will use a very simple metric to report progress: the number of HTTP endpoints
implemented.

After development is complete, Equilibrium Labs has offered to steward the project, which
will provide necessary stability, and survive the previous work of others. This should
significantly boost community morale.

### Value

The Rust programming language has a dual value in both its feature set and its community.

A viable Rust implementation of IPFS would:

* Bring greater exposure to IPFS within the Rust community
    * Publicity opportunities at Rust-themed events such as conferences and meetups
    * Exposure to C and other APIs via Foreign Function Interfaces (FFIs)
* Enable additional opportunities in the embedded firmware and resource constrained spaces, which opens the door to things like IoT, automotive, industrial, and wearable devices
    * See the [Awesome Embedded Rust](https://github.com/rust-embedded/awesome-embedded-rust) list for some examples
* Enable additional opportunities in the WebAssembly space

### Survey of Community Efforts

The IPFS and Rust communities together have done an astounding job putting together
these projects. By thoroughly leveraging these community efforts we can save some
of time and money while fostering community morale and inclusion.

#### LibP2P + Pubsub

| Feature | Implemented? If so, where? | Notes |
| ---- | --------- | ------- |
| secio | [rust-libp2p #1413](https://github.com/libp2p/rust-libp2p/pull/1413) | Fast moving, recently ed25519 compatible |
| protocol selection: yamux or mplex multiplexing | [rust-libp2p](https://github.com/libp2p/rust-libp2p/tree/master/muxers) | | 
| DHT | [rust-libp2p](https://github.com/libp2p/rust-libp2p/tree/master/protocols/kad) | cannot comment  at this time on completeness or interoperability |
| floodsub | [rust-libp2p #1395](https://github.com/libp2p/rust-libp2p/pull/1395) | |
| gossipsub | [rust-libp2p #898](https://github.com/libp2p/rust-libp2p/pull/898) | |
| QUIC Support | Ongoing |[rust-libp2p #1334](https://github.com/libp2p/rust-libp2p/pull/1334) | 
| swarm management (id, ping) | [rust-ipfs](https://github.com/ipfs-rust/rust-ipfs/) | |
| differences in aes-ctr | [rust-libp2p #1242](https://github.com/libp2p/rust-libp2p/pull/1242) | [Pending PR](https://github.com/RustCrypto/stream-ciphers/pull/75) |


#### IPFS DAG / IPLD

| Feature | Implemented? If so, where? | Notes |
| ---- | --------- | ------- |
| dag-pb + dag-cbor | Custom version of [`rust-cbor`](https://github.com/dvc94ch/rust-cbor) crate | Implements a unifying abstraction on top of [rust-protobuf] and [rust-ipld]. |
| protobuf encoding and decoding | [rust-protobuf], [quick-protobuf], [prost!] | very mature |
| JSON serialization / deserialization | [pyfisch/cbor](https://github.com/pyfisch/cbor), with issues. (See next item) | Can be considered mature with [serde_json], yet supporting dag-json will still need work |
| CBOR tag Support | Ongoing | Problematic as tags appear in formats which are essentially a supersets of JSON, like CBOR. However, [pyfisch/cbori #172](https://github.com/pyfisch/cbor/pull/172) was recently merged, which @vmx is building off of |
| IPLD Selectors | Missing | Our understanding is that @vmx intends to implement the more advanced features of IPLD in the near future. | 

#### IPFS Blockstore

| Feature | Implemented? If so, where? | Notes |
| ---- | --------- | ------- |
| Rocksdb + filesystem based store | [rust-ipfs](https://github.com/ipfs-rust/rust-ipfs/) | Working |
| Other / Pluggable store | n/a | Multiple existing key-value store solutions randing from wrappers of databases written in different languages to fully rust solutions |

#### Bitswap

| Feature | Implemented? If so, where? | Notes |
| ---- | --------- | ------- |
| Bitswap | [rust-ipfs](https://github.com/ipfs-rust/rust-ipfs/) | This been tested to exchange block with go-ipfs 0.4.22 and an older rust-libp2p but may need updates to comply with spec |


#### HTTP

| Feature | Implemented? If so, where? | Notes |
| ---- | --------- | ------- |
| HTTP Bindings | Not implemented. | The "async story" of Rust enabling for example high performance web services is still evolving at great speed but there exists some longer running projects enabling the building of HTTP API as is required to enable testing such as [warp](https://github.com/seanmonstar/warp). | 



#### What is missing?

- What is definitely missing is support for IPLD selectors on one account of
their [spec](https://github.com/ipld/specs/blob/master/selectors/selectors.md)
is still in draft status. The functionality required by `ipfs dag get` has been
at least partially implemented already in [rust-ipfs]. The existing attempts
are expected to evolve and will be considered to be used and extended, which
ever looks most promising at the start of the project. 
- HTTP Bindings
    - [ferriseng/rust-ipfs-api](https://docs.rs/ipfs-api/0.6.0-rc/ipfs_api/) provides an HTTP API _client_ in Rust, but no server yet exists.
- Pluggable blockstore (sled, lmdb, etc)
- Bitswap up to spec

[rust-ipfs]: https://github.com/ipfs-rust/rust-ipfs/
[rust-protobuf]: https://github.com/stepancheg/rust-protobuf
[rust-ipld]: https://github.com/ipfs-rust/rust-ipld
[rust-ipld-collections]: https://github.com/ipfs-rust/rust-ipld-collections/
[quick-protobuf]: https://github.com/tafia/quick-protobuf
[prost!]: https://github.com/danburkert/prost
[vmx/rust-ipld]: https://github.com/vmx/rust-ipld
[serde_json]: https://github.com/serde-rs/json

### Maintenance and Upgrade Plan

We want to make a codebase that will last into the future. Equilibrium Labs and MRH.io,
along with the support of the community, pledge to continue to maintain the Rust IPFS
to best of their ability and within any financial constraints that exist.

Much like we will build upon community efforts, we will also enable and encourage others
to build upon our work. This will be a two-fold effort that includes both permissive
licensing and community outreach:  onboarding as many new contributors as possible,
mapping the work out into issues of different levels of difficulty, and providing mentorship.

### Figure 1. Risk Assessment

![IPFS Rust Risk Assessment](./media/fig1-ipfs-rust-risk-assessment.png)

### Project Team

| Mark Henderson | Joonas Koivunen | TBD |
| --- | --- | ---- |
| <img src="https://avatars1.githubusercontent.com/u/106148?s=256&v=4" /> | <img src="https://avatars1.githubusercontent.com/u/1081634?s=256&v=4" /> | <img src="https://avatars2.githubusercontent.com/u/48832938?s=256&v=4"> |
| Rust Developer, Project Manager | Rust Developer | Rust Developer |
| [+github](https://github.com/aphelionz) [+website](https://mrh.io) [+resume](https://ipfs.io/ipfs/QmcHxD94cvJgq5ZZxQkEi7SRMwD5dBnkhQ3zzaVFqNWFJb) | [+github](https://github.com/koivunej) [+linkedin](https://www.linkedin.com/in/joonas-koivunen-70273412/) | |
| Core contributor, OrbitDB. Implemented an [Ambients Protocol parser/compiler](https://github.com/aphelionz/ambients) in Rust | Current rust-ipfs contributor + Rust-lang tooling contributor + experience with database implementations in Rust | A qualified Rust Developer to be provided by Equilibrium Labs |



## Project Plan

### Summary

We propose a phased approach, with each deliverable building on the last while still
itself being comprehensive, usable software that the community can build upon and
continue to build. The phases are designed to fit cleanly within quarters of the year,
starting partway through Q1 2020.

#### Q1 2020

Phase 1.0:

- Initial Interoperability Report
- HTTP endpoint scaffolding (with 501 not implemented default)

This quick phase sets the baseline for interoperability testing. At this point we expect
that most, if not all, tests will fail with a `501 NOT IMPLEMENTED` error. This will become
the key metric of progress on the project.

Phase 1.1:

- Blockstore implementation
- HTTP endpoints for at least blockstore and pubsub

From there, we will begin the shortest path to enabling IPLD applications to be written in Rust.
Choosing and building (or building upon) a blockstore implementation, followed by enabling several
HTTP endpoints.

Existing community work will be extremely beneficial to this stage, as many HTTP endpoints
can likely be enabled by writing simple wrapper code around existing crates.

#### Q2 2020

Phase 2.0:

- TBD

The goal of Phase 2, at the time of this writing, is IPFS Gateway functionality, allowing for
swarming and content sharing. We've marked this phase highly TBD due to a rapidly changing
ecosystem.

### Implementation Details

#### IPLD

Minimum IPLD support will be required for existing `ipfs dag get` and `ipfs dag put`
functionality, including but likely not limited to:

* Default: Transcoding from JSON to CBOR
* Both CBOR and JSON: canonicalization (open discussion in [ipld/specs#236](https://github.com/ipld/specs/pull/236))
* Support “paths” to navigate the DAG
    * CBOR, JSON: Link can be resolved from any value
    * CBOR, JSON: Paths can resolve to documents
    * Protobuf: Links are named top level values (assumed to be used with UnixFSv1.x only)
    * Protobuf: Paths can resolve to documents only

Following the progress of  `go-graphsync` the IPLD support will need to be extended to

* Parsing IPLD selectors as transferred by Graphsync (CBOR)
* Depth-first walking according to the selector (inter-document and over links), providing support for recording the loaded blocks during walk
    * `ipfs dag resolve` has been proposed to demonstrate and test this functionality
* Traversals in all formats (CBOR, JSON, Protobuf)

This would give a solid foundation to implement Graphsync on top of these services in a later phase.

#### LibP2P

Many functions that IPFS rely on are wrappers around libp2p functions. These are:

* `ipfs swarm *`
* `ipfs pubsub *`

### Metric: Number of HTTP Endpoints Implemented

There are roughly 153 HTTP API endpoints that a typical IPFS implementation exposes.
While there are a number of other metrics we could choose to suitably track progress, “How
many endpoints have been implemented in Rust so far?” is an easy question to ask.

This proposal covers about 80 commands, with a number being deemed out of scope. See Figure 4
at the end of the document for a breakdown of which commands fall under which project phase,
and Out of Scope Commands for a list out of scope commands.

**Note:** Throughout the proposal, we will refer to commands using either the URL path or the
CLI represntation of the command, and they should be thought of as interchangable. For example
`/api/v0/add` will be referred to as `ipfs add` or simply `add`.

### Definition of Done

Our definition of done aims to be as robust as our KPI is simple. Each command will be considered done when the following requirements are met:

1. There is a working Rust implementation of the command’s functionality
    1. Code is “linted” i.e. code formatting via rustfmt and language idioms via clippy
2. There is an HTTP binding for said command exposed via the IPFS daemon
3. (Optional) There is a CLI command that utilizes either the Rust APIs or the HTTP APIs
4. There are functional and/or unit tests written, and they are passing
5. There is suitable documentation. In our case, this means:
    1. Each command has a usage example and API specification
    2. Top-level commands with subcommands display usage instructions
    3. Rustdoc tests are passing on all code-level comments
    4. Differences between Rust’s implementation and Go or JS are explained
6. There are passing conformance tests, approved by Protocol Labs

### Out of Scope

The commands listed below are deemed out of scope for this proposal, and will not be
included as part of the Rust IPFS implementation work done within.

The following commands are simply not required by our use case:
* `ipfs cid`
* `ipfs diag cmds`
* `ipfs files *`
* `ipfs key { gen, list, rename, rm }`
* `ipfs mount`
* `ipfs p2p`
* `ipfs shutdown`
* `ipfs stats bitswap`
* `ipfs swarm filters`
* `ipfs tar { add, cat }`
* `ipfs bootstrap { add, rm }`
* `ipfs config { profile, replace }`

The following commands are experimental:
* `ipfs filestore { dups, ls, verify }`
* `ipfs urlstore { add }`

The following commands are or will be deprecated:
* `ipfs file { ls }`
* `ipfs object { data, diff, ... }`

Additionally:
* ipfs update will likely be handled by cargo install
* Private network support via a swarm key is out of scope.

### Phase 1.0 Interoperability Baseline

Phase 1.0 covers project setup, and a baseline conformance test / interoperability report.

#### Deliverables

1. Project Setup
    1. Git Repository Setup
    2. Crate + Subcrate Structures
    3. CI/CD
2. Conformance testing via js-ipfsd-ctl, interface-js-ipfs-core
    1. Conformance Report
3. Interoperability testing via ipfs/interop
    1. Interop Report
4. Project Milestone Report

#### Development Schedule

Development will take place over an estimated 3-4 weeks of development. The following chart
assumes a week 8 start date (Feb 17). We can be flexible in terms of start dates, however
starting as soon as possible is preferable due to the above risk assessment.


##### Figure 2. Phase 1.0 Gantt Chart

![Phase 1.0 Gantt Chart](./media/phase-1-0-gantt.png)

_All figures are estimates._

#### Estimated Budget (Phase 1.0)

|  | Number of Hours | Hourly Rate | Total (Euros) | Total (USD) |
| --- | ---- | ---- | ---- | --- |
| Software Development and Project Management | 164 hours | 120€ | 19,680€ | $21,832.01 |

### Phase 1.2: IPLD Application Support

Phase 1.2 will complete the work started in Phase 1.1, fully enabling IPLD application
support via Rust crate functions, the HTTP API, as well as CLI commands.

#### Deliverables

1. Blockstore Implementation 
2. Bitswap testing and bug fixes
3. [Definition of Done](#definition-of-done) for:
    1. `/pubsub/*`
    2. `/swarm/*`
    3. `/version`
    4. `/id`
    5. `/block/*`
    6. `/dag/*`
    7. `/refs/*`
    8. `/bitswap/*`
4. Project Milestone Report
    1. Updated Conformance Tests
    2. Updated Interop Tests

Here, the community work will have its chance to shine - `libp2p` and `rust-ipld` in particular.

#### Development Schedule

Development will take place over an estimated 4 weeks of development. The following chart
assumes a week 9 start date (Feb 24).

##### Figure 2. Phase 1.1 Gantt Chart

![Phase 1.1 Gantt Chart](./media/phase-1-1-gantt.png)

_All figures are estimates._

#### Estimated Budget (Phase 1.2)

|  | Number of Hours | Hourly Rate | Total (Euros) | Total (USD) |
| --- | ---- | ---- | ---- | --- |
| Software Development and Project Management | 224 hours | 120€ | 26,880€ | $29,819.33 |

### Phase 2 and Onward

At this point, it's likely that the landscape will have changed such that we can't sufficiently
scope or estimate work meaningfully. We'd like to treat Phase 2 and onward as TBD, with the
intent of scoping and estimating the following work over time, as we move through Phase 1
and Phase 2.

That being said: This phase would contain the minimum viable feature set within rust-ipfs to
allow it to peer and share data with an existing go-ipfs or js-ipfs node, or perhaps even a
public gateway.

#### Potential Deliverable Ideas

1. Definition of Done for remaining endpoints
2. CLI bindings
3. Flagship Rust IPFS Public Gateway Production Deployment
4. Performance and resource utilization tuning for resource-constrained devices like the Pi Zero
5. Benchmarking using existing IPLD projects such as OrbitDB
