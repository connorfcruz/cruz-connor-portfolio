# Switch Security

### Common LAN Threats & Why Switches Are Vulnerable

**Initial Security Thinking**

The easiest device for an attacker to compromise in a LAN would likely be the switch. Other personal devices usually have security features such as antiviruses and policies to monitor their ports, but an unconfigured switch could allow an attacker to simply connect to an open port. Being "inside" the network makes a device more dangerous than being outside the network. A device inside the network can communicate with other devices in the network, which may allow an attacker to potentially compromise other devices and elevate privileges. A typical device can likely see every other device in a network by default. Since there is no segmentation by default, the device would be able to see any other device in the broadcast domain, which is essentially every device on the network.

**LAN Threat Scenario Observation Table**

| **Scenario** | **Symptoms** | **Hypothesis** | **Justification** |
| -- | -- | -- | -- |
| The default gateway address of several devices is different than expected. | Devices lose internet access, webpages load very slowly or not at all, different default gateway address than expected, no official changes to network, devices still have valid IP addresses | An unauthenticated DHCP server may have been used to give incorrect IP addresses to the devices. | This would cause a different gateway to be listed based on the DHCP server, and it would cause a different router to be listed, which matches expectations. |
| Hundreds of MAC addresses appear to be learned on a single switch port in a very short time. | Network performance is inconsistent, switch shows unusually high CPU usage, issue appears suddenly | An attacker gained access to a specific port and send many invalid ARP requests. | The threat seems to be centered around the port itself, and sending invalid ARP requests would add false MAC address entries to the ARP table. |
| Some devices connecting to the LAN receive IP addresses on the wrong subnet. | Internal resources can't be accessed, some are redirected to unexpected DNS servers, IP information is received quickly, DNS and gateway values are inconsistent | An attacker gained access to the DNS resolution settings of the network and redirects network traffic to undesired locations. | An attack on DNS would not affect the rate of receiving IP information, but rather change the information received. An attack on DNS would also explain the redirects. |
| A previously unseen device appears inside the LAN and communicates with other hosts, and there is activity originating from a wall jack. | The device appears suddenly, traffic patterns resemble a normal workstation, the device has access to other hosts | An attacker connected a personal device to an unmonitored Ethernet port. | This would give them access to the network if port security controls are not enforced well, and the device would act as a normal device in the network. |
| A student workstation is observed communicating with internal systems that should be restricted. | Administrative and server devices are accessed, communication occurs entirely inside the LAN, no authentication failures | The student workstation has permission to communicate with any device on the network due to unassigned permissions. | Since there is no VLAN segmentation, by default, any device can communicate with and read data from any other device. |

**LAN Observation**

