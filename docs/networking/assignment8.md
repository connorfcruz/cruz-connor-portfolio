# Physical Addressing and Logical Addressing

### Understanding Physical Addressing (MAC Addresses)

A NIC is the card which sends and receives data over a network, which has a unique physical address tied to the hardware. MAC addresses are assigned at creation of the NIC, and they do not usually change.

A MAC address contains an Organizationally Unique Identifier (OUI) and so on...

INSERT NIC 1 LABELED
INSERT NIC 2 LABELED

The MAC address on NIC 2 is exactly: **04:92:26:8A:BD:4C**

On a local network, a MAC address uniquely identifies each device, allowing data to be routed to the correct location.

The Ethernet port is used to plug in a network cable, which allows for a physical connection to be made to the NIC (Layer 1 OSI).

The PCIe connector allows for the NIC to connect to the computer's motherboard, powering it and allowing it to interact with the computer.

The NIC needs a main chip in order to process data and perform its intended function, sending and receiving frames.

The MAC address **belongs to the NIC** because MAC addresses are assigned at production, and they are unique to each device.

A MAC address is considered a physical address because it is usually hard-coded into a NIC at production. This address is not assigned by the network, but rather part of the NIC itself. Seeing a real NIC helps to understand this because its MAC address is actually printed on the NIC, meaning that the MAC address is paired to the NIC's hardware.

**Applying This Knowledge**

To get the IP address of the Mac Mini being used, `ifconfig` was used:

INSERT IFCONFIG

Full MAC Address: **14:98:77:6F:8D:DC**

OUI: **14:98:77**

This OUI was searched up on [this website](https://maclookup.app):

INSERT WEBSITE SCREENSHOTS

Vendor: Apple, Inc.

This appears to be physical hardware. This MAC address is also specified to have Unicast transmission and to have been intializes on November 25th, 2020.

**Comparison**

On the physical NIC images, the MAC address came directly from the manufacturer, listed on a sticker attached to the NIC. On the VM, the MAC address came from a virtual NIC, which simulates the function of a real NIC. Between physical and virtual MAC addresses, both store 48 bits of data and are in the form of hex digits. However, they differ in that the virtual MAC address does not have any listed manufacturer information, and it can be changed. A virtual NIC still requires a MAC address because that MAC address can uniquely identify the virtual machine on its virtual subnet.

Using *maclookup.app*, the information for various MAC addresses was found:

| **Full MAC Address** | **OUI** | **Vendor/Company Name** | **Type of Vendor** | Notes |
| ---- | ---- | ---- | ---- |
| F0:18:98:AA:BB:CC | Apple, Inc. | Physical | Likely identifies a Mac computer |
| 3C:5A:B4:11:22:33 | Google, Inc. | Physical | Likely identifies a Google device (Android) |
| 60:45:BD:12:34:56 | Microsoft | Physical | Likely identifies a Microsoft computer |
| A4:BA:DB:22:33:44 | Dell Inc. | Physical | Likely identifies a Dell computer |
| 04:1A:04:55:66:77 | WaveIP | Physical |  Possibly identifies a radio or wireless device |
| 00:50:56:AA:BB:CC | VMWare Inc. | Virtual | Likely identifies a VMware virtual machine |
| 52:54:00:12:34:56 | N/A | Virtual | Could identify a virtual NIC assigned to a VM |

Most of the physical vendors were under large tech companies (Apple, Google, etc.), suggesting that the devices identified by those respective MAC addresses are commonly used personal devices. Many virtual NICs may also not have an associated vendor. Virtualization vendors also need registered OUIs because virtual NICs must still be identified by their respective network (depending on whether it is in Bridged or Shared mode). This activity contributed to a better understanding of MAC addressing at Layer 2 because it showed that Layer 2's transmission of data **uniquely** identifies each device based on its vendor and physically encoded information.

**Connecting the Physical and Digital: Interpreting MAC Address Structure**

OUI: **14:98:77**
Device Identifier: **6F:8D:DC**

The OUI represents the manufacturer of the NIC. The OUI connects the NIC to the manufacturer because each manufacturer is assigned a certain OUI. Manufacturers must use unique OUIs because otherwise, the identification of two devices made by different companies could appear to be the same, thus risking data being transferred to the incorrect device.

A NIC needs its own unique second half because the second half allows for the device to be uniquely identified. Thus, this allows two devices of the same manufacturer to be uniquely identified on the same LAN because the router is able to assign different internal IP addresses to the respective devices (via the device identifier). This uniqueness is especially important for frame delivery because once in a LAN, frames require a physical address so that data can be routed to the correct place. Thus, if there is a conflict in MAC addresses, frames may be routed to different places accidentally or to an unintended device.

Using the labeled NIC images above, it was discovered that physical NICs store the MAC address internally in their hardware, with the MAC address usually being listed on a sticker on the NIC. Virtual machines generate MAC addresses, usually temporary ones, by taking from available addresses for that respective vendor. This allows data to be routed to the VMs in their network (either shared/virtual or bridged). Physical MACs and virtual MACs both contain 6 pairs of hex digits, with the first three identifying the manufacturer and the other three identifying the specific device. However, some virtual MACs do not have an associated vendor and company information or simply have a generic vendor. Layer 2 functions the same way regardless of physical or virtual hardware because VMs are intended to act as their own devices. Thus, to send and receive data from the VM, a MAC address must still be assigned such that frames are routed to the correct place.

Ultimately, MAC addresses are involved in Layer 2 (Data Link) of the OSI Model. MAC addresses never leave the local network because for the data to exit the router or enter into the router, the external IP address of the device is used, thus moving onto Layer 3 of the OSI Model. The use of IP addresses allows for broader communication between different networks. When frames move to a different network, the respective source and receiver MAC addresses change because data must be routed between different devices.

Every NIC, whether physical or virtual, must have a globally unique MAC address to ensure that there frames are always transmitted to the correct location on a LAN, as a MAC address specifies a certain physical location.

## Planning and Design

## Technical Development

## Testing and Evaluation

## Reflection