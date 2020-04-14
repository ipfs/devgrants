# Targeted Grant: Open Street Map hosted on IPFS + Filecoin

**Issuer:** @autonome + @mishmosh
**Recipient:** @okdistribute

## Project Description

<!-- Please fill in details about what you're trying to build. What is the purpose/context? What are the high-level requirements?

This section should be 2-3 paragraphs long. -->

We are building Peermaps, a distributed, offline-friendly alternative to commercial map providers such as Google Maps. Instead of fetching data from a centralized tile service, your computer fetches map data from other peers across the network. With the powerful inverse scaling dynamics of peer-to-peer, we can run a mapping platform at a fixed, modest cost, no matter how popular it becomes. 

We've developed a new standard format for map data that is better for decentralized contexts. [This specification can be found here.](https://github.com/peermaps/docs/blob/master/bufferschema.md) The original OSM data format is XML and is not great for random access or space efficiency. But both of these features -- small footprint and efficient access -- will be critical for practical use on a distributed storage network. A typical size for data in XML format is at least 87GB, and the OSM pbf format reduces it to 50GB. The peermaps format should be much smaller and faster by using compact buffers, triangulation, and clever indexing developed in Rust. 

This grant will help us use IPFS as a "hot" peer-to-peer storage network for Peermaps data for near-real-time access. This will be a premiere application built on IPFS that will greatly improve digital mapping. There is between 3-4GB of XML updated per week on OpenStreetMap -- we (bits.coop peermaps team) will run a node will download, diffs, and pack those changes into the Peermaps format on a regular basis. 

This script will also put OpenStreetMap data in the original (.pbf) format on the IPFS and Filecoin networks for cold storage, improving the overall resiliency and download speeds for the data. We figured this will be nice to do at the same time, since the processing node will have to downloading these large OSM files anyway, it would make sense to also upload the original (pre-processed) versions to IPFS and Filecoin.


## Value

<!-- Please describe why the work that will come out of this Targeted Grant is valuable for the IPFS ecosystem. -->


We will be able to lower costs for developers who are currently using embedded Google Maps or Mapbox, which both cost money per impression after a certain limit.

Currently a developer creating a website with a map will have to pay substantial money per impression.   For example,  1 million impressions * $0.07 = $70,000. Although there are often volume discounts, this gives you an idea of how expensive this can be for the unfortunately popular individual developer or small startup.

OpenStreetMap is an amazing example of public-interest technology and community-run critical digital infrastructure. They have managed to make a competitive product to Google maps, and they serve a substantial volume of requests. Decentralizing their storage -- both for hot and cold access -- could drastically lower costs for the community to maintain this public interest dataset. Peer to peer protocols like IPFS will be able to spread out the work of hosting very large files among all the participants in the network who are interested in a file. Centralized services can be overwhelmed if too many people want to download a file, but p2p services flip scaling on its head: the more people are downloading and sharing, the better the network works for everyone.

## Deliverables

<!-- What are you expecting the proposer to deliver at the completion of this project?-->


1. `peermaps/ingest`: A library for injesting and diffing OpenStreetMap data, handling periodic changes. This tool will convert OpenStreetMap into the Peermaps format. This deliverable is co-funded by this devgrant and SamsungNEXT;
2. Commandline tool using `peermaps/ingest` to diff .pbf files, convert to the Peermaps format, and pin both data formats on IPFS;
3. Commandline tool using `peermaps/ingest` .pbf files, convert to the Peermaps format, and pin both data formats on Filecoin 
4. Post about the project for the IPFS blog
5. Demo page with example code for map view in an HTML page (we were planning
   on doing this anyway, so not included in Milestones/Funding)
6. Report on feasability, usability, experience building on Filecoin/IPFS apis.

## Team

<!-- List the skills and experience you are looking for. Teams with this background might be a better fit for this project.-->


* @okdistribute-  Grant recipient. 3rd member of dat in 2014, peer-to-peer software developer with experience in developing mission-critical production applications.
* @substack, @mk30, @sedmonds, bits.coop - Technical advisors for peermaps
* Dietrich Ayala, Michelle Lee - PL Grant advisors

## Milestones & Funding

**Total Funding Amount:**  $17,100 <!-- List the total proposed funding amount (currently in USD, eventually can be a distribution between USD/FIL)-->

Milestone | Hours | Cost
--- | --- | ---
Research and experimentation with Filecoin and IPFS APIs, compiling report about feasibility and usability when building on both. | 16 | $1,800.00
New repository `peermaps/spec` that further formalizes the Peermaps specification depending on factors related to IPFS and Filecoin to improve performance and usability | 16 | $1,800.00
v1 of the `peermaps/ingest` library in Rust  | 64 | $7,200.00	
Documentation, automated testing suite, bug fixes, and performance enhancments as necessary for `peermaps/ingest` at v1.0.x | 32 | $3,600.00
Commandline tool to diff .pbf files, convert to the Peermaps format, and pin both data formats on IPFS  | 12 | $1,350.00
Commandline tool to diff .pbf files, convert to the Peermaps format, and pin both data formats on Filecoin  | 12 | $1,350.00
**Total** |  | 	**$17,100.00**

## Detailed Requirements & Constraints
<!-- You can use this section to detail requirements that the deliverables must include.

Also include any relevant constraints that the implementer should be aware of before beginning this project.-->

We plan to run the script on a node as soon as we get the commandline tool
ready. Long-term goal of this project (1+ years from now) is to make this
downloading/packing/indexing be done with distributed computation, rather than
on a single machine. Ideally, other groups in maplandia would be interested in
running the infra/CI and we could share the computation load.

We'd also be happy to run the script on the IPFS collaborative cluster infra as
well: https://blog.ipfs.io/2020-01-09-collaborative-clusters/. 

## Acceptance Criteria

<!-- What are the acceptance criteria for each milestone and for the final deliverables? These should be as objective as possible. They will be used to determine whether or not a grantee will receive payment for work completed for a milestone. -->

* A bash script can download the latest .pbf file from OpenStreetMap website and run the commandline tool to host the latest OpenStreetMap and Peermaps data on IPFS and Filecoin.
* A user can use an IPFS or Filecoin client to download both Peermaps and OpenStreetMap data.
* Peermaps team will maintain a mirror of this data.

## Resources

<!-- Link any resources that might be helpful for an implementer who is working on this project.-->

* OpenStreetMap weekly data dump (planet.osm, 87GB): https://planet.openstreetmap.org/
* Peermaps website: peermaps.org
* Google Maps Pricing: https://cloud.google.com/maps-platform/pricing/sheet/
* MapBox Pricing: https://www.mapbox.com/pricing/
* How to download OSM data: https://wiki.openstreetmap.org/wiki/Downloading_data
* Statistics of daily users: https://www.openstreetmap.org/stats/data_stats.html
* Diff size can range between 3-4GB of XML per week.

## Support and Funding

<!-- Who is backing this project? How will they pay the implementers? If you have not already added your information to [FUNDING](../FUNDING.md), you can do so now and link it here. Include a legal entity name if possible.

Any other organizations that choose to add their support to this Targeted Grant will do so in this section.
-->

This grant is funded by Protocol Labs.  
