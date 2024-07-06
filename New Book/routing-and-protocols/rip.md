---
description: Routing Information Protocol
---

# RIP

Routing RIP is a dynamic distance vector protocol in local and wide area network. It standardize in  1980, easy to implement and configure.

Configuration&#x20;

```sh
Router 1                                  router 2               
router rip                             router rip
version 2                              version 2
network 192.168.1.0                    network 192.168.2.0
network 192.168.2.0                    network 192.168.1.0
network 10.0.0.0                       network 10.0.0.0
network 11.0.0.0                       network 11.0.0.0

```



<figure><img src="../.gitbook/assets/Screenshot 2024-07-07 002124.png" alt=""><figcaption></figcaption></figure>
