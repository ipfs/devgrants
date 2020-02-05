# React Native support for the js-ipfs-http-client

**Proposer**: [schwartz10](https://github.com/schwartz10), [pcowgill](https://github.com/pcowgill/)

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** yes

# Project Description

The js-ipfs-http-client does not work out of the box in React Native. This is a problem because it’s difficult to create a native mobile application that interacts with a remote IPFS node. Running a remote node (instead of one in the phone) can be preferable if it consumes less data, battery, and memory, or is faster and more flexible to set up out-of-the-box.

Phase 0 of this proposal is for up to 1.5 weeks of research to get more visibility around the technical challenges, blockers, and potential solutions for making the js-ipfs-http-client compatible with React Native. Then we’ll submit a spec that outlines our intended solution as a follow-on deliverable.

# Value

We gauged community interest in this initiative by filing a [Gitcoin Grant](https://gitcoin.co/grants/364/react-native-support-for-ipfs) and conducting developer interviews. In two weeks, our Gitcoin Grant received \$410 from 14 different contributors. We spoke to 5 teams developing mobile wallets in the Ethereum ecosystem - each would benefit from the js-ipfs-http-client working in React Native. In the 3Box ecosystem alone, 5 active projects requested this functionality in the past few weeks.

Alternative starting points exist for running an IPFS node inside the phone. Textile worked on [grpc-ipfs-lite](https://github.com/textileio/grpc-ipfs-lite), which could be extended for use in React Native. There’s also [gomobile-ipfs](https://github.com/ipfs-shipyard/gomobile-ipfs), but it’s still experimental, and it’s unclear what its development and stability will be in the future. Involving other languages like Go, Swift, Kotlin, etc. adds complexity for a developer when initially configuring the project and when debugging, so it’s best to avoid unless absolutely necessary.

Both these alternatives are still difficult to get working in React Native and would require the developer to [eject](https://docs.expo.io/versions/latest/expokit/eject/) from React Native Expo. This could make developing with IPFS less accessible to junior engineers interested in experimenting with IPFS in native mobile apps. These alternative approaches might also not be compatible with packages like 3Box or OrbitDB.

## Deliverables

A spec that outlines the optimal solution(s) to the problem. We plan to use this spec to create follow-on deliverables for this Open Grant Proposal.

## Development Roadmap

Investigation of multipart/form-data issues that the js-ipfs-http-client lib throws errors when first configured in a React Native env. We need to figure out if this problem can/should be handled natively or in JavaScript.
Documenting proper babel config for async iterator support
Documenting work-arounds for fetch to support streams in React Native (Open PR against js-ipfs-http-client and `@stardazed/streams-polyfill`)
Investigation of viability of `rn-fetch-blob` as an alternative fetch implementation
Investigation of any other newer browser APIs used in js-ipfs-http-client that are not supported in React Native.
Documenting which of the outstanding issues can be mitigated when the IPFS core team moves away from their use of ky and ky-universal as their fetch abstraction
Investigation of any networking or libp2p issues, including pub-sub.

## Total Budget Requested

Up to \$8,775 for 1.5 weeks of work, starting Wednesday February 5th to Friday February 14th, 2020. If the investigation is finished early, a prorated amount will be paid.

## Maintenance and Upgrade Plans

Our plan is to PR the documentation/investigation outputs to an issue in ipfs/notes or ipfs/js-ipfs-http-client for others to learn from.

## Team Members

Open Work Labs (Jonathan Schwartz)<br />
[Website](https://www.openworklabs.com/)<br />
[GitHub](https://github.com/openworklabs/)

Paul Cowgill<br />
[Website](https://cowgill.io/)<br />
[GitHub](https://github.com/pcowgill/)

## Relevant experience

We’ve been working on this exact problem with Hugo Dias from IPFS core for about 3 weeks already now. We have a very in-depth understanding of the challenges ahead.

## Team code repositories

https://github.com/openworklabs/react-native-ipfs-http-client/
