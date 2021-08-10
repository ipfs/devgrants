# Open Grant Proposal: IPFS support in FFmpeg-based media players

**Name of Project:** IPFS support in FFmpeg-based media players

**Proposer:** @markg85 (Mark Gaiser)

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:** Yes

# Project Description
The way of playing videos (or looking at pictures) stored in IPFS currently is limited to either downloading them and use local applications. Or use web tailored applications that know how to talk IPFS. In the case of using web mechanics (say the `<video>` tag) you're still reliant on what your browser supports.

This project is making it possible to play video (or open images) directly trough FFmpeg. Meaning you have a lot more options in terms of codecs for your video/images to work out of the box. For example, this BigBuckBunny movie would play if ffmpeg were patched to understand IPFS `ffplay ipfs://QmbGtJg23skhvFmu9mJiePVByhfzu5rwo74MEkVDYAmF5T`

FFmpeg is used in many video applications as one of the libraries used behind the scenes to make an application on top of it. For example, `MPV`, `VLC` and `KODI` all use FFmpeg behind the scenes. Thus adding support in that backend layer opens up the possibility to integrate native IPFS (and IPNS) handling in those applications.

This proposal outlines the plan to:
* Implement IPFS and IPNS support in FFmpeg.
* Implement native IPNS and IPFS protocol support in `MPV`
* Implement native IPNS and IPFS protocol support in `VLC`
* Implement native IPNS and IPFS protocol support in `KODI`
* Develop additional `KODI` plugin to allow adding an IPFS folder.

Having IPFS/IPNS protocol support natively in FFmpeg (and in supported in the above mentioned applications) means that it becomes far easier for anyone to play media from IPFS.

Having the KODI plugin to natively add IPFS/IPNS CID's as a folder in KODI makes it very accessible to users. Furthermore, having IPFS/IPNS could mean that users potentially don't need to use protocols like SMB or NFS as files could be opened transparently through IPFS.

Lastly, and that's just a side effect of having IPFS support in FFmpeg, it could allow other applications that currently already depend on FFmpeg to easily support IPFS too. For example, `OBS Studio` or `Blender` could make use of it.

## Value
Potentially every application that uses FFmpeg could, when this proposal is executed, support video and image resources directly through IPFS and IPNS. This makes IPFS adoption one step easier and, for t he purpose of video playback, much more accessible. In the case of KODI along with the added plugin it could potentially be to use IPFS itself as the transport mechanism as opposed to SMB and NFS.

If I don't get this right then these benefits sadly will never happen. That being said, the FFmpeg part is already working with very crude preliminary patches living here: https://github.com/markg85/FFmpeg/tree/ipfs Alternatively, support for IPFS/IPNS can be implemented in each application without FFmpeg if needed. It would be far from ideal but since technically the IPFS/IPNS handling means wrapping the `<cid>` to a http url of the desired gateway, it's a fallback possibility.

For me this project does have some potential risk. I am a C++ developer, these projects are not. FFmpeg is C, KODI is C++ and Python, VLC is C, MPV is C. While they are risks, I do see them as exciting challenges! A downside is that me being quite unfamilliar with C and Python will definitely mean that i will take a bit longer to complete then a developer that has this knowledge. 

## Deliverables

### FFmpeg
Support for the IPFS and the IPNS protocols. Meaning that a command like `ffplay ipfs://QmbGtJg23skhvFmu9mJiePVByhfzu5rwo74MEkVDYAmF5T` will play the BigBuckBunny video. Likewise a `ffplay ipns://<cid>` will play the IPNS CID (provided it's a video).

### MPV
Like with `ffplay` above, the IPFS protocols (IPFS and IPNS) will be first-class-citizens and playing videos like: `mpv ipfs://<cid>` and `mpv ipns://<cid>` will work out of the box and play the video.

### VLC
IPFS protocols (IPFS and IPNS) will be first-class-citizens and playing videos like: `vlc ipfs://<cid>` and `vlc ipfs://<cid>` will work out of the box. Furthermore, the GUI in VLC for opening a network stream will be adjusted to also accept `ipfs://<cid>` and `ipfs://<cid>` URL's. However the user does it (the command line of via the gui), VLC will play the provided IPFS/IPNS CID.

### KODI
KODI doesn't have a native way or interface to play http(s) streams. Instead they need to be added in "playlist files" before they can be played (for reference: https://kodi.wiki/view/Internet_video_and_audio_streams). These playlist files will get support for `ipfs://<cid>` and `ipfs://<cid>` to allow KODI to play data from IPFS. Furthermore, calling KODI via their JSON-RPC API allows playback of `ipfs://<cid>` and `ipfs://<cid>`.

### KODI IPFS addon (add IPFS/IPNS as folder)
In KODI you can add video sources. Those are folders. They can for example be from FTP, local drive, SMB, NFS, etc... A plugin will be developed to add IPFS and IPNS as protocols there too. It will then ask the user the CID of the folder to add. That CID should be a folder on IPFS with some videos in it. KODI will display that folder and is able to play each file in it. To the user it looks just like any other folder. Note that this development work is only loosely connected to the main work of getting IPFS/IPNS support in FFmpeg and project that use FFmpeg. This KODI addon would just make much sense to have once IPFS is supported natively. Still, even if that isn't the case then having this addon would still be valuable.

## Development Roadmap
For any of the milestones. I consider them to be complete when a specific milestone is wholly completed according to the features as described for that milestone in the deliverables. 

### Milestone 1: FFmpeg gains IPFS and IPNS support upstream!
**Estimate**: 40 hours
**Staffing**: 1

#### Functionality
- `ffplay` supports the `ipns` and `ipfs` protocols. It can be called using `ffplay <protocol>://<cid>` and start playing the provided CID if that is a video.
- Internally an effort is made to use a local IPFS gateway. If that doesn't work `ffplay` falls back to playing the CID through dweb.link.
- Allow for the `-gateway <gateway>` parameter. If provided then this overwrites the internal gateway determination logic and uses just what the user provided.

#### How much time it will take
I expect the total amount of time for this milestone to not exceed 40 hours. The development is likely half of that or less with the majority of time going back and forth in mails, reaching the right people, review, feedback and documentation. 

### Milestone 2: MPV gains native IPFS and IPNS support
**Estimate**: 20 hours
**Staffing**: 1

#### Functionality
- `mpv` supports the `ipns` and `ipfs` protocols. If the user runs a local node then playing `mpv ipfs://QmbGtJg23skhvFmu9mJiePVByhfzu5rwo74MEkVDYAmF5T` will come from the local node. If the user has no node running it will come from dweb.link.
- The user is able to set the gateway through `--stream-lavf-o=gateway=custom_gateway`. Playing the same video will then come from the custom gateway. 

#### How much time it will take
MPV already integrates deep with FFmpeg. MPV furthermore exposes a subset of protocols that FFmpeg supports as native first-class-citizen protocols. Adding `IPNS` and `IPFS` to those is quite likely not a lot of work. The 20 hours definitely is a maximum extimate here.

### Milestone 3: VLC gains native IPFS and IPNS support
**Estimate**: 60 hours
**Staffing**: 1

#### Functionality
- `vlc` supports the `ipns` and `ipfs` protocols. If the user runs a local node then playing `vlc ipfs://QmbGtJg23skhvFmu9mJiePVByhfzu5rwo74MEkVDYAmF5T` will come from the local node. If the user has no node running it will come from dweb.link.
- Modules (VLC's version of protocols) have the ability to set options. The `gateway` option is possible to set which, if set, will let VLC get IPFS/IPNS data from only that gateway. If no gateway is provided then it first attempts to use the local user's gateway if it exists and use dweb.link otherwise.
- The VLC `Open Network Stream` dialog will show an example for `ipfs://bafy....` and `ipns://bafy....`. Providing such a url structure will play the media.
  - Furthermore it will also allow one to set the gateway property

#### How much time it will take
From a quick glance VLC looks to have a rather complicated structure for new first-time contributors like myself. It will likely take between 40 and 60 hours to get this feature from development to upstream.

### Milestone 4: KODI gains native IPFS and IPNS support
**Estimate**: 40 hours
**Staffing**: 1

#### Functionality
- Add support for IPFS/IPNS in KODI playlist files.
- Add support for IPFS/IPNS in KODI's JSON-RPC API to allow (remotely) sending it an `ipfs://<cid>` to playback.

#### How much time it will take
How KODI is internally using ffmpeg and how challenging it is to add support for IPFS/IPNS in the playlist files KODI can handle is a big questionmark. I expect it to not take more then 20 hours before KODI can play IPFS/IPNS content but it could take longer. I don't expect it to take longer then 40 hours which includes getting it accepted upstream.

### Milestone 5: KODI IPFS addon (add IPFS/IPNS as folder)
**Estimate**: 100 hours
**Staffing**: 1

#### Functionality
- When adding a new folder (under Browse -> Add network location), the user chooses a protocol. IPFS and IPNS are one of the protocols to choose.
- An input field for the CID to add as folder. Here supplying `CID/foo/bar` should also work.
- A default filled in input field with the auto detected local gateway.
- Gateway communication over the HTTP API.
- Show an descriptive error when the user tries to add a CID that isn't a folder.
- After adding, the user is still presented with a screen to name the folder (default KODI mechanics). If the user does nothing the CID is used as the folder. The user can change the name there.
- (once a CID is added)
  -  The user has a new folder in the `Videos` section with the name of the CID or the user chosen name.
  -  Entering the folder shows the user the files.
  -  If the users enters a file it plays
- In KODI's `Setting -> Services` there will be a new menu entry named `IPFS`.
  - The user can set the gateway to use.
  - If a local gateway was detected a warning is shown advising the user against filling in a custom gateway.
  - By default the user's local gateway is filled in.
  - The local gateway is detected on a best-effort basis. If no gateway was detected the user is prompted with a descriptive message.

#### How much time it will take
Everything regarding KODI and custom addons is totally new to me. This will make it take a bit longer. This part is also the most features of any of the deliverables. I do expect this to be manageble within 100 hours.

## Risk assessment
This section describes forseen risks for all deliverables, those are the `General risks`. Risks per deliverable are further subdivided.

### General risks
* **PR not accepted upstream.** A deliverable could be fully done and conforms to the quality standards of the individual project but still won't get accepted. I expect this risk to be near 0. But if it occurs at the ffmpeg level then this whole grant proposal will be withdrawn as it all rests on landing in ffmpeg. To mitigate this risk, work on patches for ffmpeg will start first and be the first one to send as PR to their team. Other PRs for the other milestones won't be send till ffmpeg is done.
* **PR temporarily not accepted.** There is a chance that a PR (for example MPV or KODI) will only be accepted till they themselves depend on an ffmpeg version that includes support. An effort on my part will be required to keep an eye on this and ping the right people once the PR can land.
* **Loss of interest in this project.** This project has the potential to last for half a year or even more (hence the open grant as opposed to a microgrant). If it drags out over many month it could lose my interest. Therefore in order to prevent that from happening I will develop all the parts needed for this grant rather quickly to have all the work done. It then only becomes a matter of getting the PRs accepted.
* **Technical inability to complete.** The 3 projects (VLC, MPV and KODI) all use different programming languages. KODI even has at least 2 i need to dive into, perhaps even more. There is a possibility that a change is needed in code i just don't understand (unlikely, but still). If this does occur i will first look in my own circle if someone can help. If that doesn't work out then i'll ask for help on the KODI forums. If that too doesn't work then there's the option to hire someone for an hour or so to help out. I don't expect any help is needed.
* **Incomplete but still a succesfull grant.** If ffmpeg accepts the patches (it then has IPFS support) then the fundamentals to get IPFS support in any project that uses ffmpeg are there. If for example KODI refuses to accept patches (but MPV and VLC do) then i'd still consider this grant to be a succesful grant. The aim is for all of them to accept the patches.
* **Unexpected additional things to implement.** I only went over the codebases of MPV, VLC and KODI very roughly. Enough to give me an impression of what i might need to change to add IPFS support. Still, i could very well have missed parts i need to implement but are not listed at all in this document. For that reason the time estimates are as they are to allow for moderate unexpected surprises. Fundamental big surprises that throw out the current estimate are not expected. In the worst case though, the milestone cannot be reached in the given estimated time and we'll need to re-evaluate the estimate. I do expect there to be some small surprises but nothing so big that it becomes impossible to complete in the given estimates time.


### FFmpeg (milestone 1)
* **The other projects depend on this.** MPV, VLC and KODI all depend on the support of ffmpeg. Therefore it's rather vitally important to get the ffmpeg patches out first and accepted through their PR mechanism. There is no real risk if this doesn't happen first, but it quite likely does delay the full completion of the other milestones.

### Risks specific to KODI (milestone 4)
* **Way more complicated then thought.** KODI has a large codebase and a lot of features. It's impossible to see much of it when analyzing how to support IPFS. It can therefore be possible that it's much more complicated then anticipated. The estimate of 40 hours does give some flexibility for unexpected setback but not if it turns out to be multiple times the work that I initially assumed. If that is the case then a document will be made explaining the complexities of KODI and this particular milestone will be withdrawn. It might need to be a grant project of it's own. I don't expect this to be the case!

### Risks specific to KODI addon (milestone 5)
* **Features described are impossible to implement.** I am fairly sure that the addon in general can be developed and work. I'm not sure on the details such as letting it show the default gateway that is coming from the settings. There is a possibility that specifics for the addon are not possible to be implemented in KODI's current addon structure. If that turns out to be the case then the specific parts of the addon won't be implemented. I expect that the addon is possible to implement.


## Total Budget Requested

### Total Budget

| Milestone | Developer Hours | Hourly Rate | Total |
|-|-|-|-|
| Milestone 1 | 40 | € 75 EUR | € 3,000 EUR |
| Milestone 2 | 20 | € 75 EUR | € 1,500 EUR |
| Milestone 3 | 60 | € 75 EUR | € 4,500 EUR |
| Milestone 4 | 40 | € 75 EUR | € 3,000 EUR |
| Milestone 5 | 100 | € 75 EUR | € 7,500 EUR |
| **Total** | **260** | | **€ 19,500 EUR** |

### Total Requested

**€ 19,500 EUR**


## Maintenance and Upgrade Plans

All the work will be send upstream as PRs according to their ways of receiving patches. Any changes requested during that phase will be handled by me. Based on all the projects current support of protocols I don't expect them those projects to deny proper patches.

# Team

## Team Members

- Mark Gaiser - Independent contractor / Web3 enthusiast. (Linkedin [profile](https://www.linkedin.com/in/markgaiser/))

## Team Website

None

## Relevant Experience

I have quite a bit of experience in playing with IPFS. I'm also working on making an IPFS PubSub bridge network to access PubSub via normal websites. This work is in it's early alpha phase but already working. With regards to this very proposal, I already have a working FFmpeg and MPV that uses IPFS directly.

## Team code repositories
https://github.com/markg85

Most notably repositories that are applicable to IPFS:
- FFmpeg fork (see the `ipfs` branch in there)
- ipfs-websocket-api (a project exposing PubSub as Socket.IO websockets)
- openpubsubnetwork (a project making `ipfs-websocket-api` easily accessible to web and node.js users)
