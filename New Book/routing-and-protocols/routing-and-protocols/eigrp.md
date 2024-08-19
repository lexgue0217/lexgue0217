# EIGRP

EIGRP (Enhanced Interior Gateway Routing Protocol) is a dynamic routing protocol used in computer networks. It was developed by Cisco Systems and is designed to be an improvement over its predecessor, the Interior Gateway Routing Protocol (IGRP). EIGRP is widely used in Cisco-based networks because of its efficiency, fast convergence, and ease of configuration.

#### Key Features of EIGRP

1. **Distance Vector Protocol with Advanced Features:**
   * EIGRP is a distance vector routing protocol, meaning it calculates the best path to a destination based on distance (metrics like bandwidth and delay) and vector (the next hop).
   * Unlike traditional distance vector protocols, EIGRP includes features like rapid convergence and reduced bandwidth usage.
2. **Partial Updates:**
   * EIGRP only sends updates when there is a change in the network topology, and it only sends information about the change, rather than the entire routing table. This reduces the bandwidth used by routing updates.
3. **Rapid Convergence:**
   * EIGRP quickly recalculates routes if a primary path fails, allowing for rapid convergence and reducing downtime.
4. **Uses Multiple Metrics:**
   * EIGRP uses a composite metric based on bandwidth, delay, load, and reliability to determine the best path to a destination.
   * The default metric calculation is primarily based on bandwidth and delay.
5. **Supports VLSM (Variable Length Subnet Masking):**
   * EIGRP can support networks with different subnet masks, making it flexible for complex network designs.
6. **DUAL Algorithm (Diffusing Update Algorithm):**
   * EIGRP uses the DUAL algorithm to ensure loop-free and optimal paths. DUAL ensures fast convergence and determines the best route by analyzing the feasible successors (backup routes).
7. **Scalability:**
   * EIGRP is scalable, capable of supporting large and complex network topologies with minimal configuration and management overhead.
8. **Supports IP and IPv6:**
   * EIGRP can be used for both IPv4 and IPv6 routing, making it versatile for modern network environments.
9. **EIGRP Authentication:**
   * EIGRP supports authentication, allowing for secure routing updates between routers.

#### How EIGRP Works

1. **Neighbor Discovery:**
   * EIGRP routers establish neighbor relationships with adjacent routers using Hello packets. Once neighbors are established, they exchange routing information.
2. **Topology Table:**
   * Each EIGRP router maintains a topology table with all the paths to each destination. The best path is moved to the routing table, and backup paths are kept as feasible successors.
3. **Routing Updates:**
   * EIGRP sends partial updates to its neighbors only when there are changes in the network topology. These updates include information about the specific changes rather than the entire routing table.
4. **Path Selection:**
   * The DUAL algorithm is used to select the best path based on the composite metric, ensuring the chosen route is loop-free and optimal.

#### Summary

EIGRP is a reliable, efficient, and scalable routing protocol that provides fast convergence and is easy to manage. It is commonly used in enterprise networks where Cisco equipment is prevalent.
