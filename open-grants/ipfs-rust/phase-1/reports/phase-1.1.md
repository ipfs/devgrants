<h1>
  <img src="https://ipfs.io/ipfs/QmRcFsCvTgGrB52UGpp9P2bSDmnYNTAATdRf4NBj8SKf77/rust-ipfs-logo-256w.png" width="128" /><br />
  Rust IPFS: Phase 1.1 Milestone Report
</h1>

The IPFS Rust team completed Phase 1.1 one day behind schedule, despite adverse internal and external conditions that threatened to push the project back over one week. The following activities were completed:

- [HTTP endpoints](#http-endpoints).
    - [`/version`](#version)
    - [`/id`](#id)
    - [`/swarm/*`](#swarm)
    - [`/pubsub/*`](#pubsub)
- [Blockstore](#blockstore) research was conducted and deferred until whenever, wherever
- [Miscellaneous](#miscellaneous) Updates and Bug Fixes 
- [Conformance testing](#conformance-testing)
- Various [community activities](#community-activities) outside of the grant scope

## HTTP Endpoints

### /version

The grant team completed functionality for the [`/version` endpoint](https://github.com/ipfs-rust/rust-ipfs/issues/78), both the plaintext `/version` and the `/api/v0/version` that accepts arguments. See the [pull request](https://github.com/ipfs-rust/rust-ipfs/pull/85) here.

### /id

The grant team completed functionality for the [`/id` endpoint](https://github.com/ipfs-rust/rust-ipfs/issues/79), which returns identifying information about the user's peer. Note that identifying another peer required additional work that was unforseen by the grant team at planning time, and was [pushed to Phase 1.2](https://github.com/ipfs-rust/rust-ipfs/issues/121).

### /swarm

The grant team completed functionality for the [`/swarm` endpoints](https://github.com/ipfs-rust/rust-ipfs/issues/77), We discovered cases involving [multiaddrs with peer ids](https://github.com/ipfs-rust/rust-ipfs/issues/105), which we will address in Phase 1.2.

### /pubsub

The grant team completed the work on the [pubsub functionality](https://github.com/ipfs-rust/rust-ipfs/pull/118) and [HTTP bindings](https://github.com/ipfs-rust/rust-ipfs/pull/118) .Please note the [discrepancy](https://github.com/ipfs-rust/rust-ipfs/issues/76#issuecomment-604053881) between how the `go-ipfs` client and `js-ipfs` client send pubsub messages.

## Blockstore

Rust IPFS currently has three features that lend itself to expanding into a fully-fledged, highly performant blockstore:

1. The [`BlockStore`](https://github.com/eqlabs/rust-ipfs/blob/cb664e11f8ec2f4700e860bee2da95de36df6662/src/repo/mod.rs#L51) trait
2. An in-memory store
3. A rudimentary filestore.

The grant team had originally planned to follow latest developments within `go-ipfs` and `js-ipfs` and innovate, as [requested by @stebalien](https://github.com/ipfs-rust/rust-ipfs/issues/84). However, we quickly learned certain architectural decisions are [pending within `ipfs/specs`](https://github.com/ipfs/specs/issues/242), so we postponed any work on the `BlockStore` until those decisions were made.

This was fortunate, because it allowed us to focus solely on the libp2p integration during this phase, which was certainly a lift in terms of development effort.

## Miscellaneous

- [In memory config](https://github.com/ipfs-rust/rust-ipfs/pull/113) for easier testing: 
- Fixing [crate names](https://github.com/ipfs-rust/rust-ipfs/pull/106)

## Conformance Testing

### Interface

The grant team is happy to report that [31 interface tests now pass](https://github.com/ipfs-rust/ipfs-rust-conformance/actions/runs/63502176) on the latest build of Rust IPFS.

The roster of supported endpoints now includes:

* `/pubsub/{ publish, subscribe, unsubscribe, peers, ls }`
* `/swarm/{connect, peers, addrs, localAddrs, disconnect }`
* `/id`
* `/version`
* `/stop`

### Interop

The grant team discovered that a number of the interop tests, as well as the conformance tests for Phase 1.2, use endpoints that are out of grant scope, primarily `ipfs.add`. PL helped us make the decisions to refactor the tests to use a more limiited set of APIs, which will make conformance easier in the long run. This will take place in Phase 1.2

## Community Activities

Matrix now bridges to a Telegram group called rust-ipfs.

The grant team submitted two [blog posts](https://github.com/ipfs-rust/rust-ipfs/issues/67) which seemed to be well received by the community.
- https://blog.ipfs.io/2020-03-18-announcing-rust-ipfs/
- https://medium.com/equilibriumco/announcing-rust-ipfs-af8358f90beb

The repository has [359 stars](https://github.com/ipfs-rust/rust-ipfs/stargazers) at the time of this writing.

Mark (@aphelionz) from the Rust IPFS team has attended two IPFS Core Implementation calls.
