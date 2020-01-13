# Introduction

This draft provides a framework and architecture for discussing transport network slices, multipoint-to-multipoint connections:

    "A transport slice is an abstract network topology connecting a
    number of endpoints, with expected objectives specified through
    a set of service level objectives (SLO)". 

This definition comes from [draft-rokui-teas-transport-slice-definition].

This framework is intended as a structure for discussing interfaces and technologies. It is not intended to be a new set of concrete interfaces or technologies. Rather,  the idea is that existing or under-the-development IETF technologies (plural) can be used to realise the ideas expressed here.

Note: It is conceivable that extensions to these IETF technologies are needed in order to fully support all the ideas that can be implemented with slices, but at least in the beginning there is no plan for the creation of new protocols or interfaces.

While slices are commonly discussed in the context of 5G, it is important to note that the transport network slices are a narrower concept, and focus only on a particular network connectivity aspect. Other systems, including 5G deployments, may use transport network slices as a component  to create entire systems and end-to-end constructs that match their needs.

# Requirements

It is intended that transport network slices can be created to specific requirements, typically expressed with bandwidth, latency, and other desired or required characteristics. The creation is initiated by a management system or other application that wishes to specify network-related conditions for a particular traffic flows. It is intended that later these slices can be monitored, modified, deleted, and otherwise managed.

It is also intended that applications and components wishing to use these slices can use the slices, i.e., can move packets between the specified end-points in accordance with the specified characteristics such as bandwidth.

# Framework

The users of the transport network slices are:

* The management system or other application that creates and manages them.
* The applications and components wishing to use these slices.

These users are served by the system that can build the network slices:

* A controller that can take requests from the management system or other application, which are communicated in the northbound interface. This interface transmits data objects that describe the needed transport network slices.
* The transport network slices, which use specific implementation techniques (such as MPLS). These are in turnimplemented on top of the underlying network infrastructure.

## Management systems or other applications

The transport slice system is used by a management system or other application. These systems and applications may also be a part of a higher level function in the system, e.g., putting together network functions, radio equipment, application specific components, as well as the transport network slices.

## Expressing connectivity intents

The northbound interface can be used to communicate betweern users of the transport network slices and the transport network slice system controller.

## Controller

The controller takes requests for slices and actually implements them using a suitable underlying technology such as MPLS. The controller is a piece of software. 

## Mapping

The main task of the controller is to map abstract transport network slice requirements to concrete technologies and set up the connectivity.

## Underlying technology

There are a number of different technologies here, ranging from physical standard connections to MPLS, TSN, Flex-E, etc.

# Considerations

## Monitoring

Sice realisation needs to be instrumented in order to track how it is working, and it is necesary update the slice as situation changes. Dynamic reconfiguration may be needed.

## Security model


