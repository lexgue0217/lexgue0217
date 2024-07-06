---
description: this page gives an introduction to routing and types of routing
---

# Introduction



## Routing&#x20;

Routing is the process of selecting path in a network along which to send data packets.



{% hint style="info" %}
Router:- These are the network devices, that perform this task by using routing tables and algorithms to determine the best path for data to travel from its source to destination.
{% endhint %}

## Routing Tables&#x20;

A routing table is a database in a router that router that stores route information about the network topology. Each entry in the routing table includes :



1. Destination Network : the IP address of the destination network.
2. Subnet Mask : Used to determine the network portion of an IP address.
3. Next Hop : The IP address of the next router to which the packet should be forwarded
4. Interface : The outgoing interface used to send the packet.
5. Metric : The cost associated with the route, used to determine the best path.
6. Route Source : Information on how the route was learned(eg, Directly connected, static, or dynamic via a routing protocol).



| Destination Network | subnet        | next hop    | Interface | Metric |
| ------------------- | ------------- | ----------- | --------- | ------ |
| 192.168.1.0         | 255.255.255.0 | 192.168.2.1 | eth0      | 1      |
| 10.0.0.0            | 255.0.0.0     | 10.0.0.1    | eth1      | 10     |
| 0.0.0.0             | 0.0.0.0       | 203.0.113.1 | eth2      | 20     |

### Routing Algorithms

Routers use various routing algorithms to determine the best path to forward packets. they are



1. Distance Vector Algorithms
2. Link-State Algorithms
3. Path Vector Algorithms



## 1.Distance Vector Algorithm

* Router using distance vector algorithm send their routing to directly connected neighbors periodically.
* Each router calculates the vest path to a destination based on the distance(usually hop count)



{% hint style="info" %}
Algorithm steps

1\) Initialization : Each router initializes its own routing table with directly connected networks and sets the distance to itself as zero.

2\) Sharing : Periodically, each router share its entire routing table with its directly connected neighbor.

3\) Updating : Routers update their routing tables based on the received information. If a shorter path found, the routing table is updated with new distance and next hop.

4\)Convergence : This process continues until all routers have consistent routing information
{% endhint %}



Example : A router with the IP address 192.168.1.1 receives a routing update from a neighbor router indicating a path network 192.168.2.0/24 with a distance of 2 hops. The router updates its table if this new route is shorter.



```sh
Router rip
version 2
network 192.168.1.0
network 192.168.2.0
```

Common Protocols :&#x20;

RIP : Routing information Protocol

&#x20;EIGRP : Enhanced Interior Gateway Routing Protocol. it is hybrid but primarily distance vector.



## 2. Link State Algorithms



* Router using link-state algorithms have a complete view of the network topology.
* Each router independently calculates the shortest path to every destination using algorithms like DIjkstra Shortest path First(SPF)



{% hint style="info" %}
Steps :&#x20;

1\)Link state advertisement (LSA): Each router discovers its neighbor and forms LSAs containing its directly connected links.

these LSAs are flooded to all routers in the network.

2\) Build network map : Each router collects LSAs from all other routers and builds a complete map (graph) of the network topology.

3\) Update routing tables : Based on SPF each router update its routing table with the shortest paths to all destinations in the network. And trigging a new calculation of Shortest path and updating of routing tables.

&#x20;
{% endhint %}

common Protocol : OSPF



## Path Vector Protocol

Path-vector algorithm, used in BGP ,focuses on inter-domain routing and allows routers to advertise path with policies and preferences.



{% hint style="info" %}
Steps&#x20;

1\) Each router start with of its directly connected neighbors and paths to them.

2\)Path advertisement and Verification : Router advertise paths to destinations along with policies and attributes. Path includes information about multiple Autonomous Systems(ASes) through which the data must travel.

3\) Policy enforcement : path vector routing allows routers to enforce policies and preferences regarding path selection, which may include preferences for certain ASes or Region.
{% endhint %}

> Common Protocol : BGP

HYBRID :&#x20;

it is the combination of both distance and link-state algorithms.

EIGPR

