# Determining Security Controls in a LAN

### Common Security Controls in a LAN

**LAN Threat Scenarios**

Note that these interpretations may be incorrect, as this was the part of the introduction to these topics.

| **Scenario Letter** | **Symptoms Summary** | **Hypothesis** | **Justification** |
| A | A device suddenly receives the wrong gateway | The switch which the device is connected to changes its broadcast address | If the broadcast address of a switch is changed, then a device connected to it would connect to the switch, and this data would be diverted to another router |
| B | The switch CPU spikes; many MAC addresses appear on one port | An attacker requests IP addresses on many devices from the same router | The device cannot accept any more devices, and devices on the network cannot communicate |
| C | Clients receive IPs from an unexpected source | The network settings may not be secure, so the device is easier to attack | The source is unknown, so settings might not be very secure |
| D | A new unknown device appears inside the broadcast domain | The security for letting devices join the network is weak | Someone would be able to connect more easily without valid credentials, causing risk to data |
| E | A host begins reaching other internal hosts it should never reach | The host is accidentally connected to an internal router | This allows access to internal devices since it is under the same DHCP |

The most likely explanation to be correct is explanation D. While this may not be the entire explanation, weak security controls are likely at the core of this problem. The hardest scenario to interpret would be many MAC addresses appearing on the same port. This is because nothing discussed before has covered multiple MAC addresses on the same port, and the understanding of ports in general is weak. Talking with another pair strengthened these hypotheses because they were able to be combined and refined to create more empirical hypotheses. Across all of these scenarios, the overarching cause could be attributed to weak security configurations, specifically on the router or switch.

**Task A - LAN Observation**

Note that this activity was performed on the Ubuntu Desktop VM.

The following outputs show, in order, the network interfaces and subnet, the ARP cache, a neighbor table, and routing information.

INSERT MULTIPLE OUTPUTS

From these outputs, the following are found:

**Subnet:** 192.168.64
**Default Gateway:** 192.168.64.1
**Visible Hosts:** 16:98:77:f6:04:64 (gateway), fe80::1498:77ff:fef6:464, 16:98:77:f6:04:64
**ARP/Neighbor Table Entries:** 16:98:77:f6:04:64 (gateway), fe80::1498:77ff:fef6:464, 16:98:77:f6:04:64

The ARP table and the neighbor table have very similar entries, which is a pattern suggesting that neighboring devices are likely communicated with recently. The interface of each device also shows in several of the outputs, suggesting that the interface is an important part of device identification.

An attacker could misuse the information gained from an ARP table because they would be able to find the MAC addresses of valuable devices, which could be found and manipulated. They could impersonate a device by statically assigning their IP address to the same IP address, or by changing their device's virtual MAC address. Thus, any traffic to the targeted device could be redirected to their device since a LAN cannot distinguish between two devices with the same MAC address.

**Task B - Match Observations to Possible Threats**

Two of the outputs above were chosen: the ARP table entries (`arp -n`) and the gateway information (`ip route show`).

Below is an explanation of the threats provided by gaining access to these:

| **Evidence from your VM** | **Possible Threat Enabled** | **Why?** |
| ARP Table Entries | ARP Spoofing | ARP spoofing involves associating an attacker's MAC address with one in the network (which is located in the ARP table), so an attacker could obtain a MAC address to copy |
| Gateway Information | Unauthorized Plug-In Device | Knowing gateway information could allow a device to connect directly to a network, bypassing security controls. This could also allow for administrator privileges to be gained without permission |

**Task C - Threat Mini-Simulation**

This task involves choosing a threat to analyze in-depth. The chosen threat was **MAC Flooding**.

The following information was found:

1. To successfully execute a MAC flooding attack, an attacker would first need to know how to gain access to open ports in the target network. Open ports allow packets with false MAC addresses to be sent to a switch, overflowing the MAC table.

2. MAC flooding primarily targets switches, as a switch stores a MAC address table of the devices under it. Overflowing this table forces data to be sent to all devices in the MAC table, thus letting the attacker gain access to data which is intended for specific devices under that switch.

3. One prominent change a user might notice in MAC flooding would be the worsening of device performance. Since this attack requires overflowing a MAC address table, all devices on the network will receive the data sent to any single device, which can also cause much more data to be received than expected.

4. Between the Ubuntu Desktop VM and the Linux Server VM, the Linux Server VM most resembles a device which would be targeted by MAC flooding. MAC flooding does not target individual devices, but rather switches and other controlling devices, since these devices decide where to send data and device permissions.

MAC flooding takes advantage of a key part of every LAN: the MAC address table contained in switches. Since a MAC address table must have limited capacity, MAC flooding exploits this by sending frames with false MAC addresses to the network, thus filling up the table. When a MAC address table overflows, it ensures that all data is still received by sending all network traffic to every device. Thus, an attacker could gain access to private data intended for specific devices, compromising their confidentiality.

**Final Reflection: Analysis of Both VMs**

INSERT NEIGH SCREENSHOTS OF BOTH VMS

Both of these screenshots display the ARP table entries for the respective virtual machine (Ubuntu Desktop and Linux Server). This information would be valuable to an attacker because having ARP table entries could allow for false ARP packets to be sent based on that table, creating false IP to MAC address pairings.

**Final Reflection: Five Common Internal LAN Threats**

- ARP Spoofing: sending fake ARP messages to associate the attacker's MAC address with a valid IP address; ARP spoofing takes advantage of the assumption that ARP table entries are all valid.

- MAC Flooding: 

### Physical Security Controls for Network Devices and Physical Spaces

This activity considers the security of a large medical pharmaceutical research company.

**Enterprise Physical Security Threat Analysis**

A pharmaceutical research environment may have the vulnerability of unauthorized access to the buildings themselves, as well as to certain areas in those buildings. This vulnerability specifically exists in the perimeter and primary entrances of the pharmaceutical research facility. Allowing access to buildings without permission could lead to tampering with equipment and the potential destruction and theft of property.

Access to the facilities may also not have the ability to be monitored, causing uncertainty on who is present on-site. This vulnerability affects the entirety of the facilities, as it is important to log who enters and leaves at what times. Failure to monitor access could lead to parties entering and tampering with equipment without being noticed.

Given the storage of medical substances and network control systems, temperature and humidity also pose a major vulnerability to this environment. This vulnerability applies to the research laboratories on account of the storage of chemicals, the on-site ata center, network closets, and controlled lab spaces. This presents much risk because incorrect environmental conditions could damage server devices or render certain drugs or chemicals ineffective.

With the existence of server devices and network closets, a lack of access controls to these systems is a major vulnearbility. This vulnerability affects any device which has elevated permission in the research center's network. If one were to gain access to the network closet or the ports of one of these elevated devices, they could cause harm to the network and gain access to other devices, which may hold sensitive information.

If employees are not verified or adequately trained, then they could internally pose risk to the facility, especially with elevated permissions. This vulnerability applies to all parts of the company, as any staff member could cause harm. A staff member could potentially leak company information to competitors or the personal information of test subjects.

Visitors from other companies or manufacturers to the company are a vulnerability if not vetted properly. This vulnerability could affect areas where visitors may go and anywhere where materials from outside manufacturers might be implemented. Non-vetted manufacturers could lead to the development of faulty equipment or unauthorized information being gained inside the facility, and unmonitored visitors could reveal confidential company information.



**Physical Security Plan - Pharmaceutical Research Facility**

## Project Development

## Planning and Design

## Technical Development

## Testing and Evaluation

## Reflection