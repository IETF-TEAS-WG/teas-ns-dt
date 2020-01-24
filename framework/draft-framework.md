---
title: Framework for Transport Network Slices
abbrev: Transport Network Slice Framework
docname: draft-framework-00
date:
category: info

ipr: trust200902
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
  -
    ins: E. Gray
    name: Eric Gray
    org: Ericsson
    email: eric.gray@ericsson.com
  -
    ins: J. Drake
    name: John Drake
    org: Juniper Networks
    email: jdrake@juniper.net
  -
    ins: J. Arkko
    name: Jari Arkko
    org: Ericsson
    email: jari.arkko@piuha.net

informative:
  RFC7149:
  RFC8172: 
  RFC8568: 
  I-D.nsdt-teas-transport-slice-definition: 
  I-D.ietf-teas-enhanced-vpn: 
  NGMN-NS-Concept:
   title: Description of Network Slicing Concept
   date: 2016
   author:
    - ins: NGMN Alliance
   seriesinfo:  https://www.ngmn.org/uploads/media/161010_NGMN_Network_Slicing_framework_v1.0.8.pdf 
  TS23501:
   title: System architecture for the 5G System (5GS)
   date: 2019
   author:
    - ins: 3GPP
   seriesinfo: 3GPP TS 23.501
  TS28530:
   title: Management and orchestration; Concepts, use cases and requirements
   date: 2019
   author:
    - ins: 3GPP
   seriesinfo: 3GPP TS 28.530
  BBF-SD406:
   title: End-to-end network slicing
   author:
    - ins: Broadband Forum
   seriesinfo: BBF SD-406
  
--- abstract

TBD

--- middle

# Introduction

This draft provides a framework and architecture for discussing transport slices, multipoint-to-multipoint connections:

    "A transport slice is an abstract network topology connecting a number of endpoints, with expected objectives specified through a set of service level objectives (SLO)." 

This definition comes from {{I-D.nsdt-teas-transport-slice-definition}} (to be replaced by draft-rokui-teas-transport-slice-definition).  It is the intention in this document to use terminology consistent with this and other definitions provided in that draft.

This framework is intended as a structure for discussing interfaces and technologies. It is not intended to be a new set of concrete interfaces or technologies. Rather,  the idea is that existing or under-development IETF technologies (plural) can be used to realize the ideas expressed here.

For example, virtual private networks (VPNs) have served the industry well as a means of providing different groups of users with logically isolated access to a common network.  The common or base network that is used to provide the VPNs is often referred to as an underlay network, and the VPN is often called an overlay network.  As an example technology, a VPN may in turn serve as an underlay network for transport slices.

Note: It is conceivable that extensions to these IETF technologies are needed in order to fully support all the ideas that can be implemented with slices, but at least in the beginning there is no plan for the creation of new protocols or interfaces.

Driven largely by needs surfacing from 5G, the concept of network slicing has gained traction ({{NGMN-NS-Concept}}, {{TS23501}}, {{TS28530}}, and {{BBF-SD406}}).  In {{TS23501}}, Network Slice is defined as "a logical network that provides specific network capabilities and network characteristics", and Network Slice Instance is defined as "A set of Network Function instances and the required resources (e.g. compute, storage and networking resources) which form a deployed Network Slice".  According to {{TS28530}}, an end-to-end network slice consists of three major types of network segments: Radio Access Network (RAN), Transport Network (TN) and Core Network (CN).  Transport network provides the required connectivity within and between RAN and CN portions, with a specific performance commitment.  For each end-to-end network slice, the topology and performance requirement on transport network can be very different, which requires the transport network to have the capability of supporting multiple different transport slices.

While network slices are commonly discussed in the context of 5G, it is important to note that transport slices are a narrower concept, and focus primarily on particular network connectivity aspects. Other systems, including 5G deployments, may use transport slices as a component to create entire systems and concatenated constructs that match their needs, including end-to-end connectivity.

A transport slice is a virtual (logical) network with a particular network topology and a set of shared or dedicated network resources, which are used to provide the network slice consumer with the required connectivity, appropriate isolation and specific service level objectives (SLO).  A transport slice could span multiple technology and multiple administrative domains.  Depending on the consumer's requirements, a transport slice could be isolated from other, often concurrent transport slices in terms of data, control and management planes.

Network abstraction is a technique that can be applied to a network domain to select network resources by policy to obtain a view of potential connectivity and a set of service functions.

Transport network slicing builds on the concept of resource management, network virtualization and abstraction to provide performance assurance, flexibility, programmability and modularity.  It might use techniques such as Software Defined Networking (SDN) {{RFC7149}} and Network Function Virtualization (NFV) {{RFC8172}}, {{RFC8568}} to create multiple logical (virtual) networks, each tailored for a set of services, a particular transport slice consumer, or a group of consumers that share the same (or closely similar) requirements, on top of a shared network.  How the network slices are engineered can be deployment-specific.

Thus, there is a need to create virtual network structures with required characteristics.  The consumer of such a virtual network can require a degree of isolation and performance that previously might not have been satisfied by traditional overlay VPNs.  Additionally, the transport slice consumer might ask for some level of control to their virtual networks, e.g., to customize the service paths in a network slice.

This document specifies a framework for the use of existing technologies as components to provide a transport slice service, and might also discuss (or reference) modified and potential new technologies, as they develop (such as {{I-D.ietf-teas-enhanced-vpn}}).

# Requirements

It is intended that transport slices can be created to meet specific requirements, typically expressed as bandwidth, latency, latency variation, and other desired or required characteristics. Creation is initiated by a management system or other application used to specify network-related conditions for particular traffic flows. 

And it is intended that, once created, these slices can be monitored, modified, deleted, and otherwise managed.

It is also intended that applications and components will be able to use these transport slices to move packets between the specified end-points in accordance with specified characteristics.

As an example of additional requirements that might apply to transport slices, see {{I-D.ietf-teas-enhanced-vpn}} (in particular, section 2).

# Framework

A number of transport slice services will typically be provided over a shared underlying network infrastructure.  Each transport slice consists of both the overlay connectivity and a specific set of dedicated network resources and/or functions allocated in a shared underlay network to satisfy the needs of the transport slice consumer.  In at least some examples of underlying network technologies, the integration between the overlay and various underlay resources is needed to ensure the guaranteed performance requested for different transport slices.

The users of transport slices are:

* The management system or other application that creates and manages them.
* The applications and components wishing to use these slices.

These users are served by the system that can build transport slices, as follows:

* A controller takes requests from a management system or other application, which are then communicated via an abstracted northbound interface. This interface transmits data objects that describe the needed transport slices in terms of service level objectives (SLO).
* These requests are assumed to be translated by one or more underlying systems, which establish specific transport slice instances, using specific implementation techniques (such as MPLS) implemented on top of the underlying network infrastructure.

Section 3 of {{I-D.ietf-teas-enhanced-vpn}} provides an example architecture that might apply in using the technology described in that document.

## Management systems or other applications

The transport slice system is used by a management system or other application. These systems and applications may also be a part of a higher level function in the system, e.g., putting together network functions, radio equipment, application specific components, as well as the transport slices.

## Expressing connectivity intents

The northbound interface can be used to communicate betweern users and/or providers of the transport slices and the transport slice system controller.

## Controller

The transport slice controller takes abstract requests for transport slices and implements them using a suitable underlying technology. 

## Mapping

The main task of the transport slice controller is to map abstract transport slice requirements to concrete technologies and establish the required connectivity, and ensuring that required resources are allocated to the transport slice.

## Underlying technology

There are a number of different technologies that can be used, including physical connections, MPLS, TSN, Flex-E, etc.

See {{I-D.ietf-teas-enhanced-vpn}} - section 4 - for instance, for example underlying technologies.

<Note: do we want to add to the list of candidate technolgies in the enhanced VPN draft?  It should not be the intention that this document should provide an exhaustive list.>

A transport slice can be realized in a network, using specific underlying technology or technologies.  The creation of a new transport slice will be initiated with following three steps:

* Step 1:  A higher level system requests connections with specific  characteristics via NBI.

* Step 2:  This request will be processed by a Transport Slice Controller which specifies a mapping between northbound request to  any IETF Services, Tunnels, and paths models.

* Step 3:  A series of requests for creation of services, tunnels and paths will be sent to the network to realize the trasport slice.

It is very clear that regardless of how transport slice is realized in the network (i.e. using tunnels of type RSVP or SR), the  definition of transport slice does not change at all but rather  its realization.

# Considerations

## Monitoring

Transport slice realization needs to be instrumented in order to track how it is working, and it might be necessary to modify the transport slice as requirements change. Dynamic reconfiguration might be needed.

## Security Considerations

Transport slices might use underlying virtualized networking.  All types of virtual networking require special consideration to be given to the separation of traffic between distinct virtual networks, as well as some degree of protection from effects of traffic use of underlying network (and other) resources from other virtual networks sharing those resources.

For example, if a service requires a specific latency, then that service can be degraded by added delay in transmission of service packetws through the activities of another service or application using the same resources.

Similarly, in a network with virtual functions, noticeably impeding access to a function used by another transport slice (for instance, compute resources) can be just as service degrading as delaying physical transmission of associated packet in the network.

While a transport slice might include encryption and other security features as part of the service, consumers might be well advised to take responsibility for their own security needs, possibly by encrypting traffic before hand-off to a service provider.

## Privacy Considerations
Privacy of transport nework slice service consumers must be preserved.  It should not be possible for one transport slice consumer to discover the presence of other consumers, nor should sites that are members of one transport slice be visible outside the context of that transport slice.

In this sense, it is of paramount importance that the system use the privacy protection mechanism defined for the specific underlying technologies used, including in particular those mechanisms designed to preclude acquiring identifying information associated with any transport slice consumer.

# Acknowledgments

The entire TEAS NS design team and everyone participating in those discussion has contributed to this draft. Some text fragments in the draft have been copied from the {{I-D.ietf-teas-enhanced-vpn}}, for which we are grateful.