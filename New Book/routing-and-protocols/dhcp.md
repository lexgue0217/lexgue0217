# DHCP

Sure, here's an example of a basic DHCP server configuration. We'll cover a configuration on a Linux-based system using the `isc-dhcp-server` package, which is a common DHCP server implementation.

#### Installing DHCP Server

On a Debian-based system (like Ubuntu), you can install the `isc-dhcp-server` package with:

```bash
bashCopy codesudo apt update
sudo apt install isc-dhcp-server
```

#### Configuring DHCP Server

The main configuration file for the `isc-dhcp-server` is usually located at `/etc/dhcp/dhcpd.conf`. Here's a simple configuration example:

```bash
bashCopy code# Sample DHCP configuration file

# Define the default and max lease times
default-lease-time 600;
max-lease-time 7200;

# Specify the domain name and DNS servers
option domain-name "example.com";
option domain-name-servers ns1.example.com, ns2.example.com;

# Declare the subnet and specify the range of IP addresses to be distributed
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.100;
    option routers 192.168.1.1;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option domain-name-servers 192.168.1.1, 8.8.8.8;
}

# Static IP assignment for specific clients (optional)
host printer {
    hardware ethernet 00:1A:2B:3C:4D:5E;
    fixed-address 192.168.1.50;
}

host server {
    hardware ethernet 00:1A:2B:3C:4D:5F;
    fixed-address 192.168.1.60;
}
```

#### Key Configuration Directives

* `default-lease-time`: Specifies the default lease time (in seconds) for IP addresses assigned by the DHCP server.
* `max-lease-time`: Specifies the maximum lease time (in seconds) for IP addresses assigned by the DHCP server.
* `option domain-name`: Sets the domain name to be used by the clients.
* `option domain-name-servers`: Specifies the DNS servers to be used by the clients.
* `subnet`: Defines the subnet and network configuration.
  * `range`: Specifies the range of IP addresses that can be assigned to clients.
  * `option routers`: Specifies the default gateway for the subnet.
  * `option subnet-mask`: Sets the subnet mask for the subnet.
  * `option broadcast-address`: Defines the broadcast address for the subnet.
* `host`: Configures static IP assignments based on the client's MAC address.

#### Starting and Enabling the DHCP Server

After configuring the DHCP server, start the service and enable it to start on boot:

```bash
bashCopy codesudo systemctl start isc-dhcp-server
sudo systemctl enable isc-dhcp-server
```

#### Verifying DHCP Server Status

You can check the status of the DHCP server with:

```bash
bashCopy codesudo systemctl status isc-dhcp-server
```

This basic configuration should be sufficient to set up a DHCP server on a small network. For more complex configurations, refer to the `isc-dhcp-server` documentation or consult additional resources based on your specific requirements.



### Cisco Packet tracer configuration&#x20;



Configuring a DHCP server on a Cisco router in Cisco Packet Tracer involves a few steps. Here is a step-by-step guide to setting up a DHCP server on a Cisco router:

#### Step 1: Create the Network Topology

1. Open Cisco Packet Tracer.
2. Create a network topology with at least one router, one switch, and a few PCs.
3. Connect the devices appropriately using cables.

#### Step 2: Configure the Router

1. Select the router and go to the CLI tab.
2.  Enter global configuration mode:

    ```plaintext
    plaintextCopy codeRouter> enable
    Router# configure terminal
    ```
3.  Define the DHCP pool:

    ```plaintext
    plaintextCopy codeRouter(config)# ip dhcp pool NAME
    ```

    Replace `NAME` with a descriptive name for the DHCP pool.
4.  Define the network and subnet mask for the DHCP pool:

    ```plaintext
    plaintextCopy codeRouter(dhcp-config)# network 192.168.1.0 255.255.255.0
    ```
5.  Define the default gateway (router's IP address) for the DHCP clients:

    ```plaintext
    plaintextCopy codeRouter(dhcp-config)# default-router 192.168.1.1
    ```
6.  Define the DNS server for the DHCP clients (optional):

    ```plaintext
    plaintextCopy codeRouter(dhcp-config)# dns-server 8.8.8.8
    ```
7.  Define the domain name for the DHCP clients (optional):

    ```plaintext
    plaintextCopy codeRouter(dhcp-config)# domain-name example.com
    ```
8.  Exit DHCP configuration mode:

    ```plaintext
    plaintextCopy codeRouter(dhcp-config)# exit
    ```

#### Step 3: Exclude IP Addresses (Optional)

If there are specific IP addresses you don't want to be assigned by DHCP (e.g., addresses reserved for servers or network devices), you can exclude them:

```plaintext
plaintextCopy codeRouter(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
```

This command excludes the IP addresses from 192.168.1.1 to 192.168.1.10 from being assigned by the DHCP server.

#### Step 4: Configure Interfaces

Assign IP addresses to the router interfaces:

```plaintext
plaintextCopy codeRouter(config)# interface gigabitEthernet 0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

#### Step 5: Verify the DHCP Configuration

1.  Check the DHCP bindings to verify that IP addresses are being assigned:

    ```plaintext
    plaintextCopy codeRouter# show ip dhcp binding
    ```
2.  Check the DHCP pool statistics:

    ```plaintext
    plaintextCopy codeRouter# show ip dhcp pool
    ```

#### Step 6: Configure PCs to Obtain IP Addresses Dynamically

1. Select a PC, go to the Desktop tab, and open the IP Configuration tool.
2. Set the IP Configuration to DHCP.

The PC should now receive an IP address from the DHCP server configured on the router.

#### Example Configuration

Here's a summary of the complete configuration:

```plaintext
plaintextCopy codeenable
configure terminal
ip dhcp excluded-address 192.168.1.1 192.168.1.10
ip dhcp pool MY_POOL
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 8.8.8.8
 domain-name example.com
exit
interface gigabitEthernet 0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
```

This configuration sets up a basic DHCP server on a Cisco router in Cisco Packet Tracer. Adjust the IP addresses, subnet masks, and other parameters to fit your specific network requirements.

