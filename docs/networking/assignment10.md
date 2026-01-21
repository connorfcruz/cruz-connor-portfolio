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

The following output displays the ARP table for the devices on the LAN via `ip neigh`:

INSERT IP NEIGH

An attacker could misuse this information by keeping in mind the IP address paired to the MAC address of a device with elevated privileges. An attacker could use this to their advantage by responding to requests for the device's IP address, thus pairing the attacker's unverified MAC address with the verified IP address.

**Wrap-Up**

The threat scenario with a previously unseen device connecting to a wall jack seems the most realistic. If a school's network is not properly configured, then this could happen unintentionally by connecting a student or other device to the respective wall jack, possibly for charging.

It was also surprising that, inside of a switched LAN with no segmentation, a normal device can see all other device activity and communicate with other devices. This was especially surprising because these are the default settings for a network, rather than an altered state.

### Switch Security Controls - From Observations to Decisions

**Basic Vocabulary**

- Threat - an attack on a network which takes advantage of a vulnerability
- Vulnerability - a weakness in the security of a network
- Control - a means to combat threats or decrease vulnerability
- Prevent vs. Mitigate - preventing is to completely remove a vulnerability, while mitigating is to lessen a vulnerability

**Visualizing Switch Security With Packet Tracer**

This activity involves the creation of a small LAN using Cisco Packet Tracer and the enabling and monitoring of security controls on its respective switch.

| VM Evidence | Vulnerability | Control | Why This Control Mitigates Risk |
| -- | -- | -- | -- |

INSERT LATER

### Explain, Design, and Defend a Secure Switched LAN


**Mini-Threat Simulation**

The "Compromised Teacher Laptop" scenario was chosen arbitrarily, where a teacher's laptop is infected with malware after opening a phishing email while connected to the school network.

Analysis:

To execute this attack, the attacker must have the teacher's contact information and software that can infect one's system from the browser.

The most directly targeted devices of this attack are the device being compromised and devices on the same subnet, since devices on unconfigured subnets can see all other devices on that subnet.

The only user who would likely notice this attack is the user whose device is compromised, whether that be through increased CPU usage or unfamiliar software.

The Ubuntu Desktop VM best resembles the attacker's perspective because the device being attacked is a common user device. A teacher probably does not have elevated permissions on a school network, so the Ubuntu Desktop VM is mores suitable due to its function as a common device.

**Scenario: School LAN**

The following is a sketch of the proposed network:

INSERT NETWORK SKETCH

Trust and Restrictions:

- Students -> Servers: Denied; Student should not be able to obtain server information and modify the servers
- Students -> Teacher: Restricted; Students should not have access to teacher information, such as grades, but communication should be allowed
- Students -> Administration: Denied; Students should not have access to administration since it manages other devices
- Teachers -> Servers: Denied; Nothing should be able to communiacte with servers except administration
- Administration -> Servers: Restricted; Server access should be allowed to administration but limited for safety

**Trust Enforcement**

The VLAN which should be least trusted is the student VLAN since students should not have the authority and do not have the experience to deal with devices other than their own. The VLANs which require the most protection are VLANs 30 and 40 (Administration and Servers) since they have the most sensitive information and control other devices. The switch should also be the most strict on the Administration and Server VLANs due to the possibility of tampering with other devices.

**Control Layering**

VLANs alone do not fully secure a design because devices can still communicate with each other within each VLAN, and their permissions are not managed at all. Thus, attackers are still able to compromise a device in one VLAN and easily compromise the other devices in the same VLAN. This statement is supported by the mini-task simulation, as neighboring devices in the same VLAN could be easily affected if one device is compromised in the scenario. DHCP snooping is necessary in addition to VLANs because it protects Layer 3 of the OSI layers, mitigating the risk of false IP address assignments and the bypassing of the restrictions set by VLAN segmentation. Dynamic ARP inspection also relies on DHCP snooping because DAI trusts that the ARP table is correctly assigned, and DHCP snooping ensures that IP to MAC address mappins are correct. ACLs are still needed after segmentation to control the permissions of devices within each VLAN since a VLAN simply changes the available broadcast range for each device, while ACLs can manage permissions and more specifically manage device permissions.

**Professional Security Rationale**

