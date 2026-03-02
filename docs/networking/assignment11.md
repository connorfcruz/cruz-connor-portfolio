# Routing

### Your Machine's Layer 3 Identity

**Investigation 1: The Layer 3 Identity**

The following information was gathered for each VM (Ubuntu and Linux): IP address, interface names, and routing table entries.

These were gained via the `ip addr` and `ip route` commands, as shown below:

Ubuntu:

INSERT COMMANDS

Linux:

INSERT COMMANDS

In the above commands, IP address could be found in `ip addr` under *enp0s1*, and interface names were also listed. Routing table entries are listed in order under `ip route`.

Ubuntu:

- IPv4 Address: **10.12.26.143**
- Interface Names: **lo, enp0s1**
- Routing Table Entries: **default (10.12.16.1), 10.0.1.28, 10.0.1.34, 10.0.1.38, 10.12.16.0**

Linux:

- IPv4 Address: **10.12.27.165**
- Interface Names: **lo, enp0s1**
- Routing Table Entries: **default (10.12.16.1), 10.12.16.0**

The IPv4 addresses for these VMs are listed above. They are also both on the **enp0s1** network. A default route is present in both VMs, as shown in the output of `ip route` under *default via*. The gateway device for both is **10.12.16.1**.

In general, the information for a device to send information to itself, devices on its subnet, and devices outside of its subnet is present in the **routing table** (obtained through `ip route`). The default gateway allows connection to other devices outside the subnet, and the other entries provide information to connect to devices on the subnet. The *lo* interface in `ip addr` also allows for a device's connection to itself via the IP address 127.0.0.1. If the default gateway disappeared, then the VM would not be able to communicate with any devices outside of its subnet.

**Investigation 2: Sending Traffic**

Case 1: Send Traffic to Itself (Loopback)

The command `ping -c 3 127.0.0.1` was run to ping the device itself via loopback:

INSERT PING 127.0.0.1

The traffic does not leave the machine because the loopback interface is handled internally and contained in the respective device's hardware. The routing table does not need a gateway entry for this to work because a gateway entry only facilitates communication outside of the subnet.

Case 2: Send Traffic to the Other VM (Same Network)

The ping command was run again with the other VM's IP (10.12.27.165) to test communication:

INSERT PING 10.12.27.165

Ubuntu dd not send this traffic to the default gateway because the other VM should be on the same subnet, so no communication outside of the network is necessary. The routing table entry which allows direct delivery can be found through the entry with "scope link", which was found to be **10.12.16.0** in the routing table. This can be proven by running `ip route` and analyzing the output. This is also supported by a slightly longer transmission time than loopback.

Case 3: Send Traffic Off the Network

The Ubuntu VM then pinged Google's IP address (8.8.8.8.8) to simulate external transmission of data:

INSERT PING 8.8.8.8

The routing table entry which made this possible is the default gateway, found under **default via** in the routing table. Ubuntu cannot deliver this directly because the router sits as the only way for data to exit the network, so data must pass through it first. This is supported by the transmission times being significantly longer than the other cases. The router device handled the first step outside of the network.

**Investigation 3: How the Decision is Made**

Predictions:

If traffic is sent to the other VM (Linux), the next hop would be direct since no external communication is required. If traffic is sent to 8.8.8.8 (Google), the next hop would be gateway since this does require external communication.

**Reflection**

The role of the routing table is to serve as a guide for where a device can communicate and what the best path of transmission is. The role of the default gateway is to provide a path for external communication, allowing access to devices outside of the current subnet. This was proven when communicating with *8.8.8.8*, as `traceroute` showed that the default gateway was one of the hops. For direct delivery, the devices communciating must be on the same network/subnet, as this can only be done if the devices know each other's MAC addresses (which can be found via a MAC address table). Communication with devices outside of the network requires router involvement because the default gateway must first be accessed to reach that device.

## Project Overview

## Planning and Design

## Technical Development

## Testing and Evaluation

## Reflection