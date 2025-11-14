# Types of Networks & Connections and Devices

### Exploring IP Addresses in Shared and Bridged Mode

**Shared Mode**

This is the output when running `ip a` in shared mode:

INSERT IP A

As shown above, the IP address in shared mode is **192.168.64.2/24**. 

Note that since this command was run in shared mode, a virtual subnet defines the network. It is also important to note that this is the **internal** IP address, which defines a device relative to the home network.

This differs from what is displayed when going to [this website](https://whatismyipaddress.com).

INSERT EXTERNAL IP

This displays the external IP address, **173.95.44.210**, which defines a network with respect to the internet as a whole.

Shared Mode Reflection:

When comparing the two IP addresses, they are completely different. The IP address **192.168.64.2/24** thus belongs to the local network, while the address **173.95.44.210** belongs to the internet. Overall, a virtual machine may use NAT/Network Address Translation if it wants to connect to the internet if the VM should be contained and managed by the host system. NAT is necessary in this case because the virual subnet containing the VM must route data to the Mac's network and out to the internet. Shared mode in general makes it easier to connect multiple virtual machines on one computer because they are all centralized under the Mac. This allows for permissions to be managed and artificially defined using the virtual subnet created by the host system.

**Bridged Mode**

Note that when switching to Bridged mode, the *Bridged Interface* must match that of the Mac's active connection the the router (WiFi/Ethernet).

This is the output after running `ip a` in bridged mode:

INSERT BRIDGED INTERNAL IP

Thus, the internal IP address when on bridged mode is **127.0.0.1/8**.

Bridged mode allows the VM to act as a device on the same LAN as the host system. However, it is classified as a separate device to the host.

When checking the external IP address, it turned out to be the same as in shared mode:

INSERT EXTERNAL IP

The IP address is exactly the same as the external address in shared mode, that being **173.95.44.210**. Thus, it is likely that the external IP address is defined based on the closest layer to the internet, which is the router of the host system in both cases.

Bridged Mode Reflection:

The internal IP address greatly changed when switching to bridged mode. In bridged mode, the device is defined relative to the Mac's network rather than a virtual network created by the Mac, so it is expected to be different. However, the external IP address remained the same regardless of which mode was used. In bridged mode, a VM ultimately acts more like a separate computer because it directly connects to the same router as the Mac, rather than acting as part of the Mac. Overall, Bridged mode may be chosen by corporations and users in general to allocate a computer's resources to VMs acting as individual devices, using time and cost efficiently. However, bridged mode carries a risk because it is not able to be managed by the host system. As such, actions can be performed which may make the host system's network vulnerable because no virtual subnet exists to contain these vulnerabilities.

**Overall Comparison**

| **Mode** | **Internal (Private) IP** | **External (Public) IP** | Notes |
| ---- | ---- | ---- | ---- |
| Shared (NAT) | 192.168.64.2/24 | 173.95.44.210 | Internal IP is defined independent of the host's network; External IP is defined by the host's network |
| Bridged (NAT) | 127.0.0.1/8 | 173.95.44.210 | Internal IP is defined by the host's network; External IP is defined by the host's network |

Bridged mode made the VM appear as its own device on the local network, while Shared mode provided a safer and more controlled environment. Overall, NAT helps to manage limited IPv4 addresses because it centralizes them under a virtual subnet and allows for the configuration of that subnet through the host device. This configuration and management also creates a more secure environment. In shared mode, data travels from the virtual machine to the host system's virtual subnet, then to the host system's LAN, then to the internet. Meanwhile, in bridged mode, data travels from the virtual machine directly to the host system's LAN, then to the internet. In both of these cases, the host system's LAN must be passed through, so this is what defines the external IP address of the VM in both cases.

**Reflection**

To summarize the information above:

The internal IP address differed while the external IP address remained the same between Shared and Bridged mode. Ultimately, this activity revealed that local networks may be created inside of other networks, creating a chain of data movement between an endpoint device (such as a VM) and the internet. The internal IP address is defined with respect to the lowest layer (that of the endpoint device), while the external IP address is defined with respect to the highest layer (usually a router). IT professionals may use different network configurations depending on the situation to manage efficiency vs. security. In a home or lab, it may be better to use a shared environment since endpoints are contained within a more secure network. This is in general useful for dealing with secure information. However, in business and tasks that require heavy use of resources, a bridged environment may be better. However, this has the downside of possibly introducing new vulnerabilities to the host's network. In the classroom, bridged mode is likely better to use since it better simulates a real computer, thus replicating real-world scenarios better. Since a classroom environment likely does not store any sensitive data, then the risks associated with bridged mode are not significant.

### Connections That Share Data and Resources

For this activity, it is useful to know what a PAN, LAN, MAN, and WAN are.

| Term | Definition|
| ---- | ---- |
| PAN | Devices communicate within a very small range of a person (a couple of meters) |
| LAN | Devices communicate within a small area, usually a building or a couple of buildings |
| MAN | Covers larger areas than a LAN (usually cities or larger areas) |
| WAN | Spans a very large area (e.g. a country) |

Below is a diagram which represents how devices interact between PAN, LAN, MAN, and WAN:

INSERT CONNECTIONS DIAGRAM

**Reflection**

On a day to day basis, all of these networks are used. A PAN is used for interaction between, for example, a cell phone and smartwatch, while a LAN is used on a home Wi-Fi network. A MAN is used to provide cellular data to a phone, and a WAN is used to gather information from the internet as a whole when performing actions such as browsing. A PAN usually connects to a LAN or MAN, mostly through Bluetooth or Wi-Fi, and a LAN, MAN, and WAN connect to each other through satellites, fiber cables, and other means. This activity ultimately displays that as the scale of a network increases, although it can handle more devices, the cost also increases because there must be many more connections between devices, while speed might also decrease because of this increased amount of connections.

### Network Topologies

Network topology - a configuration of how devices are arranged and connected in a network which shows how data travels among devices

There are two ways to interpret a topology:

- Physical topology - shows the physical layout of devices (cables, devices, routers, switches)
- Logical topology - models data movement through the network, which could differ from the physical topology

Topologies are made up of:

- End devices - tools that people use
- Networking devices - devices that control the transfer of data between devices
- Cables/wireless connections - what data actually travels through

Here are the primary topologies of networks and an example diagram for each:

Star Topology - a central networking device with each end device connected to the central device

Bus Topology - a backbone cable with each device branching off of it

Ring Topology - the devices form a circle with their neighbors, with data travelling one way only

Mesh Topology - every device has connections to multiple others, creating redundancy and reliability

Hybrid Topology - combines two or more types of topology

INSERT TOPOLOGY SCREENSHOTS

**Reflection**

For a small business, a **star topology** would likely be **easier** to implement. This is because connections only have to be made between each end device and the respective networking device (usually a router/switch). Thus, a relatively small amount of connections have to be made, and data can still travel indirectly among all devices in the network.

However, to handle the case where **one connection fails**, a **mesh topology** would work best. This is because if a connection between two devices happens to fail, there will likely be a backup connection (usually indirect) between the devices which need to communicate.

The most **expensive** topology to implement would likely be a **mesh topology** since for the same amount of devices, it requires many more cables. Depending on how many connections are desired (a partial vs. full mesh), the amount of cables can increase much.

A **school** would likely use a **hybrid topology**, made up of a star topology of switches with a star of devices with respect to each switch. This allows for centralized control of groups of devices, while also allowing management of each switch individually via the primary router.

The physical layout of a topology greatly affects speed because wires can be very long, and indirect connections could require going through several of these wires, increasing the time for data to be transferred through these wires (or through WiFi). Also, if a wire is faulty or disconnected, then depending on the layout, devices could become inaccessible.

### Ethernet Cable

INSERT THIS

### OSI and TCP/IP - Layers 1 and 2

This activity involves an exploration of layers 1 and 2 (Physical and Data Link) of the OSI layers. To begin this, an Ubuntu VM was connected to the internet, and a network connection was confirmed via `ping -c 3 google.com`.

**Data Link Layer**

To start, the active interface was found, and its information was displayed using `ip link show`:

INSERT IP LINK SHOW

The following information was obtained:

**Interface Name:** enp0s1
**MAC Address:** 1a:63:23:39:a4:2c
**Broadcast Address:** ff:ff:ff:ff:ff:ff

Note that the interface references the virtual network card of the VM, and the MAC address uniquely identifies the computer on the LAN. The broadcast address is used to send messages.

Next, the command `arp -n` was used:

INSERT ARP N

As displayed above, the IP address, MAC address, and interface of devices on the same LAN are shown.


Next, the `ip -s link` command was run to show data transmitted and received by the VM's interfaces:

INSERT IP -S LINK

For the active interface enp0s1:

**RX/Received Packets:** 6671
**TX/Transmitted Packets:** 1287
**Errors:** None

**Physical Layer**

To check details about the physical layer (actual hardware), `sudo ethtool enp0s1` was run:

INSERT ETHTOOL

The following stats were found:

**Speed (Mb/s):** 1000
**Duplex:** Full
**Link Detected:** Yes

The speed details how fast the link is. Duplex showed that data travels in both directions in this case, and the detection of a link shows that the VM is connected.

Finally, to analyze network traffic, `sudo tcpdump -c 5` was used to get 5 live packets:

INSERT TCPDUMP

The following information can be inferred from the output:

**Source MAC Address:** b6:b5:c3:cf:91:e6
**Destination MAC Address:** ff:ff:ff:ff:ff:ff
**Protocols Used:** Ethernet, BOOTP/DHCP, UDP, IPv4

To summarize the above, the source MAC address is **b6:b5:c3:cf:91:e6** while the destination MAC adddress is **ff:ff:ff:ff:ff:ff** (the broadcast address). The packets transferred are likely packets which are required for the maintaining of certain protocols or connections to the internet. This data is important for troubleshooting and network monitoring because it ensures that a stable connection is being maintained, and it shows each step of data transmission. Thus, problems can be pinpointed to certain IP and MAC addresses.

**Reflection**

INSERT REFLECTION PARAGRAPH

### Building and Testing a Small Office/Home Office (SOHO) Network

