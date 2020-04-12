# fwding-using-path-diversity
Cloud service based path discovery and instantiation of forwarding state on behalf of Clients
Cloud service based path discovery and instantiation of forwarding state on behalf of Clients

Multihoming common - Right now a few prefixes go through ISP1 and the rest through ISP2

This causes increase in Routing Table size

What if you had just one prefix and multiple next hops in the SRAM on routers

This way we reduce the prefixes in the routing table but provide an alternate forwarding paradigm involving Edge gateways - Assuming there is enough path diversity in the internet to get to a destination since multi-homing is common.

Client , Edge Gateway , Orchestrator , Forwarding mechanisms (multiple), Route-views server (subscriber service from them)

Mechanisms - possibly openflow and other open source mechanisms

Path diversity in the internet - explore this.

Packet forwarding using this path diversity - (a) Client end point requests specific path forwarding based on least hc, least delay, least mixed metric - (b) Client also knows about inter-AS topology and requests a forwarding mechanism to be deployed by edge gateway. - (a) edge gateway decides what to do - (b) Client has already decided the path and edge gateway provides a forwarding mechanism service

Forwarding mechanism service could be based inter-AS TE-LSP or Segment Routing paradigm.

Edge gateway subscribes to route-views and gets topology notification regarding inter-AS events (node / link notification)

Edge gateway - Build inter-as topology through route-views download and through subscription service to keep it updated - Have hop-count and delay information of various paths in the Internet (subsumes the draft sent to Swamy) - This could be subscribed to another service in the cloud which monitors such details such as hc and delay - Employ different forwarding mechanisms and possibly in packet data as well to get the packet from A to B through specific path - Get packet through specific path to destination - Reverse path service through another edge gateway close to the destination

Client asks Edge gateway for - packet forwarding service based on a specific metric or set of metrics - Can even say provide me based on hc but if not through delay or mixed metric - Then sends to edge gateway and Edge gateway performs the magic. - Edge gateway could be in touch with ISP1 - ISP1 could offer services to edge gateway to get from A to B through specific LSPs - such LSPs could be advertised as services to edge gateway based on HC and delay - ISP need not tell the edge gateway LSP specific information - but offer service as hc, delay or mixed metric - ISP1 could hide all topology details as necessary to offer such services - ISP1 then could say i) consult inter-AS topology ii) decide on path iii) instantiate forwarding mechanism to get this through iv) forward the packet
