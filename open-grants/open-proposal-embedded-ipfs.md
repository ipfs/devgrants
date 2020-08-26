# Open Grant Proposal:  `Simplified Lightweight IPFS for embedded systems` 



**Name of Project**:  _Embedded IPFS_



**Proposer**: `GeorgeTsagk` - Libre Space Foundation



**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT and APACHE2 licenses?:**

"Yes"

# Introduction


### About _Libre Space Foundation_:
Libre Space Foundation is a non-profit organization creating open source space technologies. LSF is active on several free software, open hardware and open data projects directly related to space applications and technologies while producing open-data and know how for all.

One of the most active Libre Space projects is SatNOGS, the open global satellite ground-station network. It is designed as an open source participatory project based on the users operating a ground station that is accessed via a web page for all of the network users.

Libre Space together with the University of Patras are also the makers of UPSat, the 1st free software, open-hardware cubesat.

Libre Space Foundation is also implementing the European Space Agency activity SDR Maker Space working on several open-source Software Defined Radio sub-activities, to facilitate satellite communications.


### Project Goal:
The goal of this project is to provide a simplified, yet fully functional, IPFS implementation suitable for embedded systems,
allowing embedded system networks to interoperate with the existing IPFS networks.


# Project Description

Applying the IPFS concept on embedded systems and success in exchanging information between them will show the wide field of applications that IPFS can cover and extend it even more by bootstrapping new opportunities.

At greater scales, the content-addressed concept between systems exchanging data can prove very suitable in terms of code complexity for the end user, as well as data consistency in cases of sub-system failure, without over-stressing the hardware. Such examples could be multiple-subsystem satellites or any generic network of connected devices (e.g. IoT).

The IPFS concept best serves flexible and modular decentralized networks, which is the new trend in embedded systems.

This project aims to:
* investigate the optimal way of applying an IPFS PoC on embedded systems
* provide the design and an implementation of a simple and lightweight solution
* demonstrate embedded-to-embedded utilization
* explore ways of establishing full interoperation with existing IPFS implementations


# Value

If the application of this concept proves functional, then not only is the IPFS application width extended, but it opens a lot of opportunities in integrating with existing networks.

An integrating example could be the propagation of information by using an embedded system as a node able to dynamically join / seperate from IPFS networks.

For example a literate  inter-planetary exchange of information that treats the system as the moving node which serves as the information carriage (e.g. a futuristic concept where a device being a node on Earth travels and becomes a node on Mars). In such a case, the device could also internally utilize a simplified IPFS implementation for inter-system communications.

Apart from the last example, a functional implementation of such a concept in embedded systems could be expanded in order to be used by device networks sharing data while serving many different roles (e.g. IoT). 

An unsuccessful execution of this project will give useful feedback on the simplified protocol's design.

While conducting this program of work, main challenges would include issues regarding the respect on the lightweight approach of this implementation, as well as maintaining independence by any OS.


# Deliverables

The deliverables would include (sorted by ascending order of delivery date):

* Documentation about the specifications of a PoC version of IPFS on embedded systems
* Documentation and examples of various use cases
* Implementation of the simplified IPFS (in the form of a C++ library)
* Research results of effect on embedded system's resources
* Minimalistic example of the library's usage by 2 or more systems
* List of new features and optimizations to consider for a future version
* Interoperability & integration with existing IPFS research results


# Development Roadmap



The following table describes the main checkpoints of this R&D procedure.

|                          Milestone                           |                           Details                            | Hours |         Assignees          | Funding |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :---: | :------------------------: | :-----: |
|        Complete investigation of solution's approach         | Full details on what the solution serves to the embedded systems. |  40   | `GeorgeTsagk` & `surligas` |  1400€  |
|      Complete research around application's feature set      | Documentation regarding the features that the library in its final form can support. |  40   |       `GeorgeTsagk`        |  1400€  |
|                Complete Library Architecture                 | Layout of the library and its components, including documentation about its lifecycle. |  40   | `GeorgeTsagk` & `surligas` |  1400€  |
|                   Complete Software Design                   | Definition of the library's components & functions. Definition of the end user interface. |  40   |       `GeorgeTsagk`        |  1400€  |
|                    Implementation of PoC                     | Basic functional implementation of the library with a sub-set of features present. |  240  |       `GeorgeTsagk`        |  8400€  |
|                Functional example on systems                 | Utilize the library by a network of systems, applying the IPFS over a common channel|  120  |       `GeorgeTsagk`        |  4200€  |
| Investigation about level of interoperation with existing IPFS | Report of compatibility with IPFS & interoperability with existing implementations |  60   | `GeorgeTsagk` & `surligas` |  2100€  |



#### Total Budget Requested:

The full completion of the upper roadmap would sum up a budget of  _**24,000.00 USD**_

Expenses would include:

- Engineers salary
- Administrative overhead
- Equipment procurement
- Lab expenses


# Team



* **George Tsagkarelis** - Embedded Engineer - Libre Space Foundation (GitHub: [`GeorgeTsagk`](https://github.com/GeorgeTsagk) , GitLab: [`georgetsag`](https://gitlab.com/georgetsag))
* **Manolis Surligas** - Systems Architect - Libre Space Foundation (GitLab: [`surligas`](https://gitlab.com/surligas))


# Relevant Experience

The group of LSF holds a significant amount of experience on embedded systems, showcased by a variety of previous projects.

[AX5043 Transceiver Driver](https://gitlab.com/librespacefoundation/ax5043-driver)

[HAB System](https://gitlab.com/librespacefoundation/hab)

[Qubik](https://gitlab.com/librespacefoundation/qubik) 

[Rocketry Avionics](https://gitlab.com/librespacefoundation/rocketry)

[UPSat](https://gitlab.com/librespacefoundation/upsat)

[SatNOGS Rotator Firmware](https://gitlab.com/librespacefoundation/satnogs/satnogs-rotator-firmware)
