# Phase 1.0 Milestone Report 
> Project Setup, HTTP Scaffolding, Conformance Testing Framework

# Executive Summary

The IPFS Rust grant team completed Phase 1.0 on schedule. 

# Issue by Issue

The following activities were scoped and planned for Phase 1.0:

- Project Setup
    - Git Repositories
    - Code Organization
    - CI/CD
- HTTP Scaffolding
    - Simple Daemonization
    - 501 NOT IMPLEMENTED` Boilerplate
- Conformance Testing
    - Update js-ipfsd-ctl
    - Update ipfs/interface-js-ipfs-core
    - Run conformance testing on implemented endpoints
- Interoperability Testing
    - Update ipfs/interop
    - Interop Testing
- Project Milestone Report
    - Executive Summary
    - Comformance Test Results
    - Interop Report

## Project Setup

* Chat Bridges
* Logo
    * https://github.com/ipfs-rust/logo/issues/2
    * https://github.com/ipfs-rust/rust-ipfs/pull/55
    * https://github.com/ipfs-rust/rust-ipfs/pull/70


Finally, we applies Mozil

### Git Repositories

Goal: Quality of repository administration (as opposed to code quality)

We organized the repositories according to the following list. Indentation implies creating crates within subfolders, and importing them via the [Rust module system](https://doc.rust-lang.org/book/second-edition/ch07-00-modules.html).

- rust-ipfs
    - http
    - bitswap
- rust-ipld

We chose the Standard Readme spec. For example, see the [ipfs-rust](ttps://github.com/ipfs-rust/rust-ipfs/pull/72
) and [ipfs-rust-conformance](https://github.com/ipfs-rust/ipfs-rust-conformance/issues/11) READMEs. We also wrote a [Contributors guide](https://github.com/ipfs-rust/rust-ipfs/issues/61) and added it to the repo according to GitHub's "Community profile", which is now reporting a green status.

Finally, we also applied the [IPFS Community code of conduct](https://github.com/ipfs-rust/rust-ipfs/pull/68) following permission from Protocol Labs.

### Code Organization

* https://github.com/ipfs-rust/rust-ipfs/issues/54
* https://github.com/ipfs-rust/rust-ipfs/pull/74
* https://github.com/ipfs-rust/rust-ipfs/pull/81

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
