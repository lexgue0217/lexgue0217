---
description: Border Gateway Protocol
---

# BGP

BGP stands for Border Gateway Protocol, which is the protocol used to exchange routing information between different networks on the internet. Here’s a brief overview of its key concepts and functions:

#### Key Concepts:

1. **Autonomous System (AS):** A collection of IP networks and routers under the control of a single organization that presents a common routing policy to the internet.
2. **BGP Peers (Neighbors):** Routers that have established a BGP session to exchange routing information.
3. **BGP Sessions:**
   * **eBGP (External BGP):** BGP session between routers in different autonomous systems.
   * **iBGP (Internal BGP):** BGP session between routers within the same autonomous system.
4. **Path Vector Protocol:** BGP is a path vector protocol that maintains the path information that gets updated dynamically as the network topology changes.

#### Functions of BGP:

1. **Route Advertisement:** BGP advertises IP prefixes (routes) and the AS path that data packets should take to reach those prefixes.
2. **Path Selection:** BGP selects the best path to reach a destination based on various attributes like AS path length, next hop, and multi-exit discriminator (MED).
3. **Policy-Based Routing:** BGP allows network administrators to define routing policies to control the advertisement and selection of routes.
4. **Loop Prevention:** BGP uses the AS path attribute to prevent routing loops by rejecting routes that contain the AS number of the router.

#### Attributes in BGP:

1. **AS Path:** Lists the ASes that a route has traversed. It helps in loop prevention and path selection.
2. **Next Hop:** Indicates the next hop IP address to reach a particular destination.
3. **Multi-Exit Discriminator (MED):** Used to convey the preferred path into an AS when multiple entry points are available.
4. **Local Preference:** Indicates the preferred path for outgoing traffic from the AS.

#### BGP Operations:

1. **Establishing BGP Sessions:** BGP peers establish a TCP connection on port 179 and exchange Open messages to establish the session.
2. **Route Exchange:** Once the session is established, BGP peers exchange routing information through Update messages.
3. **Route Maintenance:** BGP continuously monitors the health of the session and the routes exchanged. If changes are detected, BGP updates the routing tables accordingly.

#### BGP Security:

* **Route Filtering:** Ensures only trusted routes are accepted and advertised.
* **Prefix Filtering:** Prevents the propagation of incorrect or malicious route advertisements.
* **BGP Authentication:** Uses MD5 or more advanced techniques to secure BGP sessions.

BGP is a crucial component of the internet's routing infrastructure, ensuring that data can travel efficiently and reliably between different networks across the globe.



```
// Router bgp 50
bgp router-id 1.1.1.1
neighbor 10.0.0.2 remote-as 10
network 192.168.1.0 mask 255.255.255.0
neighbor 11.0.0.2 remote-as 20
neighbor 12.0.0.2 remote-as 20

```
