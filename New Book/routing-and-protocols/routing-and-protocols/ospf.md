---
description: Open Shortest Path First
---

# OSPF

OSPF : is a widely used interior gateway protocol for routing within an autonomous system in IP networks. It is a link-state routing protocol, which means it maintains a map of the network topology and uses the Dijkstra algorithm to compute the shortest path to each destination.



### Key Features of OSPF



#### Link State Routing Protocol :&#x20;

ospf operates by having routers share information about their directly connected links with in entire network. this information is used to build a complete map of the network's topology.



#### Hierarchical Design  :&#x20;

it supports a hierarchical structure using areas. The network is divided into different areas to optimize traffic and reduce routing overhead. Area 0, also know as the backbone area, is the core of an OSPF network.



#### Cost Metric :  ospf uses a cost metric  to determine the best path to a destination.



#### Convergence : it converges quickly compared to distance vector protocol like RIP. This means it can adapt to changes in the network topology rapidly



#### Authentication : it supports several types of authentication to ensure that routing information is exchanged securely.



#### Equal cost multi path : Ospf can utilize multiple paths to a destination that have the same cost, enabling load balencing across these paths.



### OSPF OPERATIONS :&#x20;



* Neighbor Discovery
* Link-State-Advertisements(LAS's)
* Shortest path First Algorithm (SPF)
* Route Calculation



#### OSPF Packets Types :&#x20;



* Hello
* Database Description&#x20;
* Link-State Request&#x20;
* Link-State Update
* Link-State Acknowledgment



#### Ospf Areas : &#x20;

* Back Bone Area ; the core of an ospf network , all other ares must connect to the back bone area.
* Standard Area :  A regular  ospf area that has no special attribute ospf AS.
* Totally stubby Area : A cisco -Special feature , it does not receive external routes or inter-area routers, using only a default route.
* Not-so-stubby Area : similar to a stub area but can import autonomous system external routes and redistribute them.



### Key Features of OSPF&#x20;



* Link-state Advertisement
* Areas
* Route Calculation
* Metric&#x20;
* Convergence
* Authentication

#### OSPF packets types&#x20;



* Hello Packet
* Database Description Packet
* Link-state Request Packet
* Link-State update packet
* Link-state Acknowledgment packet.



### OSPF Operation Steps&#x20;



1. Neighbor Discovery : Routers send hello packets to discover and form adjacencies with neighbors.
2. Data Synchronization : Router exchange DBD packets to ensure they have the same link-state information.
3. Link-state Advertisement : Router flood LSAs to update the network topology information
4. Shortest Path Calculation : Each router the Dijkstra algorithm to compute the shortest path to every network destination.
5. Routing table Update : based on shortest path tree , routers update their routing tables.



<figure><img src="../../.gitbook/assets/Screenshot 2024-07-26 225601.png" alt=""><figcaption></figcaption></figure>
