# Routing and types



## Static Routing :&#x20;

it is a types of routing technique where the routers are manually configured and set by a network administrator.

* its is simple to implement and no routing protocol overhead
* cons: Does not change any implementation automatically and  only manual update.

Example :&#x20;

to configure a static route to the 192.168.136.25/24 network via to the next hop at 192.168.137.44 you would enter like below



```sh
router(configure)ip route 192.168.136.25 255.255.255.0 192.168.137.44

```



## Dynamic Routing :&#x20;

Dynamic routing is process of finding the best path for the data to travel over a network in this process a router can transmit data through various different routes and reach its destination on the basis of the conditions at the time of communication circuits.

There are three types of Dynamic routing&#x20;



1. Distance Vector
2. Link-State
3. Hybrid



### Distance vector routing Protocol :&#x20;

Router determines the best path based on distance metrics

ex: RIP && IGRP

small to medium sized networks



### Link-State Protocol :&#x20;

Routers have a complete map of the network topology and use "algo" to calculate the shortest path to each destination.

ex : OSPF && IS-IS (intermediate system- Inter systems)

Large , complex network can used.



### Hybrid Routing Protocols :&#x20;

this is the combination of both distance and link-state.

ex : EIGRP

used in medium and large network.



## Default Routing :&#x20;

the route takes effect when no other route is available for an ip destination address.



{% hint style="info" %}
Static Routing Practical

<img src="../.gitbook/assets/Screenshot 2024-07-06 234152.png" alt="" data-size="original">
{% endhint %}
