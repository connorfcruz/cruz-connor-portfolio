# Data Movement and Types of Networks

## Project Overview

**Problem Statement:**

INSERT

**Objectives:**

INSERT

**Success Criteria:**

INSERT

## Design & Planning

### Data Movement Notes

**LAN**

| Term | Definition | Additional Notes |
| ------ | ------ | ------ |
| LAN (Local Area Network) | A network that connects computers and devices within one building/campus | Lets devices share printers, files, internet connections, etc. efficiently |
| Host | Device that can send or receive data on the network | Has unique IP address |
| Switch | Connects multiple devices inside the LAN | Learns the address of each device plugged in; fowards data to only the intended device |
| Router | Connects LAN to other networks | Uses IP addresses to decide destination |
| Packet | Data travels in chunks called packets | Contain sender's IP (return address), receiver's IP (destination), payload (data transmitted) |
| IP Address | Identifies each device on a network | Unique for each device |

**Number Bases and Applications**

Binary is useful because:

- All digital data is transmitted through binary/base 2
- Computer signals are either on or off, represented by 1 or 0 respectively
- On/off signals can store IP addresses, MAC (hardware) addresses, and packets

Binary:

- Each binary digit is a bit
- 8 bits = 1 byte
- 4 bits = nibble

IP addresses:

- E.g. 192.168.1.1
- Each division is an octet
- Each octet is 8 bits = 1 byte
- 4 bytes total
- 192.8.1.1 to binary: 11000000.00001000.00000001.00000001

Hexadecimal:

- Base 16
- Each hex digit = 4 bits, so you can split a binary string into sets of 4 to easily convert
- Shorthand way to read a long binary string

**Practice Conversions**

| Denary | Binary | Hex |
| ---- | ---- | ---- |
| 0 | 0 | 0 |
| 1 | 1 | 1 |
| 2 | 10 | 2 |
| 3 | 11 | 3 |
| 4 | 100 | 4 |
| 5 | 101 | 5 |
| 6 | 110 | 6 |
| 7 | 111 | 7 |
| 8 | 1000 | 8 |
| 9 | 1001 | 9 |
| 10 | 1010 | A |
| 11 | 1011 | B |
| 12 | 1100 | C |
| 13 | 1101 | D |
| 14 | 1110 | E |
| 15 | 1111 | F |
| 16 | 10000 | 10 |

| Binary | Decimal | Hex |
| ----- | ----- | ----- |
| 11001000 | 200 | C8 |
| 101101 | 45 | 2D |
| 00001100 | 12 | C |
| 10101111 | 175 | AF |

## Technical Development

INSERT

## Testing and Evaluation

INSERT

## Reflection

INSERT