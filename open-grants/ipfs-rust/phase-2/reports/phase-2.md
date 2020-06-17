<h1>
  <img src="https://ipfs.io/ipfs/QmRcFsCvTgGrB52UGpp9P2bSDmnYNTAATdRf4NBj8SKf77/rust-ipfs-logo-256w.png" width="128" /><br />
  Rust IPFS: Phase 2 Milestone Report
</h1>

The IPFS Rust team completed Phase 2 roughly one week after the estimated time, simply due to inherent complexities in the large
feature set created. In spite of the delay, everything proposed in original grant is now delivered.

The following activities were completed:

- [ipfs_unixfs](#ipfs_unixfs-crate) crate
- [HTTP Endpoints](#http-endpoints).
    - [`/cat`](#get)
    - [`/get`](#cat)
- [Miscellaneous](#miscellaneous) bug fixes and upgrades
- [Interface Test Refactoring](#interface-test-refactoring), which was required for certain tests
- [Conformance Testing](#conformance-testing)
- [Test Coverage](#test-coverage)

## ipfs_unixfs crate

Following previous discussions on the repository issues, the grant team
started a new crate in the main repository called `ipfs_unixfs`, which was
designed so that it can be reused not only in `rust-ipfs` but in other
implementations as well. At the moment the implementation supports only the
work implemented in Phase 2 but we hope to grow its feature set in the coming months
to support `/add`, and more.

## HTTP Endpoints

### /cat

The grant team completed the functionality for the `/cat` endpoint. Work started
by first implementing initial support for walking file trees in order for the
content in ipfs-unixfs PR [#176] followed by the endpoint implementation in PR
[#184].

[#176]: https://github.com/rs-ipfs/rust-ipfs/pull/176
[#184]: https://github.com/rs-ipfs/rust-ipfs/pull/184

### /get

The grant team completed the functionality for the `/get` endpoint in PR [#189].
The pull request ended up large as a way to split the work between the
iterations could not be found. The pull request ended up addressing a number of
issues:

* cleanup of overall `ipfs-unixfs` structure
* traversing over UnixFs directories (plain and HAMT Sharded), symlinks and
  files (`/cat` feature)
* serving UnixFs content as `tar` at `/get` endpoint

[#189]: https://github.com/rs-ipfs/rust-ipfs/pull/189

# Miscellaneous

Relevant pull requests:

* [Upgrade to rust-libp2p 0.19]
* [Cache dependencies on Windows builds]
* [Removal of `unsafe` code through dependency upgrade]

[Upgrade to rust-libp2p 0.19]: https://github.com/rs-ipfs/rust-ipfs/pull/169
[Cache dependencies on Windows builds]: https://github.com/rs-ipfs/rust-ipfs/pull/180
[Removal of `unsafe` code through dependency upgrade]: https://github.com/rs-ipfs/rust-ipfs/pull/191

# Interface Test Refactoring

Continuing the work started in previous phases, the `ipfs.add` API use was replaced
in the tests for `/cat` and `/get`. This resulted in two PRs, one of which has
already been merged:

* https://github.com/ipfs/js-ipfs/pull/3078
* https://github.com/ipfs/js-ipfs/pull/3093

# Conformance Testing

## Interface

The grant team is happy to report that *121 interface tests now pass* on the
latest build of Rust IPFS.

The supported endpoints now includes:

* `/pubsub/{publish,subscribe,peers,ls}`
* `/swarm/{connect,peers,addrs,addrs/local,disconnect}`
* `/id`
* `/version`
* `/stop`
* `/block/{get,add,rm,stat}`
* `/dag/{get,put,resolve}`
* `/refs` and `/refs/local`
* `/bitswap/{stat,wantlist}`
* `/cat`
* `/get`

## Automation

The grant team has been running conformance tests on CI since PR [#98] was merged
at near the beginning of Phase 2. Following testing PR [#24] we are now able to
maintain a patched version of the `interface-ipfs-core` package with our patches
to version we are currently basing the work on.

[#98]: https://github.com/rs-ipfs/rust-ipfs/pull/98
[#24]: https://github.com/rs-ipfs/ipfs-rust-conformance/pull/24

# Test Coverage

Before Phase 2 the line coverage as reported by
`cargo-tarpaulin` (latest version, latest rust toolchain) was 54%,
1926/3542 lines covered. After Phase 2 the coverage report stands at 57%
coverage, 3232/5653 lines covered. Calculating from the coverage report, over
2000 lines were added but still the overall coverage was **increased.**

The new crate, `ipfs-unixfs`, is compiled with different lint settings than
existing code, namely warnings on missing public element documentation has been
enabled. This has lead to the crate having at least minimal documentation and is
supported by two examples: `get` and `cat`, which demonstrate the crates use.
