# Determining Security Controls in a LAN

### Common Security Controls in a LAN

**LAN Threat Scenarios**

| **Scenario Letter** | **Symptoms Summary** | **Hypothesis** | **Justification** |
| A | A device suddenly receives the wrong gateway | The switch which the device is connected to changes its broadcast address | If the broadcast address of a switch is changed, then a device connected to it would connect to the switch, and this data would be diverted to another router |
| B | The switch CPU spikes; many MAC addresses appear on one port | An attacker requests IP addresses on many devices from the same router | The device cannot accept any more devices, and devices on the network cannot communicate |
| C | Clients receive IPs from an unexpected source | The network settings may not be secure, so the device is easier to attack | The source is unknown, so settings might not be very secure |
| D | A new unknown device appears inside the broadcast domain |  | |
| E | A host begins reaching other internal hosts it should never reach | | |

## Project Development

## Planning and Design

## Technical Development

## Testing and Evaluation

## Reflection