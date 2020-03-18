<h1>
  <img src="https://ipfs.io/ipfs/QmRcFsCvTgGrB52UGpp9P2bSDmnYNTAATdRf4NBj8SKf77/rust-ipfs-logo-256w.png" width="128" /><br />
  Rust IPFS: Phase 1.0 Milestone Report
</h1>

The IPFS Rust grant team completed Phase 1.0 on schedule. The following activities were initially scoped and planned: 

- [Project Setup](#project-setup) incl. Git repositories, code organization, and continuous integration
- HTTP Scaffolding with `501 NOT IMPLEMENTED` boilerplate
- Conformance Testing
- Interoperability Testing
- Project Milestone Report
    
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

### CI/CD

* https://github.com/ipfs-rust/rust-ipfs/issues/62
* https://github.com/ipfs-rust/rust-ipfs/issues/41
* https://github.com/ipfs-rust/rust-ipfs/pull/69
* https://github.com/ipfs-rust/rust-ipfs/pull/73
* https://github.com/ipfs-rust/rust-ipfs/pull/100

## HTTP Scaffolding

* https://github.com/ipfs-rust/rust-ipfs/issues/60
* https://github.com/ipfs-rust/rust-ipfs/pull/103
* https://github.com/ipfs-rust/rust-ipfs/pull/64
* https://github.com/ipfs-rust/rust-ipfs/pull/71

### Simple Daemonization

### 501 NOT IMPLEMENTED Boilerplate

* https://github.com/ipfs-rust/rust-ipfs/blob/master/http/src/v0.rs#L30

## Conformance Testing

* https://github.com/ipfs-rust/npm-rust-ipfs-dep/issues/1

### Update js-ipfsd-ctl

* https://github.com/ipfs/js-ipfsd-ctl/pull/473

### Update ipfs/interface-js-ipfs-core

* not necessary
* note that some tests _will_ need to be refactored
* Transisitioning to 

### Run conformance testing on implemented endpoints

* See testing below

## Interoperability Testing

### Update ipfs/interop

* https://github.com/ipfs-rust/interop/issues/1
* https://github.com/ipfs-rust/interop/pull/2

### Interop Testing

* See interop testing below

# Conformance Test Results

## Interface Tests

* 501 Not implemented

## Interop Tests

* Not required but some cursory exploration was done, and planning for 1.1 and 1.2

# What's Next?

Phase 1.1 will XXXX.
