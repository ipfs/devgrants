# Open Grant Proposal: Rust IPFS Phase 2
> Category: core-dev | Proposed by: Mark Henderson and Joonas Koivunen of [Equilibrium](https://equilibrium.co)

The goal of the [Rust IPFS Phase 1 devgrant](https://github.com/ipfs/devgrants/tree/master/open-grants/ipfs-rust)
was to allow developers to write IPLD applications. Since the approval and inception of the
grant work in Q1 2020, the grant team has delivered a Rust implementation with over a dozen HTTP
endpoints and over 100 passing conformance tests.

As such, we believe that IPLD application developers have what they need to start creating apps
that leverage the flexibility and connectivity of IPLD, along with the performance and reliability
of Rust.

However, without battle testing" Rust IPFS in the wild, we will miss opportunities to
gather insight and benchmarks into how it truly performs. Luckily, there's an easy use case to
reach for:

## Project Description

### Summary

The Rust IPFS grant team successfully completed Phase 1 of the
[Rust IPFS devgrant](https://github.com/ipfs/devgrants/tree/master/open-grants/ipfs-rust), and
plans to continue working towards a fully conformant Rust implementation of IPFS.

Next, we would implement UnixFS and the minimum-viable set of endpoints, determined to be
`/get`, and `/cat`. If time allows we may explore `/ls` as well.

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

As for Phase 2, the value of UnixFS would be the final pillar in the foundation allowing for use
cases such as low-resourced devices in IoT and embedded settings.

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

| Mark Henderson | Joonas Koivunen |
| -------------- | --------------- |
| <img src="https://avatars1.githubusercontent.com/u/106148?s=256&v=4" /> | <img src="https://avatars1.githubusercontent.com/u/1081634?s=256&v=4" /> |
| Rust Developer, Project Manager | Rust Developer |
| [+github](https://github.com/aphelionz) [+website](https://mrh.io) [+resume](https://ipfs.io/ipfs/QmcHxD94cvJgq5ZZxQkEi7SRMwD5dBnkhQ3zzaVFqNWFJb) | [+github](https://github.com/koivunej) [+linkedin](https://www.linkedin.com/in/joonas-koivunen-70273412/) |
| Core contributor, OrbitDB. Current rust-ipfs contributor. Implemented an [Ambients Protocol parser/compiler](https://github.com/aphelionz/ambients) in Rust | Current rust-ipfs contributor + Rust-lang tooling contributor + experience with database implementations in Rust |

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
the last.

* **Phase 2.0** will be time-boxed to 2 weeks and will add the necessary UnixFS support for
`/cat`, and `/get` endpoints. `/ls` may be added if time allows.

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

Finally, as mentioned above, we are trying out time-boxing for Phase 2.0.

### Implementation Details

#### Phase 2.0

UnixFSv1 support is necessary for many use cases. We will start with basic files (non-hamt
directories), supporting single-block directories and multi-block files with up to
[174 links](https://github.com/ipfs/specs/blob/master/UNIXFS.md#layout) per folder.
That will allow us to land `/get/` as well as `/cat`.

This will also be a time-boxed phase of two weeks. If time allows we will also add support for
the `/ls` endpoint, and perhaps others as suggested by PL.

### Success Metric
Previously we used
[HTTP endpoints](https://github.com/ipfs/devgrants/tree/master/open-grants/ipfs-rust#metric-number-of-http-endpoints-implemented)
implemented as the key performance indicator. Given the lessons learned from Phase 1, we’d like
to stick closely to this, but change the metric slightly to **passing conformance tests**
for endpoints.

As of the writing of this proposal, the grant team's work passes 102 conformance tests. Analysis of
the conformance tests that cover Phase 2's endpoints suggest there could be well over 135 passing
tests by the end of this grant cycle.

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
| Software Development and Project Management | 70 hours | 120€ | 8.400€ | $9096.11 |
