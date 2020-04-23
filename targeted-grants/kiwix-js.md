# Unstoppable knowledge: kiwix-js reading Wikipedia .zim archives from IPFS

Issuer: \@lidel / [distributed-wikipedia-mirror](https://github.com/ipfs/distributed-wikipedia-mirror)

- [Project Description]
  - [Background]
  - [Goals]
  - [Value]
- [Team]
- [Milestones & Funding]
- [Acceptance Criteria]
  - [Milestone 1: PoC]
  - [Milestone 2: User interface and permalinks]
  - [Milestone 3: Robust transport]
  - [Milestone 4: Final product]
- [Additional notes]

  [Project Description]: #project-description
  [Background]: #background
  [Goals]: #goals
  [Value]: #value
  [Team]: #team
  [Milestones & Funding]: #milestones--funding
  [Acceptance Criteria]: #acceptance-criteria
  [Milestone 1: PoC]: #milestone-1-poc
  [Milestone 2: User interface and permalinks]: #milestone-2-user-interface-and-permalinks
  [Milestone 3: Robust transport]: #milestone-3-robust-transport
  [Milestone 4: Final product]: #milestone-4-final-product
  [Additional notes]: #additional-notes

## Project Description

In this devgrant we are looking at adding IPFS support to kiwix-js project,
making it a viable option for browsing distributed Wikipedia mirror from a
static, regular web page.

### Background

#### About Kiwix and .zim archives

Quoting Wikipedia feels appropriate here:

> Kiwix is a free and open-source offline web browser created by Emmanuel
> Engelhart and Renaud Gaudin in 2007. It was first launched to allow offline
> access to Wikipedia, but has since expanded to include other projects from
> the Wikimedia Foundation as well as public domain texts from Project
> Gutenberg. Available in more than 100 languages, Kiwix has been included in
> several high-profile projects, from smuggling operations in North Korea and
> encyclopedic access in Cuba to Google Impact Challenge\'s recipient
> Bibliothèques Sans Frontières.
>
> -- [https://en.wikipedia.org/wiki/Kiwix]

In more technicl terms, Kiwix project is responsible for creating [.zim
archives] (single-file snapshots of MediaWiki and other websites), hosting
mirrors and maintaining the suite of [readers] for various platforms.

  [https://en.wikipedia.org/wiki/Kiwix]: https://en.wikipedia.org/wiki/Kiwix
  [.zim archives]: https://wiki.kiwix.org/wiki/Content_in_all_languages
  [readers]: https://www.kiwix.org/en/downloads/kiwix-reader/

#### About Kiwix JS and this grant

[kiwix-js] is an offline ZIM reader written in JavaScript. In its current form
kiwix-js is unable to read huge files from user\'s machine, unless the reader
is wrapped in a browser extension.

  [kiwix-js]: https://github.com/kiwix/kiwix-js

### Goals

In order for this project to be a success, it must meet the following goals:

- Kiwix-js:
  - Supports loading ZIMs from IPFS
  - Uses the best IPFS transport available
  - Runs on a regular page while still being able to read a huge ZIM
    (\>4GB)
  - Makes URL in web browser address bar useful as bookmark, namely:
    - URL deterministically points at currently viewed ZIM resource
      (includes a cryptographically verifiable content path of browsed
      ZIM archive followed by name of currently viewed article)
    - Copying permalink from address bar and sharing it with someone gets
      them to the same article

### Value

**Kiwix**: project benefits from improved accessibility and additional mirrors.
The web-based ZIM reader works in every web browser without installing any
browser extension or additional software. Specific article inside of ZIM can be
bookmarked and shared to anyone with a web browser. IPFS users are cohosting
popular ZIM archives, acting as a distributed CDN.

**Distributed Wikipedia Mirror Project**: ability to read ZIM files directly
(without unpacking and processing them) decreases the overhead of running the
project and make it possible to easily add additional languages as soon as .zim
files are created and added to IPFS.

**IPFS**: reaffirming the project mission. Thanks to the content addressing,
trustless p2p networking, cryptographically verifiable ZIM assets are cached
and cohosted by IPFS nodes, making the knowledge available in offline and
censored environments.

## Team

TBD (this could be you!)

## Milestones & Funding

**Total Funding Amount:** TBD

**Milestones:**

| Milestone No. | Milestone Description | Amount |
| ---           | ---                   | ---    |
| 1             | PoC                   | TBD    |
| 2             | UI                    | TBD    |
| 3             | Transport fallback    | TBD    |
| 4             | Final product         | TBD    |

## Acceptance Criteria

<!-- What are the acceptance criteria for each milestone and for the final
deliverables? These should be as objective as possible. They will be used to
determine whether or not a grantee will receive payment for work completed for
a milestone.  -->

### Milestone 1: PoC

Create a PoC that demonstrates feasibility of reading ZIM from IPFS. It could
be built with [ipfs-http-client] using HTTP API at `https://ipfs.io/api/v0/cat`
or `http://127.0.0.1:5001/api/v0/cat` exposed by [ipfs-desktop] (whichever
works best / turns out to be easier at this stage).

Test:

- kiwix-js should be able to read data from IPFS to browse archive bigger than
  4GB, such as [wikipedia\_tr\_all\_maxi\_2020-04.zim] or later.

  [ipfs-http-client]: https://github.com/ipfs/js-ipfs/tree/master/packages/ipfs-http-client
  [ipfs-desktop]: https://github.com/ipfs-shipyard/ipfs-desktop
  [wikipedia\_tr\_all\_maxi\_2020-04.zim]: https://download.kiwix.org/zim/wikipedia/wikipedia_tr_all_maxi_2020-04.zim

### Milestone 2: User interface and permalinks

Implement user interface for opening ZIM from IPFS and customizing IPFS
transport.

Test:
- Shareable permalinks control what is loaded and displayed to the user
  - IPFS address of ZIM file can be passed as URL hash (without sending it
    to HTTP server) 
    - eg. check `window.location.hash` for
      `#/ipfs/$cid/wikipedia_tr_all_maxi_2020-04.zim`
  - URL hash gets updated as user browses the ZIM contents, reflects
    currently viewed resource
    - eg. `#/ipfs/$cid/wikipedia_tr_all_maxi_2020-04.zim!Güneş_Sistemi` points at a snapshot of  [this article](https://tr.wikipedia.org/wiki/G%C3%BCne%C5%9F_Sistemi)
- GUI is added for manually entering IPFS CID, content path or URL at a public gateway
  (all get converted to content path)
- GUI is added for customizing IPFS transport
  - HTTP API URL: user should be able to use custom API endpoint

### Milestone 3: Robust transport

Automatically find the best IPFS API available on user\'s machine. Reuse
[ipfs-provider] if possible for modeling fallback order and built-in connection
testing.

It should try [httpClient] on `http://127.0.0.1:5001/api/` ([ipfs-desktop]),
then one at `window.location.origin` (the server used for fetching the page
with kiwix-js), try public instance at `http://ipfs.io/api/`, and if all failed
fallback to spawning embedded js-ipfs with webrtc transport as a last resort.

Test:

- kiwix-js tries to leverage `ipfs.io/api/` if no local node is available
- kiwix-js is reading ZIM from local IPFS node when user has [ipfs-desktop]
  installed and proper CORS headers set up or IPFS Companion installed
- kiwix-js is spawning embedded js-ipfs when all HTTP APIs failed

  [ipfs-provider]: https://github.com/ipfs-shipyard/ipfs-provider/
  [httpClient]: https://github.com/ipfs/js-ipfs/tree/master/packages/ipfs-http-client
  [ipfs-desktop]: https://github.com/ipfs-shipyard/ipfs-desktop

### Milestone 4: Final product

Polished code is ready for review by the upstream kiwix-js project. PR against
[kiwix-js] repo is opened, feedback from kiwix-js maintainers is addressed.

Test:

- PR is closed.
  - Either PR is merged or grant sponsor agrees to creating a fork.

  [kiwix-js]: https://github.com/kiwix/kiwix-js

----

## Additional notes

Below resources may be useful for initial research and developer ramp up:

- IPFS Daemon exposing HTTP API at http://127.0.0.1:5001
  - CLI: https://github.com/ipfs/go-ipfs 
  - GUI: https://github.com/ipfs-shipyard/ipfs-desktop 
  - JS:
  - HTTP API client for JS: https://github.com/ipfs/js-ipfs/tree/master/packages/ipfs-http-client 
  - Full IPFS node in JS: https://github.com/ipfs/js-ipfs/tree/master/packages/ipfs
  - **Note:** both expose the same programmatic interface: https://github.com/ipfs/js-ipfs/tree/master/docs/core-api
- Fetching arbitrary byte ranges from a file in IPFS: 
  https://github.com/ipfs/js-ipfs/blob/master/docs/core-api/FILES.md#cat
  https://docs-beta.ipfs.io/reference/http/api/#api-v0-cat 
- Sample ZIMs useful for testing:
  - 2MB: [wikipedia_en_ray_charles_maxi_2020-03.zim](https://download.kiwix.org/zim/wikipedia/wikipedia_en_ray_charles_maxi_2020-03.zim)
  - 70MB: [wikipedia_en_climate_change_maxi_2020-04.zim](https://download.kiwix.org/zim/wikipedia/wikipedia_en_climate_change_maxi_2020-04.zim)
- Note that ZIM can be represented on IPFS with or without explicit filename. Need to support both.
  - Option 1: wrapped in a directory which stores the filename
  ```
  $ ipfs add --cid-version 1 ./wikipedia_en_ray_charles_maxi_2020-03.zim
  added bafybeieejumqwzjka7etfaiee33bkato524sqhdk5boyzyiz4537y7bk44 wikipedia_en_ray_charles_maxi_2020-03.zim
  added bafybeigdrvnlyegx34647xkcyuq7hoe6k7nofafgbzgbuuvaobcuchhrkq 
  ```
  Then use the CID of the wrapping directory:
  - public gateway ([there are many](https://ipfs.github.io/public-gateway-checker/))
    - https://ipfs.io/ipfs/bafybeigdrvnlyegx34647xkcyuq7hoe6k7nofafgbzgbuuvaobcuchhrkq/wikipedia_en_ray_charles_maxi_2020-03.zim
    - https://bafybeigdrvnlyegx34647xkcyuq7hoe6k7nofafgbzgbuuvaobcuchhrkq.ipfs.dweb.link/wikipedia_en_ray_charles_maxi_2020-03.zim
  - locally running go-ipfs:
    - http://127.0.0.1:8080/ipfs/bafybeigdrvnlyegx34647xkcyuq7hoe6k7nofafgbzgbuuvaobcuchhrkq/wikipedia_en_ray_charles_maxi_2020-03.zim
  - Option 2: no wrapping (just a hash, but optional `filename` can be provided manually to set `Content-Disposition` HTTP header for browsers)
  ```
  $ ipfs add --cid-version 1 ./wikipedia_en_ray_charles_maxi_2020-03.zim
  added bafybeieejumqwzjka7etfaiee33bkato524sqhdk5boyzyiz4537y7bk44 wikipedia_en_ray_charles_maxi_2020-03.zim
  ```
  - public gateway: 
    - https://ipfs.io/ipfs/bafybeieejumqwzjka7etfaiee33bkato524sqhdk5boyzyiz4537y7bk44?filename=wikipedia_en_ray_charles_maxi_2020-03.zim
    - https://bafybeieejumqwzjka7etfaiee33bkato524sqhdk5boyzyiz4537y7bk44.ipfs.dweb.link/?filename=wikipedia_en_ray_charles_maxi_2020-03.zim
  - locally running go-ipfs:
    - http://127.0.0.1:8080/ipfs/bafybeieejumqwzjka7etfaiee33bkato524sqhdk5boyzyiz4537y7bk44?filename=wikipedia_en_ray_charles_maxi_2020-03.zim 

