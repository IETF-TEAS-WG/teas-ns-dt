# Introduction

This draft provides a framework and architecture for discussing transport network slices, multipoint-to-multipoint connections:

    "A transport slice is an abstract network topology connecting a number of endpoints, with expected objectives specified through a set of service level objectives (SLO)". 

This definition comes from [draft-rokui-teas-transport-slice-definition].

This framework is intended as a structure for discussing interfaces and technologies. It is not intended to be a new set of concrete interfaces or technologies. Rather,  the idea is that existing or under-the-development IETF technologies (plural) can be used to realise the ideas expressed here.

While slices are commonly discussed in the context of 5G, it is important to note that the transport network slices are a narrower concept, and focus only on a particular network connectivity aspect. Other systems, including 5G deployments, may use transport network slices as a component  to create entire systems and end-to-end constructs that match their needs.

# Requirements

It is intended that transport network slices can be created to specific requirements, typically expressed with bandwidth, latency, and other desired or required characteristics. It is intended that later these slices can be monitored, modified, deleted, and otherwise managed.

It is also intended that applications and network components wishing to use these slices can use the slices, i.e., can transport 

# Framework
... diagram ...

## Applications

... the transport slice system is used by an application. in most likely, that application is just another level slice orchestrator, e.g., the end-to-end slice orchestrator. but in theory it could also be an actual application that wants to manage some specific connectivity through the transport slice system. ...

## Expressing connectivity intents

... northbound interface ...

... data models ...

... SLOs as intents ...

... (most of this comes from the definitions draft) ...

## Mapping

... the requirements get mapped by a piece of software, the controller, to concrete technologies and the connectivity is set up ...

## Controller

...

## Underlying technology

... such as MPLS or VPNs or even physical cables ...

# Considerations

## Monitoring

... we need to instrument the slice realisation to know how it is doing + update the slice as situation changes + dynamic reconfig...

## How to deal with hierarchy

...

## Scalability

...

## Security model

... accidental or malicous interaction between slices raises new security concerns ...
