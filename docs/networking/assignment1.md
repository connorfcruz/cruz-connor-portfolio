# Component Cards and Software Slips

## Project Overview

**Problem Statement:**

Although many people use computers on a daily basis, few know about the individual components, both hardware and software, which actually control how that computer functions. To remedy this problem, this assignment introduces students to the hardware and how signal flows from one component to the next, as well as how each software component interacts with or allows for the next to perform its function.

**Objectives:**

- Learn what a protocol is and the difficulty of conveying information.
- Know what hardware components are and why they matter.
- Know how each piece of hardware interacts with the rest.
- Learn software and their interactions.

**Success Criteria:**

Be able to identify hardware/software given their definition or function, and also know how to do the opposite. 

## Design & Planning

### Silent Signals

![Silent Signals Diagram](../images/SilentSignalsDiagram.jpg)

This is a diagram of the finalized process for Silent Signals. Specifically, this solves the problem of communicating

- Yes/No answers
- Numbers
- Months

all in the same message, using only a card with two faces: one blue and one white.

Note that this solution requires tapping the card, which was later found out to be prohibited.

### Hardware and Software

**Hardware Diagram:**

The first diagram shows how hardware components interact with each other step by step to type a sentence and save it.

![Hardware Diagram](../images/HardwareDiagram.jpg)

Here is my thought process behind this:
- PSU: Powers the entire system
- Motherboard: PSU connects to the motherboard to power and link the other components
- Cooling system: Applies to everything controlled by the motherboard
- I/O Device (Keyboard): Serves as input for when the user types, so goes into the motherboard
- CPU: Interacts with the RAM and Storage to get/send th text data, and sends data for the GPU to display
- RAM: Stores the typed text short-term
- GPU: Renders graphics and output them on an I/O device (Monitor)
- Storage: When the text is saved, it is stored here

The generally accepted diagram by the class was Arshia's, shown below. This differs from mine in that it shows every interaction between components rather than a step-by-step diagram.

![Arshia's Diagram](../images/ArshiaDiagram.jpg)

**Software Diagram:**

This diagram shows how the software in a computer interacts to download a file and open it via a graphics program.

![Software Diagram](../images/SoftwareDiagram.jpg)

Here is my thought process:
- Firmware/UEFI: Starts the computer and allows the OS to run
- Virtual Machine/Runtime Environment: The base of the OS; also necessary for the OS to run
- OS: manages other software applications
- Device Drivers: Go both in and out from the OS to interact with hardware components
- Security/Encryption Layer: Goes in and out from the OS for sending a request and receiving the downloaded file to ensure security
- Networking Stack Layer: Downloads the file and goes through security/encryption layer to protect the OS
- File System Layer: Allows for file management to save the downloaded file
- Applications: Run from the file system layer; in this case, it is the graphics program
- Libraries/Runtimes: Provide necessary resources for groups of applications

**Hardware/Software Diagram:**

This diagram shows how hardware and software interact for printing an English paper.

![Hardware/Software Diagram](../images/HardwareSoftwareDiagram.jpg)

The interactions on this diagram can be generalized from the others. A notable point is that the device drivers interact between the OS and many hardware components. Furthermore, the Security/Encryption Layer, Networking Stack Layer, and NIC are not necessary because there is no requirement of network connection (assuming a local text editing program such as Word).

## Technical Development

**Components Song:**

![type:audio](../audio/Cruz-TheTechInside.mp3)

??? note "Lyrics:"

    \[Verse 1\]
    Yo, the brain of the beast, call it CPU,
    Calculatin’ every move, every click you do.
    Clock ticks quick, instructions in a queue,
    Arithmetic and logic, keepin’ it true.

    RAM’s the sprinter, short-term speed,
    Holdin’ what you need, while the programs feed.
    Temporary thoughts, fast as a steed,
    But cut the power, gone—won’t succeed.

    Storage, that’s memory for the long haul,
    SSD’s flash, no spin at all.
    HDD, old school, disks gotta crawl,
    But both save your files, big or small.

    \[Chorus\]
    It’s the tech inside, it’s the heart, the soul,
    Each piece in sync, makin’ the system whole.
    From the brain to the power, every role defined,
    Understand the parts, you control the grind.

    \[Verse 2\]
    GPU, the artist, paintin’ the screen,
    Renderin’ dreams in pixels so clean.
    3D worlds, movies pristine,
    Gamers and creators, it’s the unseen machine.

    Motherboard’s the hub, connections unite,
    Pathways and circuits, keepin’ it tight.
    All roads lead here, no part’s in flight,
    Communication central, day or night.

    \[Verse 1\]
    Yo, the brain of the beast, call it CPU,
    Calculatin’ every move, every click you do.
    Clock ticks quick, instructions in a queue,
    Arithmetic and logic, keepin’ it true.

    RAM’s the sprinter, short-term speed,
    Holdin’ what you need, while the programs feed.
    Temporary thoughts, fast as a steed,
    But cut the power, gone—won’t succeed.

    Storage, that’s memory for the long haul,
    SSD’s flash, no spin at all.
    HDD, old school, disks gotta crawl,
    But both save your files, big or small.

    \[Chorus\]
    It’s the tech inside, it’s the heart, the soul,
    Each piece in sync, makin’ the system whole.
    From the brain to the power, every role defined,
    Understand the parts, you control the grind.

    \[Verse 2\]
    GPU, the artist, paintin’ the screen,
    Renderin’ dreams in pixels so clean.
    3D worlds, movies pristine,
    Gamers and creators, it’s the unseen machine.

    Motherboard’s the hub, connections unite,
    Pathways and circuits, keepin’ it tight.
    All roads lead here, no part’s in flight,
    Communication central, day or night.

    \[Chorus\]

    \[Verse 3\]
    PSU’s the lifeline, feedin’ the juice,
    Convertin’ AC to DC, lettin’ volts loose.
    No power? No play—nothing to produce,
    Wattage on point, keepin’ tight with no excuse.

    NIC’s the bridge, to the net it connects,
    Sendin’ data fast, keepin' all in check.
    Ethernet or Wi-Fi, commands it directs,
    Online or LAN-side, it earns your respect.

    Coolin’ the heat, fans or the liquid flow,
    Keepin’ temps low when performance grows.
    Overclock dreams? You better know,
    Without that chill, your system won’t go.

## Testing and Evaluation

## Reflection and Analysis

