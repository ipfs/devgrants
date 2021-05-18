# Targeted Grant: DNSLink multiplatform and update

**Issuer:** [@lidel][]
**Recipient:** [@martinheidegger][]

## Project Description

**Update DNSLink implementations and publication for consistency and interoperability.**

The project consists of 4 parts in 5 milestones:

1. Create Test Suite for DNSLink implementations.
2. Fix essential issues with existing DNSLink implementations in IPFS.
3. Update DNSLink website & specifications to reflect the changes in the implementation and reference the test suite.
4. Create browser tool for DNSLink exploration.

## Value

With the work done in this grant, DNSLink will support multi-protocol. Allowing users of DNSLink to choose both IPFS and another protocol instead of having to choose either as its the case right now.

The documentation updates have the goal to explain DNSLink system better to end users, developers and implementers.

The consistency of the implementations is to increase the confidence in DNSLink.

## Deliverables

- Language and platform independent **test setup** for dnslink.
- **Documentation** specifying redirects and consistent ordering.
- Independent DNSLink **JavaScript implementation** that works in browsers and Node.js.
- **Browser util** that visualizes the output of the DNSLink for a given domain name.
- **Fixes for the existing implementations** of DNSLink used in IPFS (GO & javascript).

## Team

- [@martinheidegger][] - (Grant recipient) Active member of the dweb community.
   New to the IPFS community; working on dns support for the `hyper://` community. Actively developing of `hyper-dns` for the hyper community.

- [@lidel][] - (Protocol Labs) Technical advisor

## Detailed Requirements & Constraints

**Test Setup:** A test setup needs to consist of DNS-settings on the domain that can be used to verify a working version of DNSLink. It needs to cover all edge cases, such as: existing/missing `_dnslink` subdomains, redirects, multiple dnstext entries for multiple protocols and error cases.

**Documentation:** The documentation to be published on the dns page needs to cover the Test setup, and detail the new fixes of the implementation.

**JavaScript Implementation:** The JavaScript implementation needs to provide TypeScript definitions, `tape` tests be published on NPM. In the CI setup it needs to work with `browser-run`. The implementation needs to also work with DoH, respecting the [wire format](https://developers.cloudflare.com/1.1.1.1/dns-over-https/wireformat).

**Browser util:** The browser util at dnslink.io needs to work on modern browsers, excluding IE 11. Minimally it needs to provide the result of DNSLink lookup for a given domain: resolve DNS TXT lookup over DoH using the RFC-compliant wire-format. Needs option to specify DoH configuration.

**Fixes for the existing implementations:** Provide Pull Requests an tests for the existing `js-ipfs` implementation, `go-dnslink` implementation and `go-namesys` implementation.

## Milestones & Funding

**Total Funding Amount:**  $9100 <!-- List the total proposed funding amount (currently in USD, eventually can be a distribution between USD/FIL)-->

**Milestones:** (working ~30 hours a week)<!-- Make sure that the values in the Funding column add up to the Total Funding Amount listed above.-->

| Milestone No. | Milestone Description | Funding | Estimated Timeframe |
| --- | --- | --- | --- |
| 1 | Test Setup | $1300 | ~20h  |
| 2 | Documentation | $1300 | ~20h  |
| 3 | JavaScript Implementation | $2600 | ~40h  |
| 4 | Browser util | $1300 | ~20h |
| 5 | Fixes for the existing implementations | $2600 | ~40h  |

## Acceptance Criteria

<!-- What are the acceptance criteria for each milestone and for the final deliverables? These should be as objective as possible. They will be used to determine whether or not a grantee will receive payment for work completed for a milestone. -->

1. Published Test Setup and examplary use of it in one implementation.
2. Pull-Request on dnslink homepage containing all required changes to the spec.
3. JavaScript library with reference implementation of the DNSLink spec published on NPM. Programmatic interface for resolving DNSLink records works in Nodejs and Browser, and command line script can be used for quick lookup/validation when run via `npx`.
4. Browser Util, based on the NPM library, published on the dnslink.io website allowing to explore and test DNSLink records on a domain provided by the user. DoH endpoint used for DNS lookups can be customized via UI.
6. Accepted PR's to existing IPFS repositories. go-ipfs uses go-dnslink, and js-ipfs uses the new dnslink library from NPM. 

## Resources

<!-- Link any resources that might be helpful for an implementer who is working on this project.-->

- https://github.com/ipfs/js-ipfs/issues/3685
- https://github.com/ipfs/go-dnslink/issues/14
- https://github.com/JChanceHud/dnslink/issues/5
- https://github.com/ipfs/js-ipfs/issues/3684
- https://github.com/ipfs/dnslink.dev/issues/1
- https://github.com/ipfs/js-ipfs/issues/2212

## Support and Funding


This grant is funded by Protocol Labs.  
Technical guidance will be provided by [@lidel][].

[@lidel]: https://github.com/lidel
[@martinheidegger]: https://github.com/martinheidegger
