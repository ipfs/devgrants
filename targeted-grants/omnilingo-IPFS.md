# Targeted Grant: Omnilingo hosted on IPFS

* **Issuer:** @autonome
* **Recipients:** @nlhowell @ftyers

## Project description

We are building a language-learning app for language communities
that are either unsupported by major platforms or do not wish
to give up sovereignty over their languages. Centralised language-learning
systems privately collect user data and audio samples, trapping communities
into proprietary silos and walled gardens. With the popularisation of open
content licences and the innovation of new accessible distributed storage
systems, we can build language-learning for the decentralised web.

Our design is decentralised from the beginning, with common resources
accessible through a robust simple protocol amenable to offline, http-based, or
peer-to-peer access; user settings stored in one or more persistent stores of
the user's choice; and clients offering users maximum sovereignty over who has
their data.

This grant will allow us to implement an IPFS-based common resource storage
design and plugins for client applications to access IPFS-based common
resources. IPFS provides flexible storage and content distribution network
capabilities without the dependency on and vulnerability to a centralised
system.

## Target audience

We have several target audiences for the software.

Firstly language learners, the demo was built to scratch an itch. The second author
was taking a language class and wanted a way to practise listening comprehension. There
are no other free/open-source applications for this, and certainly no others that support
a wide range of languages or allow languages to be easily added. In terms of the size of 
the potential learner userbase, it scales with the number of language communities we serve. 

Secondly developers of other language learning applications in the free/open-source world.
There are a wide variety of applications that have a problem accessing open content in 
many languages and so cannot take advantage of the kind of scale available to enterprise
players. 

Thirdly language teachers, we have been in contact with various people with an eye to 
working out how to fit language teachers into the project as a primary stakeholder and driver
and not just as a passive user. This could for example allow them to design their own 
curricula using the data, without having to do the processing themselves. Think of it as
"distributed audio-visual building blocks for language courses".

Fourthly researchers. This would need to be worked out from a privacy perspective, but we 
would like to develop a system to allow users to locally store their behavioural/activity data and 
optionally and with full consent share it in an anonymised form with researchers in the fields
of second-language acquisition/second-language studies/linguistics/computer-aided language learning
etc. This could enable research into active learning and tailored-language learning (for example
a curriculum of clips that maximises acquisition of particular phonemic contrasts). Although
the data would be locally stored, the references/addresses of the relevant content would be 
global.

## Data characteristics

* The principle data we are interested in with respect to language data are audio 
  files and text files. These are split by language, a given language may have thousands
  of potential clips, and each one needs to be addressed and linked to metadata about 
  the clip (e.g. difficulty rating, transcript, etc.)
* To give an example, in our demo which supports 60 languages, each language has around
  10,000 audio clips, with each language having in the region of 10M-100M of clips. We are only
  currently able to use a fraction of the available data, which is in the region of 250G
  of clips with a median per language of 400M.
* The precise location of the clip does not matter, so long as it is addressable and linkable
  to the relevant metadata.

## Value

Language learning resources is an embarrassingly distributable system, and is an
opportunity to expose the large population of language learners to the
distributed web. 

## Future directions

This seed grant is intended to fund proof-of-concept work on using IPFS for decentralised
and content-addressed audio-visual content storage aimed at language learning. This is however
only a start. 

***From crowdsourcing to crowdstoring***: The popular methods of crowdsourcing language data
currently work in a centralised way. There is storage in something like EC3, and contributors
have to give up the rights over their data to participate. If there are many other options 
and people are participating for pure enjoyment this is not problematic, but if people are 
participating because they have no other option then it tends to extraction. This is particularly
highlighted when indigenous or colonised communities are involved (e.g. [Māori are trying to save 
their language from Big Tech](https://www.wired.co.uk/article/maori-language-tech)). We envisage
a more equitable approach that would allow individuals and language communities to license their data
however they see fit, but take advantage of content addressing and distributed storage to lower
the barrier to entry and to enable wide replication to avoid catastrophic data loss.

<!-- MORE HERE -->

## Deliverables

1. IPFS support for Omnilingo client applications
1. IPFS support in the Omnilingo language data toolkit
1. Demo page working with several languages with available data
1. Post about the project for the IPFS blog
1. Design of distributed voice data contribution system using IPFS
1. Scientific article describing our success published in workshop proceedings and/or on arxiv.

## Team

* @ftyers, @nlhowell - Grant recipients. Computational linguists with
  familiarity with multilingualism and experience in distributed computing and
  speech processing
* Dietrich Ayala - PL Grant advisor

## Milestones & Funding

**Total Funding Amount:** $10,000

Week | Milestone | Cost
---- | --------- | ----
   1 |  ipfs support in toolkit  design         | $1250
   2 |  ipfs support in toolkit  implementation | $1250
   3 |  ipfs support in client   design         | $1250
   4 |  ipfs support in client   implementation | $1250
   5 |  ipfs support in client   integration    | $1250
   6 |  demo of omnilingo on ipfs               | $1250
   7 |  distributed voice contrib design        | $1250
   8 |  paper and blog post                     | $1250

## Resources

* Omnilingo: https://omnilingo.xyz
* Open voice data: https://openslr.org
* A centralised language learning system: https://duolingo.com
* A centralised voice contribution system (for comparison):
  https://commonvoice.mozilla.org

## Support and Funding

This grant is funded by Protocol Labs.
