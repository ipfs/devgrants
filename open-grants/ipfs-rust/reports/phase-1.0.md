<h1>
  <img src="https://ipfs.io/ipfs/QmRcFsCvTgGrB52UGpp9P2bSDmnYNTAATdRf4NBj8SKf77/rust-ipfs-logo-256w.png" width="128" /><br />
  Rust IPFS: Phase 1.0 Milestone Report
</h1>

The IPFS Rust grant team completed Phase 1.0 on schedule. The following activities were initially scoped and planned: 

- [Project Setup](#project-setup) incl. Git repositories, code organization, and continuous integration
- [HTTP Scaffolding](#http-scaffolding) with `501 NOT IMPLEMENTED` boilerplate
- [Conformance Testing](#conformance-testing)
- [Interoperability Testing](#interoperability-testing)
    
In addition to completing the above, we completed a number of community related efforts. Protocol Labs created a logo (above), Equilibrium created a mascot (below), and we, together, set up bridged chat between [Matrix](https://riot.im/app/#/room/#rust-ipfs:matrix.org) and [Discord](https://discord.gg/9E5SFvW).

# Activity Details

Each heading below represents a specific item promised in the initial grant proposal and relevant notes.

## Project Setup

Goal: Quality of repository administration (as opposed to code quality)

### Git Repositories

We chose the Standard Readme spec. For example, see the [ipfs-rust](ttps://github.com/ipfs-rust/rust-ipfs/pull/72
) and [ipfs-rust-conformance](https://github.com/ipfs-rust/ipfs-rust-conformance/issues/11) READMEs. We also wrote a [Contributors guide](https://github.com/ipfs-rust/rust-ipfs/issues/61) and added it to the repo, along with [issue and pull request templates](https://github.com/ipfs-rust/rust-ipfs/pull/74). According to GitHub's "Community profile", we have achieved a "green" status.

Finally, we also applied the [IPFS Community code of conduct](https://github.com/ipfs-rust/rust-ipfs/pull/68) following permission from Protocol Labs.

### Code Organization

We organized the repositories according to the following list. Indentation implies creating crates within subfolders, and importing them via the [Rust module system](https://doc.rust-lang.org/book/second-edition/ch07-00-modules.html).

- rust-ipfs
    - http
    - bitswap
- rust-ipld

### Continuous Integration (CI)

We achieve much of the "definition of done" in this step.

We set up [automated CI](https://github.com/ipfs-rust/rust-ipfs/pull/69), running on pushes to pull requested branches and master, on `rust-ipfs` and `rust-ipld`. The tests assert a [number of properties](https://github.com/ipfs-rust/rust-ipfs/issues/62), including unit tests, functional test, code linting and formatting and language idioms via "clippy". The rests even try and execute the examples in the README files via a tool called [skeptic](https://github.com/ipfs-rust/rust-ipfs/issues/41).

Note that in one instance Rust's `stable` release channel updated from 1.41 to 1.42, eschewing 32 bit iOS / OSX builds, and we were able to catch that and [fix it](https://github.com/ipfs-rust/rust-ipfs/pull/100) that day.

## HTTP Scaffolding

The grant team used the [warp](https://github.com/seanmonstar/warp) Rust framework to scaffold [HTTP endpoints](https://github.com/ipfs-rust/rust-ipfs/issues/60) for conformance testing. This involved creating a long-standing process, and then responding to HTTP calls among specific paths to return the `501 NOT IMPLEMENTED` error code, as opposed to `404 NOT FOUND`.

The grant team ensured that [all HTTP endpoints](https://github.com/ipfs-rust/rust-ipfs/blob/master/http/src/v0.rs#L30) covered by the `interface-js-ipfs-core` tests were appropriately scaffolded.

## Conformance Testing

The grant team's goal was simply to Simply being able to _run_ the tests against our setup. This involved both adding functionality to `rust-ipfs` as well as

We created [`npm-rust-ipfs-dep`](https://github.com/ipfs-rust/npm-rust-ipfs-dep/issues/1) which mirrors `npm-go-ipfs-dep`, allowing for the Rust IPFS executable to be installed as an npm dependency. From there we made [small edits](https://github.com/ipfs/js-ipfsd-ctl/pull/473) to `js-ipfsd-ctl`, and then 

We also edited the `interop` tests in a [similar fashion](https://github.com/ipfs-rust/interop/pull/2).

Currently all conformance testing, interface and interop, fail. This is intentional as grant progress can now be measured in the ratio of passing/failing tests moving forward.

# What's Next?

Phase 1.1 plans to introduce new HTTP endpoints, /pubsub, /swarm, /version, and /id, all of which will pass conformance testing standards. Additionally, we plan to expand our chat bridges to Telegram and Gitter.
