# Default Routing

Default routing is a method used in networking to define a path for packets to take when no specific route is defined for their destination. In Cisco Packet Tracer, configuring default routing involves setting a default route on a router, which directs packets to a specified gateway if no other route is available.

#### Why Use Default Routing?

* **Simplifies Configuration**: Reduces the need for multiple static routes, especially in smaller networks.
* **Backup Path**: Provides a fallback path if no other specific route matches the destination IP address.

#### Step-by-Step Guide to Configuring Default Routing in Cisco Packet Tracer

#### Step 1: Create the Network Topology

1. Open Cisco Packet Tracer.
2. Create a simple network topology with at least two routers (Router1 and Router2), one switch, and a few PCs.
3. Connect the devices appropriately using cables.

#### Step 2: Configure IP Addresses

Assign IP addresses to the interfaces of both routers. Here’s an example setup:

**Router1 Configuration**

1. Select Router1 and go to the CLI tab.
2.  Enter global configuration mode and assign IP addresses:

    ```plaintext
    plaintextCopy codeRouter1> enable
    Router1# configure terminal
    Router1(config)# interface gigabitEthernet 0/0
    Router1(config-if)# ip address 192.168.1.1 255.255.255.0
    Router1(config-if)# no shutdown
    Router1(config-if)# exit
    Router1(config)# interface serial 0/0/0
    Router1(config-if)# ip address 10.0.0.1 255.255.255.252
    Router1(config-if)# no shutdown
    Router1(config-if)# exit
    ```

**Router2 Configuration**

1. Select Router2 and go to the CLI tab.
2.  Enter global configuration mode and assign IP addresses:

    ```plaintext
    plaintextCopy codeRouter2> enable
    Router2# configure terminal
    Router2(config)# interface gigabitEthernet 0/0
    Router2(config-if)# ip address 192.168.2.1 255.255.255.0
    Router2(config-if)# no shutdown
    Router2(config-if)# exit
    Router2(config)# interface serial 0/0/0
    Router2(config-if)# ip address 10.0.0.2 255.255.255.252
    Router2(config-if)# no shutdown
    Router2(config-if)# exit
    ```

#### Step 3: Configure Default Routing

**On Router1**

1.  Enter global configuration mode and set the default route to Router2:

    ```plaintext
    plaintextCopy codeRouter1(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.2
    ```

**On Router2**

1.  Enter global configuration mode and set the default route to Router1:

    ```plaintext
    plaintextCopy codeRouter2(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1
    ```

#### Step 4: Verify the Configuration

1.  Check the routing table on Router1:

    ```plaintext
    plaintextCopy codeRouter1# show ip route
    ```

    You should see a route like this:

    ```plaintext
    plaintextCopy codeGateway of last resort is 10.0.0.2 to network 0.0.0.0
    ```
2.  Check the routing table on Router2:

    ```plaintext
    plaintextCopy codeRouter2# show ip route
    ```

    You should see a route like this:

    ```plaintext
    plaintextCopy codeGateway of last resort is 10.0.0.1 to network 0.0.0.0
    ```

#### Step 5: Test the Connectivity

1.  Ping from a PC in Router1's network to a PC in Router2's network:

    * Select a PC connected to Router1's network.
    * Open the Command Prompt and use the `ping` command to ping a PC in Router2's network.

    ```plaintext
    plaintextCopy codeping 192.168.2.2
    ```
2. If everything is configured correctly, the ping should be successful, indicating that the default route is working as expected.

#### Example Configuration Summary

**Router1**

```plaintext
plaintextCopy codeenable
configure terminal
interface gigabitEthernet 0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
interface serial 0/0/0
 ip address 10.0.0.1 255.255.255.252
 no shutdown
exit
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

**Router2**

```plaintext
plaintextCopy codeenable
configure terminal
interface gigabitEthernet 0/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown
exit
interface serial 0/0/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown
exit
ip route 0.0.0.0 0.0.0.0 10.0.0.1
```

This configuration sets up default routing on both routers, allowing for communication between networks connected to each router. Adjust the IP addresses and interfaces as per your specific network setup.
