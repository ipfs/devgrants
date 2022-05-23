# Open Grant Proposal: `Agregore Mobile`

**Name of Project:** Agregore Mobile

**Proposal Category:** `app-dev`

**Proposer:** @RangerMauve

**Technical Sponsor:** @autonome

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description

<!--
Please describe exactly what you are planning to build. Make sure to include the following:
- Start with the need or problem you are trying to solve with this project.
- Describe why your solution is going to adequately solve this problem.

This section should be 2-3 paragraphs long.
-->

We're going to make it easier for people in under connected communities to access peer to peer web content using an Android web browser with IPFS protocol support.

Currently, existing browsers with IPFS support either only work on desktop environments, require the use of a centralized gateway, or don't have easy ways to publish new content without a third party.

Agregore Mobile will run a local IPFS node and enable communities to publish and load content using [the ipfs:// protocol scheme](https://github.com/ipfs-shipyard/ipfs-protocol-compliance-suite/) within browsers on local networks without needing any extra infrastructure.

In addition, we will be hosting a co-design workshop with participants from various community-based connectivity initiatives around the world to demonstrate the software and better understand how the approach can enable underserved communities to be more resilient.

As we complete parts of the project, we will be periodically posting blog updates on https://agregore.mauve.moe

## Value

<!--
Please describe in more detail why this proposal is valuable for the Filecoin ecosystem. Answer the following questions:
- What are the benefits to getting this right?
- What are the risks if you don't get it right?
- What are the risks that will make executing on this project difficult?

This section should be 1-3 paragraphs long.
-->

Publishing and sharing in community networks currently relies on centralized infrastructure and is prone to being unusable due to brownouts or network outages. With IPFS and a mobile web browser, any sort of content that can be loaded on the web can also be authored directly on a persons phone and transmitted to others. We will be ensuring peers can load data from each other on their community network, and directly between phones using Wifi Direct. In underserved ares, communities spend up to 30% of their income on mobile data, often to communicate and share data with people in close proximity. This solution can enable communities to be more resilient and circumvent the barriers to access.

Our integration with the [nimble](https://wakoma.co/nimble/), a portable mesh network node running useful services, will make it easier for communities to back up their data and make it discoverable within their networks. The nimble recently won [first prize](https://www.businesswire.com/news/home/20211207005426/en/IEEE-Announces-First-Winners-of-Connecting-the-Unconnected-Challenge-a-New-Competition-Providing-Solutions-for-the-Digital-Divide) in the IEEE Connecting the Unconnected challenge and is a promising open source solution for enabling communities to connect themselves. Integrating IPFS pinning services into the nimble platform will be an avenue for deploying IPFS in community networks and other community-based conectivity initiatives around the world.

### Risks

There are three areas that bring potential risk with this project.

Will the performance of IPFS nodes on mobile phones will enable rapid loading of content while avoiding excessive battery drain? We will attempt to mitigate this by following the latest recommendations for running "light" IPFS nodes that focus on MDNS peer discovery and reaching out to gateways for loading content off the internet.

Second will be making the technology accessible and usable for communities with low digital literacy and skills. Members of our team have worked with low-digital literacy communities in the past, so we will be able to pull from their experience to help explain the technology and guide the UX.

Finally, we will need to pay special attention to privacy and security implications to make sure that data doesn't accidentally get leaked and put people at risk. We will be assessing the tradeoffs between connectivity and privacy as we design the system.


## Deliverables

<!--
Please describe in details what your final deliverable for this project will be. Include a specification of the project and what functionality the software will deliver when it is finished.
-->

- Android Web Browser with IPFS protocol support
    - Supports chrome dev tools (based on kiwi browser)
    - Embeds go-ipfs node based on [prior work](https://github.com/ipfs-shipyard/gomobile-ipfs)
    - Protocol Handlers pass majority of [IPFS protocol test suite](https://github.com/ipfs-shipyard/ipfs-protocol-compliance-suite/)
    - Support for wifi-direct hotspots to share p2p data without the internet or any infrastructure other than their phones
    - Support for pinning IPFS and IPNS urls to configurable pinning services via an extension
- IPFS pinning services integrated with the nimble for servicing ad-hoc community networks
- Example application which enables people to share media such as images/text/audio
- Two workshops that will teach a focus group of community-based connectivity advocates how to use the browser and how to share information using the example app and will collect information on pain points they have within their networks + potential future applications of the technology.
- Blog post documenting our progress as we go.

## Development Roadmap

<!--
Please break up your development work into a clear set of milestones. This section needs to be very detailed (will vary on the project, but aim for around 2 pages for this section).

For each milestone, please describe:
- The software functionality that we can expect after the completion of each milestone. This should be detailed enough that it can be used to ensure that the software meets the specification you outlined in the Deliverables.
- How many people will be working on each milestone and their roles
- The amount of funding required for each milestone
- How much time this milestone will take to achieve (using real dates)
-->

Here is an outline of the timeline for the milestones. We aim to tackle several milestones at once with two small teams in order to get everything completed within 13 weeks. This is motivated by our desire to align with Community Networks trainings taking place in South Africa in early May.

Track one:

Milestone 1 (3 weeks) Initial browser with go-ipfs node
Milestone 2 (6 weeks) Custom protocol handlers
Milestone 3 (2 weeks) Protocol compliance suite passing

Track two: (starts two weeks after Milestone 1)

Milestone 4: (3 weeks) Example app for sharing data
Milestone 5: (3 weeks) Pinning Service Integration
Milestone 6: (4 weeks) Preparing and running workshops 

### Milestone 1: Browser with Go-IPFS node

1 C++ dev 60h (Emmanuel) / 3 weeks
1 Golang dev 60h (Makeworld) / 3 weeks
1 Android dev 30h / 3 weeks

Total = 150h * 65 = 9750

We will be forking the Kiwi Browser and doing a loose integration with a go-ipfs node which will use the `http://localhost/` gateway to load content from IPFS. We will also edit the branding to look more like Agregore Desktop. We will also take this time to review our strategy for the coming milestones. This is where we'll review the approaches taken in the Brave Browser and the work of Igalia and compare it to the approach we're going to take based on Electron's protocol handler API.r

**Reusable outputs:**: Other browser projects could fork from what we develop if they wish to use the gomobile-ipfs method.

- Android Dev:
    - Fork kiwi browser and get it compiling (20h) (2 weeks)
    - Customize branding to show Agregore logo (10h) (1 week)
- C++ dev:
    - Fork kiwi browser and get it compiling (30h) (1.5 week)
    - Load gateway on startup / close on finish (30h) (1.5 week)
- Golang Dev:
    - compile go-ipfs node for Android using [gomobile-ipfs](https://github.com/ipfs-shipyard/gomobile-ipfs) (40h) (2 week)
        - Set up another repo and configure it as a Gradle pacakge we can import into the browser codebase?
        - Set up gomobile within the main repo and just import a go package?
    - Debug running the gateway with C++ dev (20h) (1 week)

### Milestone 2: Integrating custom protocol handlers

1 C++ dev 120h (Emmanuel) / 6 weeks 
1 Golang dev 120h (Makeworld) / 6 weeks
1 Android dev 120h (Mauve) / 6 weeks

Total = 360h * $65/h = $23400

We will create patches for the chromium source code to add IPFS and IPNS as protocol handlers, and implement a custom mutable gateway which will be invoked by the protocol handlers. Then, we will test out the IPFS protocol compliance suite against them (including mutable IPFS/IPNS) and make sure a large portion of the tests are passing (enough for the next milestone). We will also integrate a UI for Android's Wifi Peer to Peer API that will attempt to connect to local phones. 

Based on this: https://hackmd.io/chATmkpvQh6sifBxBfKU9g

**Reusable outputs:**: Open source browser structure to add custom protocol handlers, reusable protocol handler code in Go, reusable Wifi P2P code for Android apps

- C++ dev: Register custom protocol
    - [Register protocol with registry](https://chromium.googlesource.com/chromium/src/+/HEAD/chrome/browser/custom_handlers/protocol_handler_registry.h) (20) (1 week)
    - Test GET/POST with in-memory responses (40h) (2 week)
        - Use `fetch()` API with devtools to trigger requests
    - Wire GET to go-ipfs gateway (20h) (1 week)
        - Use keepalive to reuse connections?
        - Http3/Quic?
    - Register `ipfs` and `ipns` schemes as ["standard"](https://hackmd.io/chATmkpvQh6sifBxBfKU9g?view#How) (20h) (1 week)
        - Test whether protocols get resolved for images and iframes
        - Ensure extensions can [intercept](https://github.com/electron/electron/issues/26812) IPFS/IPNS URLs
    - Integrate writable gateway (20h) (1 week)
        - Have it run instead of go-ipfs node
- Golang dev: Implement writable gateway following [js-ipfs-fetch](https://github.com/RangerMauve/js-ipfs-fetch)
    - Build a spec that we will target based on js-ipfs-fetch (20h) (1 week)
    - Set up Go package based on [gomobile-ipfs](https://github.com/ipfs-shipyard/gomobile-ipfs) or [gomobile bindings](https://pkg.go.dev/golang.org/x/mobile/cmd/gobind), with an [http-server](https://gowebexamples.com/http-server/) (20h) (1 week)
        - Configure for lower power usage, look into all config options
    - GET/HEAD from IPFS / IPNS (20h) (1 week)
        - Using [files](https://pkg.go.dev/github.com/ipfs/go-ipfs-files#ReaderFile.Seek)
        - detect content-type from URL [with this?](https://github.com/gabriel-vasile/mimetype)
        - directory listing (JSON and html if Accept header asks for it)
        - respect `range` header
    - POST to IPFS (20h) (1 week)
        - Use [files API](https://pkg.go.dev/github.com/ipfs/go-ipfs-files#Node) for regular data / new files?
        - Use [go-mfs](https://github.com/ipfs/go-mfs) to work with existing hashes, and maybe new files too
        - Support FormData (multipart/form-data), reject url encoded?
    - POST to IPNS (with MFS) (20h) (1 week)
        - Steps: load existing CID from IPNS, load into MFS, upload data, get final CID and update IPNS
        - Ensure pubsub is enabled to speed up IPNS
    - Unit Tests (20h) (1 week)
        - Similar to js-ipfs-fetch? https://github.com/RangerMauve/js-ipfs-fetch/blob/default/test.js
- Android Dev: Add wifi-direct
    - Standalone Android app for connecting peers - (60h) (3 weeks)
        - Use Wifi Direct API to create a group if one doesn't exist
        - Auto connect to groups based on name
        - Acquire MulticastLock in order to support MDNS discovery. [won't work on some devices](https://codeisland.org/2012/udp-multicast-on-android/), but there are some [workarounds](https://stackoverflow.com/questions/19197038/android-wi-fi-direct-network/19282158#19282158)
        - Attempt to broadcast Multicast UDP packets on the network
    - Abstract into Android library that can be imported into the main project - (20h) (1 week)
        - Abstract API from app
        - Emit events to whatever is using the API (connection status/number of peers)
    - Integrate library and UI into Agregore Mobile (40h) (2 weeks)
        - Button to "start / stop" local peer discovery
        - Button should reflect the current state of the wifi-direct connection (disconnected/searching/connecting/connected(n peers))
    - Test if MDNS from IPFS node is running through + peer discovery is working (20h) (1 week)
    
### Milestone 3: Passing IPFS protocol compliance suite

1 C++ dev 40h (Emmanuel) / 2 weeks 
1 Golang dev 40h (Makeworld) / 2 weeks
1 Android dev 40h (Mauve) / 2 weeks

Total = 120h * $65/h = $7800

We will ensure that Agregore Mobile passes the same amount (or more) tests as Agregore Desktop for the [IPFS protocol compliance suite](https://github.com/ipfs-shipyard/ipfs-protocol-compliance-suite/). We will also make it easier to download and test the app via Github releases and APKs published on IPNS.

**Reusable outputs:** updated IPFS Protocol Compliance Suite with more examples of how it works

- C++/Golang devs: Run the general and mutable protocol test suite and fix bugs (40h) / (40h)
    - Ensure the suite is still working in Agregore
    - Visually check that everything is passing and performant
    - Test loading data between desktop and mobile Agregore
- Android Dev:
  - Set up CI to publish APKs to Github and IPFS (20h) (1 week)
  - Ensure test suite passes over wifi-direct connection (20h) (1 week)

   
### Milestone 4: Example app showcasing sharing data

- 1 Web Dev (Dirk) 60h / 3 weeks
- 1 Tech Lead (Mauve) 30h / 3 weeks

Total = 90h * $65/h = 5850 

We will put together a basic peer to peer web app which will showcase a micro-blog-like interface where users will be able to create posts using markdown and upload images to create a simple blog. Blogs will be easy to share using QR codes via [a web extension](https://chrome.google.com/webstore/detail/qr-code-generator/afpbjjgbdimpioenaedcjgkaigggcdpp) and people will be able to bookmark blogs that they might frequently visit.
This will showcase publishing and loading content while being fairly basic so that people can extend their own versions out and using the browser's existing functionality as much as possible.

**Reusable outputs:** A reusable app to showcase publishing content to IPFS via protocol handlers, potentially reusable web components and patterns.

- Tech Lead:
    - Initial mock up (10h)
        - Figure out data architecture
            - Use subfolders for `year/month/day` with 0-padding and timestamped MD docs
        - Work with web dev to mock up the UIs (mostly defining stuff)
        - WYSIWYG text editor (to markdown?)
            - Drag and drop states?
            - Image/File upload?
        - What do you see on the "homepage" (titles of latest posts?)
    - Support web dev on post composing, start working on documentation (10h)
    - Support web dev on homepage, test QR code generators/scanner extensions and bookmarking flow (10h)
- Web Dev
    - Initial mock up (20h)
        - Learn about p2p web tech
        - Work with tech lead to mock up the UIs (implementing with basic HTMl and CSS)
    - Editor for composing "posts" / Viewing a post (20h)
        - Can viewing be done via the [Agregore markdown extension?](https://github.com/AgregoreWeb/extension-agregore-render-markdown)
    - Homepage for viewing latest posts (20h)
        - Pagination, or just everything?
        - Dynamically load with JS or statically generate HTML?
        - Color scheme customizer?

### Milestone 5: IPFS pinning service UI / integration

1 Linux sysadmin (Dirk) 60h / 3 weeks
1 Web Dev (Mauve) 30h / 3 weeks
1 Community Lead (Eric / Wakoma) 30h / 3 weeks

Total = 120h * 65 = 7800

Add ability to register [pinning services](https://ipfs.github.io/pinning-services-api-spec/) in the browser and to quickly pin a given `ipfs://` URL when its visited. Also integrate an IPFS pinning service onto the [nimble](https://wakoma.co/nimble/) and showcase connecting to one and pinning content to it. Add Agregore downloads to captive portal to bootstrap android and laptop users?

The nimble is an open source, portable, and offline-first wireless mesh network.  The nimble recently won the Best overall Proof-of-Concept award at the 2021 IEEE Connecting the Unconnected Challenge.

For the purposes of this project, there is currently one nimble readily available for development and testing in South Africa.  A second unit should be built in Ottawa to enable makeworld to contribute to and expedite the development process.  This unit should cost in the range of $2000 CAD depending on supply issues.

**Reusable outputs:** Scripts for setting up IPFS-Cluster for mesh networks, web extension for talking to pinning services (can be used across different browsers)

- Linux sysadmin: Configure IPFS pinning service on Nimble
    - Use [ipfs-cluster](https://github.com/ipfs/ipfs-cluster) (40h) (2 weeks)
        - Supports IPNS
        - Might want to [make it compliant with the spec](https://github.com/ipfs/ipfs-cluster/issues/1213)
    - Hardcode pinning service in DNS (10h) (0.5 week)
    - Agregore downloads on captive portal? (10h) (0.5 week)
- Community Lead: Look at moderation and administrative needs for pinning services
    - Analyze administrative tools for IPFS-cluster / pain points / privacy considerations (20h) (1 weeks)
    - Write up findings in a blog post (10h) (1 week)
        - What was lacking for moderation / privacy?
        - What are next steps to take to improve the situation?
- Web Dev: Add extension to agregore-mobile for pinning to nimble
    - UI for configuring pinning service and pinned items (10h)(1 week)
        - Should default to nimble's hardcoded DNS name for pinning
        - Should be able to change the pinning service URL and the bearer token
        - Should be able to list pins/remove
        - Support both standard pinning services and ipfs-cluster (how can we detect this?)
    - extension button for "pin this page" to pin the current URL (10h)
        - Do we need something fancy for embedded images and other media?
    - Test with nimble (10h)
        - Does it work out of the box?
        - Can multiple devices talk to it?
        - Can both Agregore Mobile and Desktop talk to it?

### Milestone 6: Workshop for community networks

1 Community outreach and coordination (Eric / Wakoma) 60h / 4 weeks
1 Workshop facilitator (Dirk) 80h / 4 weeks
20 Focus Group participants: 80h * 15 USD/h = $1200
Travel + Living Expenses: 3000 USD
Workshop Equipment + Refreshments: 200 USD

Workshop costs = 120h * $65 USD/h = 7800
Total = workshop + participants + equipment costs + travel = ???
Total = 7800 + 1200 + 200 + 3000 = 12200

Once we have the protocol handlers and example application finished our team will engage with two groups of community network stakeholders in South Africa to test and deploy the mobile web browser in real world contexts. Users will learn how IPFS works and discussions will take place on how it can be adopted by community networks to address challenges and enable cheaper and more reliable connectivity.  Where possible, participants will use the nimble in tandem with Agregore Mobile to load data and share it over the local network. 

**Workshop 1**
Tech for Good group in Cape Town.  This will be comprised of a small group of technologists in Cape Town working on civic tech and social change. The workshop will be conducted for initial testing and feedback of the app.

**Workshop 2**
Once the app is ready for wider use, we will hold a second workshop with a larger audience.  The group will consist of participants from various community networks in South Africa.

Over the course of several days, participants will install Agregore Mobile on their phone and test the example app and the Nimble pinning service.  Participants will also learn about the wifi-direct functionality in Agregore Mobile and will test sharing a post with each other by making an ad-hoc connection without needing the Nimble Wifi access point set up. 

Finally we will receive feedback from focus group participants to see where we can improve the UX and better understand appropriate applications of the technology. 

Participants will receive a small stipend for their participation and transcript summaries from the sessions will be made.  Depending on covid restrictions we may have fewer participants who engage more during Milestone 6. 

These workshops open up the possibly of and provide a format for hosting future workshops in other community networks around the world.

**Reusable outputs:**: Materials for running the workshop, results of the workshop posted on the blog

- Community outreach:
    - Identification of and communication with participants (40h) (3 weeks)
        - Enlist participants active in community networks and brief the group on the project objectives and process
        - Coordinate workshop/meeting times and locations
        - Coordinate travel and logistics
    - Followup on workshop (20h) (1 week)
        - Collect feedback from the workshops
        - Summarize what was learned / propose follow-up projects
- Workshop facilitator:
    - Prepare workshop materials and hardware (60h) (2 weeks)
        - Slide deck with information about the project / use cases
        - Prepare presentation and workshop plan
        - Prepare nimble units for workshops
        - Prepare questionnaires to ask participants for feedback
    - Run Workshop 1 (10h) 1 week
        - Schedule meetup with Cape Town group
        - Run workshop with participants
        - Collect feedback for later analysis
    - Run workshop (10h) (1 week)
        - Fly to Mankosi (or Johannesburg, depending on preferred workshop)
        - Establish F2F spaces to run the workshops
        - Run the workshop with participants
        - Collect participant feedback for later analysis

## Total Budget Requested

<!--
Sum up the total requested budget across all milestones, and include that figure here. Also, please include a budget breakdown to specify how you are planning to spend these funds.
-->

Rates: $65 USD/hour

Milestone 1: 150h * $65/h = $9750 (3 weeks)
Milestone 2: 360h * $65/h = $23400 (6 weeks)
Milestone 3: 120h * $65/h = $7800 (2 weeks)
Milestone 4:  90h * $65/h = $5850 (3 weeks)
Milestone 5: 120h * $65/h = $7800 (3 weeks)
Milestone 6: 120h * $65 USD/h + 80h * 15 USD/h + $200 USD + $3000 USD = $12200 (4/5 weeks)

Total: $66800 USD

## Maintenance and Upgrade Plans

<!--
Specify your team's long-term plans to maintain this software and upgrade it over time.
-->

Once the initial browser is implemented and shown to work, we will be able to start building more p2p web software on top of it and will be keeping it upgraded and in line with Chromium / IPFS updates. Particularly, we see the initial focus group using Agregore as a way to open communities to the potential of peer to peer web technology, learn how it can address their needs, and to fund work on higher level applications that provide utility for communities which wouldn't exist otherwise. Content built on Agregore Mobile/Desktop will also be able to run on traditional internet based networks, boosting both ecosystems.

# Team

## Team Members

- Mauve, Tech Lead/Android dev, p2p expertise
- Eric, Community-based Connectivity Lead
- makeworld, Senior Go Developer, mesh network and p2p expertise
- Emmanuel, C++ Developer
- Dirk, Web Dev, Sysadmin

## Team Member LinkedIn Profiles

- Mauve: https://www.linkedin.com/in/mauve-s-47697579/
- Eric: https://www.linkedin.com/in/ericnitschke/
- makeworld: N/A
- Emmanuel: N/A
- Dirk: https://www.linkedin.com/in/dirk-uys-4273578/

## Team Member GitHub Profiles

- makeworld: [@makeworld-the-better-one](https://github.com/makeworld-the-better-one)
- Mauve: [@RangerMauve](https://github.com/RangerMauve/)
- Eric: [@Wakoma](https://github.com/wakoma)
- Dirk: [@Dirk](https://github.com/dirkcuys/)
- Emmanuel: [@Madrets](https://github.com/madrets)

## Team Website

<!--
Please link to your team's website here (make sure it's `https`)
-->

https://software.mauve.moe/

## Relevant Experience

<!--
Please describe (in words) your team's relevant experience, and why you think you are the right team to build this project. You can cite your team's prior experience in similar domains, doing similar dev work, individual team members' backgrounds, etc.
-->

Mauve: Has created a peer to peer web browser for desktop environments. Has completed several protocol-labs devgrants pushing IPFS protocol support in browsers. Has been doing consulting on different decentralized projects since 2018. Before doing consulting, Mauve led a team of developers working on healthcare software and managed timelines / supporting developers to get their features finished. Mauve also has extensive experience with building Android apps and getting peer to peer code to run on Android devices.

Eric:  Founder and CEO of Wakoma, a social enterprise building open-source hardware and software solutions that enable communities to design, build and share their own network infrastructure and localized content and services which operate offline and online. Eric is a firm advocate for meaningful connectivity, digital inclusion, and open education.  

makeworld: Has experience managing, configuring, and peering IPFS nodes on less powerful systems such as Raspberry Pis, through work with Toronto Mesh. Has developed and maintained multiple open source Go libraries and applications from scratch, including implementing alternative Web protocols such as [Gemini](https://geminiquickst.art/). Has implemented custom HTTP server functionality in Go for several different projects.

Emmanuel: Has created a procedural programming language from scratch using C++, which imitates and improves upon some features of assembly language. He has also created several stand-alone desktop applications using C++. Emmanuel has recently completed a Bachelor's degree in Computer Science. 

Dirk: Has been doing full stack web development and Linux system administration in different contexts ranging from online education to in-person peer-to-peer learning. Dirk has taken several projects from conception to production. Dirk has also done several online and in-person workshops with 6-20 participants.

## Team code repositories

Please provide links to your team's prior code repos for similar or related projects.

https://github.com/AgregoreWeb/agregore-browser/
https://github.com/Wakoma/Lokal

# Additional Information

<!--
Please include any additional information that you think would be useful in helping us to evaluate your proposal.
-->

This proposal was put together with feedback from @autonome and @lidel
