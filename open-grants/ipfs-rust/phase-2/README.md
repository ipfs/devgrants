# Open Grant Proposal: Rust IPFS Phase 2
> Category: core-dev | Proposed by: Mark Henderson and Joonas Koivunen of [Equilibrium](https://equilibrium.co)

The goal of the [Rust IPFS Phase 1 devgrant](https://github.com/ipfs/devgrants/tree/master/open-grants/ipfs-rust)
was to allow developers to write IPLD applications. Since the approval and inception of the
grant work in Q1 2020, the grant team has delivered a Rust implementation with over a dozen HTTP
endpoints and over 100 passing conformance tests.

As such, we believe that IPLD application developers have what they need to start creating apps
that leverage the flexibility and connectivity of IPLD, along with the performance and reliability
of Rust.

However, without "battle testing" Rust IPFS in the wild, we will miss opportunities to
gather insight and benchmarks into how it truly performs. Luckily, there's an easy use case to
reach for:

**Public gateways**, which serve permaweb content through a URL that includes a CID, are often
the end user's first encounter with the distributed web. Accessing a version of
[Wikipedia's home page](https://ipfs.io/ipfs/bafybeiemxf5abjwjbikoz4mc3a3dla6ual3jsgpdr4cjr3oz3evfyavhwq/wiki/)
via a public gateway provides a familiar interface to a new and exciting world, and get people
excited about our shared, distributed future.

If funded this grant will deliver the _first Rust public gateway_, benchmark and test results from
the OrbitDB suite, as well as a handful of new endpoints and over 30 new passing conformance tests.

## Project Description

### Summary

The Rust IPFS grant team successfully completed Phase 1 of the [Rust IPFS devgrant], and plans
to continue working towards a fully conformant Rust implementation of IPFS. Phase 2’s primary
goal and use case would be IPFS gateway support.

We’d like to first start by hardening the project enough to publish to https://crates.io, the
official package repository for Rust. This would involve resolving our PRs in forked repositories,
ensuring that only released dependencies are used, and updating docs so they appear properly on
https://docs.rs.

From there, we would implement the minimum-viable set of endpoints necessary for a public gateway,
which the grant team determined to be `/get`, and `/cat`. If time allows we may explore `/ls` as
well.

From there, we would add `_dnslink` and basic config file support, as well as administrative
tooling like server monitoring and content reporting. Then we would add the `/ipfs` endpoint
for the gateway, and launch!

For more information on how the grant process has been going so far, please read the grant
reports for more information:
* [Phase 1.0](https://github.com/ipfs/devgrants/blob/master/open-grants/ipfs-rust/reports/phase-1.0.md)
* [Phase 1.1](https://github.com/ipfs/devgrants/blob/master/open-grants/ipfs-rust/reports/phase-1.1.md)
* [Phase 1.2](https://github.com/ipfs/devgrants/blob/master/open-grants/ipfs-rust/reports/phase-1.2.md)

### Value

The grant team has already brought both technical and administrative value to Rust IPFS. Since the
beginning of Phase 1, the team has:

* Implemented all planned endpoints
* Set up GitHub repositories according to both Github and PL community standards
* Applied continuous integration via GitHub Actions for tests, linting, and language idioms
* Published two blog posts, one on the
[IPFS blog](https://blog.ipfs.io/2020-03-18-announcing-rust-ipfs/) and the other on the
[Equilibrium blog](https://medium.com/equilibriumco/announcing-rust-ipfs-af8358f90beb)
leading to:
    * The number of stars on the repo growing by over 400, as well as:
    * Two separate community contributors lending their talents, unsolicited, to pull requests

Overall, the grant team has shown that they can meet milestones and deliverables,
even throughout internal, community-wide, external, and of course global challenges.

As for Phase 2, the value of a public IPFS gateway written in Rust is twofold:
1. It can serve as a reference implementation for others seeking to implement Rust IPFS
2. It can serve as a flagship for marketing and promotional purposes, something that both the
IPFS and the Rust communities can be proud of.

### Risk Assessment

Some of the risks from Phase 1 came to light, others did not. Still others that we
did not foresee occurred, making the progress challenging at times.

The grant team was able to mitigate many risks, and are in the process of mitigating the rest.
The following headings are what we see as the current landscape of risks as we move forward,
along with some basic rankings of likelihood and impact.

#### Reliance on rust-libp2p and its dependency chain

**Likelihood**: Certain<br />**Impact**: Medium/Low

Overall this risk was fairly mitigated, not causing too any practical issues over
the course of Phase 1. We made one required PR that was quickly merged. As we move through the list
of potential upstream features from `go-ipfs` 0.5.0 and beyond, this may require closer
collaboration with the `rust-libp2p` team.

#### Community efforts can move and change very fast

**Likelihood**: Medium/Low<br />**Impact**: Low

In the end, this was not as much of a risk as we had anticipated. In fact, the community seemed to
coalesce around `rust-ipfs`. For example, `ipfs-rust/rust-ipld` became the ad-hoc "official" IPLD
repository in Rust. We were not notified about any other critical work in the ecosystem during
Phase 1. We will continue to keep our eyes and ears out for any other meaningful community projects
during Phase 2.

#### The code could still “bit rot” even with community support

**Likelihood**: Low<br />**Impact**: Medium/Low

So far, so good. The code base and community are more active than ever. We plan on focusing more
heavily on community engagement and best practices around fostering a healthy open source project.

#### New implementation == greater attack surface for exploits

**Likelihood**: High<br />**Impact**: Medium

Focus so far has been on implementation, so undivided attention to security concerns was
unfortunately not available. For the time being, more documentation, testing, and benchmarking
will invariably lead to insights about security. Additionally, the project is still marked at
`Pre-Alpha`, so expectations are set rather low in terms of security.

#### Another implementation also means more known bugs

**Likelihood**: High<br />**Impact**: Medium/High

This risk can easily be turned into a benefit. While working towards the Phase 1 goals we've also
worked towards getting the known implementation differences fixed in ecosystem crates like
`aes-ctr`. Putting in the work to identify more of such issues through continued interoperability
testing (even if manual) will help the larger Rust ecosystem in future to interoperate with
Go and JS counterparts.

#### Kademlia Unknown Unknowns

**Likelihood**: High<br />**Impact**: High

In phase 1 we didn't get to implementing `/api/v0/id?arg=other_peer_id` or
`Ipfs::identify_other(&self, peer: PeerId)`. As a result we know very little of how the
`libp2p_kad` implementation works together with `{go,js}-ipfs`.

_This, coupled with the reliance on libp2p, poses the single largest risk to the project._

#### Open Source Governance

**Likelihood**: Medium/High<br />**Impact**: High

Open source governance is not easy, as it requires many “soft” skills outside of simple development
and engineering management. The grant team plans on working closely with Protocol Labs to ensure
that governance happens transparently, and that all interests can be represented fairly.

### Project Team

| Mark Henderson | Joonas Koivunen | Łukasz Jędrzejczyk |
| -------------- | --------------- | ------------------ |
| <img src="https://avatars1.githubusercontent.com/u/106148?s=256&v=4" /> | <img src="https://avatars1.githubusercontent.com/u/1081634?s=256&v=4" /> | <img src="https://avatars3.githubusercontent.com/u/3750347?s=460&u=ace834d0d6941c1470aaf36659a29019c4d55337&v=4"> |
| Rust Developer, Project Manager | Rust Developer | Rust Developer |
| [+github](https://github.com/aphelionz) [+website](https://mrh.io) [+resume](https://ipfs.io/ipfs/QmcHxD94cvJgq5ZZxQkEi7SRMwD5dBnkhQ3zzaVFqNWFJb) | [+github](https://github.com/koivunej) [+linkedin](https://www.linkedin.com/in/joonas-koivunen-70273412/) | [+github](https://github.com/ljedrz) [+linkedin](https://www.linkedin.com/in/ljedrz/) [+stackoverflow](https://stackoverflow.com/users/1870153/ljedrz) |
| Core contributor, OrbitDB. Current rust-ipfs contributor. Implemented an [Ambients Protocol parser/compiler](https://github.com/aphelionz/ambients) in Rust | Current rust-ipfs contributor + Rust-lang tooling contributor + experience with database implementations in Rust | Rust compiler contributor. Active Rust mentor on Stack Overflow. Wrote the `lambda_calculus` crate |

### Maintenance and Upgrade Plan

We want to make a code base that will last into the future. Equilibrium and MRH.io, along with the
support of the community, pledge to continue to maintain the Rust IPFS to the best of their ability
and within any financial constraints that exist.

Much like we will build upon community efforts, we will also enable and encourage others to build
upon our work. This will be a twofold effort that includes both permissive licensing and community
outreach: on-boarding as many new contributors as possible, mapping the work out into issues of
different levels of difficulty, and by providing mentoring.

## Project Plan

### Summary

The grant team will continue our phased approach, with each deliverable continuing to build upon
the last, culminating in the launch of the first Rust IPFS public gateway.

* **Phase 2.0** will be a time-boxed hardening phase, stabilizing the project to work towards
publishing to crates.io by adding tests, documentation, and performing necessary bug fixes and/or
refactoring to handle accumulated technical debt.
* **Phase 2.1** will begin work towards gateway support by adding the necessary UnixFS support in
`/cat`, and `/get` endpoints. `/ls` may be added if time allows.
* **Phase 2.2** will add basic configuration file support, `_dnslink` support, swarming with
bootstrap peers, and a denylist for reported content
* **Phase 2.3** will add the `/ipfs/` endpoint, and launch the server.

#### Updates to Project Management Processes

We had adopted and had success with the use of organization-wide GitHub projects, which allows us
a coordinated, high-level view of each grant phase. You can see the ipfs-rust projects here:
https://github.com/orgs/ipfs-rust/projects.

Additionally, instead of a gantt chart, we are opting for more roughly estimated timeline with
careful research done for each set of endpoints to properly scope out the requirements ahead of
implementation. An example of this is the
[block endpoint issue](https://github.com/ipfs-rust/rust-ipfs/issues/90), which combined a number
of documentation sources, tests, and independent investigation to determine conformance
requirements.

Finally, as mentioned above, we are trying out time-boxed phases for Phase 2.0 and 2.1,
prioritizing mission-critical deliverables and adding in more optional ones if we have the time.

### Implementation Details

#### Phase 2.0

The grant team has ownership of https://crates.io/crates/ipfs and plans on publishing there so
developers can use it in their Rust code, and so users can add `ipfs = "0.1.0"` to their Cargo.toml
file, or something similar. This will be a time-boxed phase of 2 weeks.

However, a few things stand in the way of publishing successfully.
- Need all dependencies to be properly released versions:
  - A forked versions `aes-ctr` crate need a PRs to be approved and merged
  - Latest versions of `rust-libp2p` and `aes-ctr` libraries need to be published to crates.io
  - `domain` could be replaced with `trust-dns`
- Activating the `interop` tests using the same refactoring techniques we applied for `interface`
- Documentation for the https://docs.rs website, then if time allows:
- Automated releases via the [`bors`](https://bors.tech/) GitHub bot
- Code Coverage via the `grcov` or `cargo-cov` tools
- Select benchmarks to set baselines for future refactoring.

We'd like to suggest utilizing the [OrbitDB](https://github.com/orbitdb) library for the benchmarks
via the HTTP API. This is due to the team's familiarity, and the fact that a large number of tests
and benchmarks already exist within OrbitDB's code base. Note that this may require creating a
scaffold `/key` endpoint, but that will not be a full implementation of the `/key` APIs.

#### Phase 2.1

UnixFSv1 support is necessary for gateway support. We will start with basic files (non-hamt
directories), supporting single-block directories and multi-block files with up to
[174 links](https://github.com/ipfs/specs/blob/master/UNIXFS.md#layout) per folder.
That will allow us to land `/get/` as well as `/cat`.

This will also be a time-boxed phase of two weeks. If time allows we will also add support for
the `/ls` endpoint, and perhaps others as suggested by PL.

#### Phase 2.2

The grant team will focus on three primary things during this phase, which will **not** be
time-boxed as all of the items here are mission-critical.

1. The foundations of `config` file support, namely the `Addresses.API`, `Addresses.Swarm`,
and `Bootstrap` configuration directives, allowing for basic configuration of a node or gateway.
2. `_dnslink` support so that people can:
    1. Point their `A` and `TXT` dns records to the gateway and host their websites on our node.
    2. Resolve IPFS paths such as `/ipns/domain.com/something`
3. The ability to swarm with designated bootstrap peers. This depends on dnsaddr with rust-libp2p,
so we will likely need to coordinate with the authors on that, or make another fork and PR.

Finally, since we will be hosting user content, we will need to support some sort of denylist
apparatus for reported content.

#### Phase 2.3

During the final phase of this grant cycle, the team will enable the `/ipfs` endpoint for the
gateway, and come up with a basic system for garbage collection. Then, Equilibrium will
choose an appropriate hosting platform, and launch!

### Success Metric
Previously we used
[HTTP endpoints](https://github.com/ipfs/devgrants/tree/master/open-grants/ipfs-rust#metric-number-of-http-endpoints-implemented)
implemented as the key performance indicator. Given the lessons learned from Phase 1, we’d like
to stick closely to this, but change the metric slightly to **passing conformance tests**
for endpoints.

As of the writing of this proposal, the grant team's work passes 102 conformance tests. Analysis of
the conformance tests that cover Phase 2's endpoints suggest there could be well over 135 passing
tests by the end of this grant cycle.

Additionally, we will define success of this grant cycle with a successful launch of a public
gateway that is capable of:

1. Resolving `/ipfs/[cid]`
2. Serving custom domains with `_dnslink`
3. Resolving `/ipns/[domain name]` via `_dnslink`

### Definition of Done
We had success with the definition of done used in Phase 1, and as such we will continue to use
it. Each command will be considered done when the following requirements are met:

1. There is a working Rust implementation of the command’s functionality
    1. Code is “linted” i.e. code formatting via rustfmt and language idioms via clippy
2. There is an HTTP binding for said command exposed via the IPFS daemon
3. There are functional and/or unit tests written, and they are passing
4. There is suitable documentation. In our case, this means:
   1. Each command has a usage example and API specification
   2. Top-level commands with subcommands display usage instructions
   3. Rustdoc tests are passing on all code-level comments
   4.  Differences between Rust’s implementation and Go or JS are explained
5.  There are passing conformance tests, approved by Protocol Labs

Note that we removed one item:
> *(Optional) There is a CLI command that utilizes either the Rust APIs or the HTTP APIs*

### Out of Scope

The following endpoints have been deemed out of scope for this proposal and will not be included in
Phase 2. The endpoints have been grouped by their respective reasonings for omission below.

The following commands require on-the-fly config changes, though we could potentially implement
the read-only versions such as `/config/show`:

- `/bootstrap`
- `/config`

Finally, the following endpoints are simply not required by our use case:
- `/stats`
- `/cid`
- `/diag`
- `/mount`
- `/p2p`
- `/swarm/filters`
- `/files` (regular and mfs)

The following endpoints are experimental:
- `/filestore`
- `/urlstore`

The following endpoints are or will be deprecated:
- `/file`
- `/object`

## Project Schedule


### Phase 2.0

Due to the fact that we can't _guarantee_ that the dependencies such as `libp2p` will be updated,
we cannot guarantee that we will publish to crates.io, but all of our effort will be focused on
that goal.

#### Deliverables (in order of prioritization)
1. Priority on released dependencies, cleaning up outstanding PRs from forked libraries.
2. Documentation for docs.rs.
3. Activate interop tests
4. bors + release CI.
5. Code coverage
6. OrbitDB Tests and benchmarking
7. Project milestone report
    1. Updated interop test results

#### Development Schedule
**This will be a time-boxed phase.** The work will be triaged and addressed by priority, getting
through as much work as we can in a two-week period. We can be flexible in terms of start dates,
however we would like to continue on the Rust IPFS work as soon as possible after Phase 1 is
completed to avoid any disruptions.

#### Estimated Budget (Phase 2.0)
|  | Number of Hours | Hourly Rate | Total (Euros) | Total (USD) |
| --- | ---- | ---- | ---- | --- |
| Software Development and Project Management | 140 hours | 120€ | 16,800€ | $18239.59 |

### Phase 2.1

The focus of this phase is UnixFSv1 support and the `/get` and `/cat` endpoints. See the
[implementation details](#implementation-details) section for more information.

#### Deliverables
1. UnixFSv1 support
2. `/get`
3. `/cat`
4. `/ls` if time allows
5. Project milestone report
    1. Interop and performance test results

#### Development Schedule
**This will be a time-boxed phase.** This is to ensure we don't go too far down the "rabbit hole"
of implementing UnixFS and the endpoint details. For example - `/get` requires `tar` support.

#### Estimated Budget
|  | Number of Hours | Hourly Rate | Total (Euros) | Total (USD) |
| --- | ---- | ---- | ---- | --- |
| Software Development and Project Management | 140 hours | 120€ | 16,800€ | $18239.59 |

### Phase 2.2

This phase continues gateway functionality development by adding basic configuration
directives as well as `_dnslink` support.

#### Deliverables
1. Configuration directive support
    1. `Addresses.API`
    2. `Addresses.Swarm`
    3. `Bootstrap`
2. `_dnslink` support
    1. Domains
    2. IPFS paths i.e. `/ipns/domain.com/something`
3. Denylist for reported content
4. Swarming with Bootstrap peers
5. Project milestone report

#### Development Schedule
This will not be a time-boxed phase, and we expect the work to take roughly 2-3 weeks.

#### Estimated Budget
|  | Number of Hours | Hourly Rate | Total (Euros) | Total (USD) |
| --- | ---- | ---- | ---- | --- |
| Software Development and Project Management | 170 hours | 120€ | 20,400€ | $22148.08 |

### Phase 2.3

This phase completes the gateway by adding the `/ipfs` endpoint, and launching the node!

#### Deliverables
1. `/ipfs/` endpoint
2. Stale Content Removal
3. Hosting Considerations (logging, monitoring, volume resizing, etc)
4. Public Gateway Launch
5. Project final report

#### Development Schedule
This will not be a time-boxed phase, and we expect the work to take roughly 1-2 weeks.

#### Estimated Budget
|  | Number of Hours | Hourly Rate | Total (Euros) | Total (USD) |
| --- | ---- | ---- | ---- | --- |
| Software Development and Project Management | 80 hours | 120€ | 9,600€ | $10422.62 |
