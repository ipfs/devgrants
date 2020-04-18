<h1>
  <img src="https://ipfs.io/ipfs/QmRcFsCvTgGrB52UGpp9P2bSDmnYNTAATdRf4NBj8SKf77/rust-ipfs-logo-256w.png" width="128" /><br />
  Rust IPFS: Phase 1.2 Milestone Report
</h1>

The IPFS Rust team completed Phase 1.2 roughly one week after the estimated time, due both in part to residual governance issues as well as some unforseen complications. In spite of the delay, everything proposed in original grant is now delivered.

The following activities were completed:

- [HTTP endpoints](#http-endpoints).
    - [`/block`](#block)
    - [`/dag`](#dag)
    - [`/refs/*`](#refs)
    - [`/bitswap/*`](#bitswap)
- [Miscellaneous](#miscellaneous) bug fixes and small refactors
- [Interface Test Refactoring](#interface-test-refactoring), which was required for certain tests
- [Conformance testing](#conformance-testing)
- [Governance](#governance) discussions took place, and some decisions were made

## HTTP Endpoints

### /block

The grant team successfully implemented the [`/block`](https://github.com/ipfs-rust/rust-ipfs/issues/90) endpoint suite.

For now we treat all CIDs as V1 internally, [upgrading them on the way in](https://github.com/ipfs-rust/rust-ipfs/blob/master/src/repo/mod.rs#L119) and only performing the conversion back to V0 if requested or in special cases, e.g. [`refs/local`](https://github.com/ipfs-rust/rust-ipfs/pull/160).

Relevant pull requests:
- [Foundational work](https://github.com/ipfs-rust/rust-ipfs/pull/137)
- [Implements V0 <--> V1 Conversion](https://github.com/ipfs-rust/rust-ipfs/pull/158)
- [`/block/rm`](https://github.com/ipfs-rust/rust-ipfs/pull/153)

### /dag

The grant team successfully implemented the [`/dag`](https://github.com/ipfs-rust/rust-ipfs/issues/91) endpoint suite.

A large amount of knowlege has been gained specifically in the area of Ipld path walking, with a by-product of varying approaches in the codebase, each with different properties, features, and use cases. We'd like to narrow those down and would seek Protocol Lab's guidance in coming together with a cohesive approach.

Relevant pull requests:
- [`/dag/put`](https://github.com/ipfs-rust/rust-ipfs/pull/137) and [fix](https://github.com/ipfs-rust/rust-ipfs/pull/157)
- [`dag/resolve`](https://github.com/ipfs-rust/rust-ipfs/pull/158)

### /refs

The grant team successfully implemented the [`/refs`](https://github.com/ipfs-rust/rust-ipfs/issues/92) endpoint suite. 

Please note the _necessary_ usage of [`unsafe`](https://github.com/ipfs-rust/rust-ipfs/blob/master/http/src/v0/support/unshared.rs#L36) here is due to a compiler bug. This well documented in the code with links to the [hyper](https://github.com/hyperium/hyper/issues/2159), [Rust internals](https://internals.rust-lang.org/t/what-shall-sync-mean-across-an-await/12020), and [async-trait](https://github.com/dtolnay/async-trait/issues/77) issues. Once the compiler bug is fixed, this issue should go away. The warp framework does not share mutable state in its responses. so a "real" problem arising here is very, very unlikely.

Relevant pull requests:
- [`/refs`](https://github.com/ipfs-rust/rust-ipfs/pull/147)
- [`/refs/local`](https://github.com/ipfs-rust/rust-ipfs/pull/150)

### /bitswap

The grant team successfully implemented the [`/bitswap`](https://github.com/ipfs-rust/rust-ipfs/issues/93) endpoint suite. Overall this was straightforward. Also note that the bitswap crate is currently a refactoring candidate, with a [number of discussion issues](https://github.com/ipfs-rust/rust-ipfs/issues?q=is%3Aopen+is%3Aissue+label%3Abitswap+label%3Arefactoring) arising as to its purpose and approach. PL's guidance would be helpful here as well.

Relevant pull requests:
- [`/bitswap`](https://github.com/ipfs-rust/rust-ipfs/pull/131)

## Miscellaneous

Relevant pull requests:
- [Subscription deadlocks](https://github.com/ipfs-rust/rust-ipfs/pull/130) were discovered and fixed
- [Flaky tests](https://github.com/ipfs-rust/rust-ipfs/pull/133) were fixed
- The [domain](https://github.com/ipfs-rust/rust-ipfs/pull/151) crate is slightly outdated, so it was pinned to a specific commit
- Small refactor to [remove some `&mut`s](https://github.com/ipfs-rust/rust-ipfs/pull/155) from the codebase
- [`clippy --workspace --tests --examples`](https://github.com/ipfs-rust/rust-ipfs/pull/156) was added to CI, and the resultant [clippy warnings](https://github.com/ipfs-rust/rust-ipfs/pull/159) were dealt with

## Interface Test Refactoring

It was discovered during this effort that many of the interface and interop tests use a diversity of APIs, not just the ones being tested, i.e. `ipfs.add` is used in the `refs.local` tests. With the philosophy that the tests should utilize "lower-level" APIs such as `ipfs.block.put`.

As part of this work, a number of PRs were made to js-ipfs, two of which have already been merged:
- [ipfs/js-ipfs#2980](https://github.com/ipfs/js-ipfs/pull/2980)
- [ipfs/js-ipfs#2983](https://github.com/ipfs/js-ipfs/pull/2983)
- [ipfs/js-ipfs#2972](https://github.com/ipfs/js-ipfs/pull/2972)
- [ipfs/js-ipfs#2982](https://github.com/ipfs/js-ipfs/pull/2982)

## Conformance Testing

### Interface

The grant team is happy to report that **102 interface tests now pass** on the latest build of Rust IPFS.

The roster of supported endpoints now includes:

* `/pubsub/{ publish, subscribe, unsubscribe, peers, ls }`
* `/swarm/{connect, peers, addrs, localAddrs, disconnect }`
* `/id`
* `/version`
* `/stop`
* `/block{ get, add, rm, stat }`
* `/dag{ get, put, resolve }`
* `/refs` and `/refs/local`
* `/bitswap/{ stat, wantlist }`

### Interop

Interop tests also use APIs unsupported by Rust IPFS such as `ipfs.add`. However, now, given the progress made on the interface test refactoring, it seems possible to refactor interop in the same way and gain that much more coverage and compatibility between the different language implementations.

## Governance

Governance was challenging during the grant cycle, perhaps due to the project being somewhat in its infancy. Things have stabilized but there is still a risk of it threatening future productivity if [more interpersonal issues](https://github.com/ipfs-rust/rust-ipfs/issues/129) arise. At this time, nobody from the grant team or PL have "Owner" access of the organization.

Despite this, some breakthroughs and decisions were made, primary in the form of productive discussions in the following issues:
- [Repo abstraction redesign](https://github.com/ipfs-rust/rust-ipfs/issues/142)
- [Error handling alternatives](https://github.com/ipfs-rust/rust-ipfs/issues/144)
- [Overall architecture discussion](https://github.com/ipfs-rust/rust-ipfs/issues/136)

The repository has [424 stars](https://github.com/ipfs-rust/rust-ipfs/stargazers) at the time of this writing.

Mark (@aphelionz) from the Rust IPFS team has attended four IPFS Core Implementation calls.
