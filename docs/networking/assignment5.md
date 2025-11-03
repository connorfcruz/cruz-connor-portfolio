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

Note that binary was given, and decimal and hex were found:

| Binary | Decimal | Hex |
| ----- | ----- | ----- |
| 11001000 | 200 | C8 |
| 101101 | 45 | 2D |
| 00001100 | 12 | C |
| 10101111 | 175 | AF |

The entries highlighted in **bold** were given:

| Denary | Binary | Hex |
| ----- | ----- | ----- |
| **597** | 1001010101 | 255 |
| 603 | **1001011011** | 25B |
| 255 | 0011111111 | **FF** |

**OSI Model**

OSI - Open Systems Interconnection

- Conceptual framework
- Each layer has its own job
- Understanding layers helps troubleshoot
- Helps understand how computesr talk to each other

| Layer | Name | Description | Details |
| -- | ----- | ----- | ----- |
| 7 | Application | Email or browser |
| 6 | Presentation | Translates data (encryption and compression) | Ensures that data is in a usable form |
| 5 | Session | Manages connection | Maintains connections; responsible for controlling parts and sessions |
| 4 | Transport | Breaks data into segments | Transmits data using transmission protocols (e.g. TCP, UDP) |
| 3 | Network | Routes packages using IP | Decides which physical path the data will take |
| 2 | Data Link | Transfers frames via MAC | Defines the format of the data on the network |
| 1 | Physical | Any hardware (e.g. wires, signals, routers) and Wi-Fi | Transmits to raw bit streams over a physical medium |

| Step | What Happens | OSI Layer |
| ----- | ----- | ----- |
| Write and address message | IP address gets formatted for communication | Presentation/Application |
| Package is prepared and boxed | Data is broken into segments | Transport/Network |
| Person at post office sorts it | ? | Session |
| Delivery truck figures out the best route | Routers and switches address routing | Network / Data Link |
| Truck drives it down the road | Data traveks through the cable fiber or Wi-Fi | Physical |

| TCP/IP | OSI | Functions |
| ----- | ----- | ------- |
| Application | 5-7 | Apps, HTTP, FTP |
| Transport | 4 | TCP/UDP, Segmentation |
| Internet | 3 | IP Addressing, Routing |
| Network Access | 1-2 | Physical & Data Link |

**MAC Addresses**

MAC Address - an address assigned to each physical device

- 6 pairs of hex digits
- 12 hex digits in total
- Each pair is separated by colons
- Unique to each device

## Technical Development

### LAN Components

**Addresses**

After net-tools is installed, *ifconfig* can be run on an Ubuntu VM to display information about the VM's network interfaces.

INSERT IFCONFIG SCREENSHOT

Some important components displayed in this are under **inet, netmask, and broadcast**.

inet: The IPv4 address assigned to that specific device which allows the router to identify it

netmask: Determines which parts of the inet/IPv4 address identify the network and which identify the host

- Note that there are 2 possible states: 255 denotes that it identifies the network, and 0 denotse that it identifies the device
- e.g. 255.255.255.0 means that the first 3 divisions define the network

broadcast: allows messages to be sent among devices on the same network



## Testing and Evaluation

INSERT

## Reflection

INSERT