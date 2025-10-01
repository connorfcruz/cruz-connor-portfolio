# Determining Security Controls for Devices

## Project Overview

**Problem Statement:**

Many people are unaware of how to secure their data, as well as possible threats which could pose a threat to their security and information. This activity provides an explanation of how the user can secure their devices effectively and the types of attacks to be aware of.

**Objectives:**

- Learn the CIA triad and how to keep information safe
- Compare current software versions with their latest updates, and update them to their latest versions
- Know common device vulnerabilities to look out for
- Know common social engineering attacks which malicious actors use
- Know how to defend from both device vulnerabilities and social engineering attacks

**Success Criteria:**

Fill out a guided note document to retain the knowledge of cyberattacks and defenses, update outdated software, and manage security controls and possible vulnerabilities in an Ubuntu virtual machine.

## Design & Planning

### Cybersecurity Basics for Devices (Guided Notes)

These notes primarily cover three topics: the CIA triad, common device vulnerabilities, and social engineering attacks.

**The CIA Triad**

The CIA triad is an acronym which is defined as follows:

- Confidentiality - keeping information inaccessible to those who should not see it
- Integrity - keep information acurate and trustworthy
- Availability - allow information to be accessed when necessary

Here are some examples of where each of these are expressed:

- Confidentiality is provided mainly through encryption of data, which prevents it from being interpreted without a key.
- Integrity is maintained via backup files and preventing users from tampering with them.
- Availability matters when specific people need access to data, suich as a test administered by the College Board.

CIA is very important for assessing the security of a device or network, and it can help to ensure that data remains safe.

**Common Device Vulnerabilities**

These are some examples of common device vulnerabilities and why they matter:

- Outdated Operating System: If a vulnerability or incompatibility is discovered in an operating system, people may try to take advantage of that vulnerability and access one's device
- Unencrypted Data: If data is accessed, it is able to be interpreted without any trouble by those who shouldn't see it
- Weak Passwords: Easy-to-guess or leaked passwords allow for malicious parties to obtain access to one's data without many boundaries
- Open Ports: Ports allow a device to access the internet, so an open port can allow for someone to remotely access one's operating system
- Unpatched Software: Similarly to an outdated OS, pplications often release patches for security flaws, and failing to update them could result in a security breach

Overall, the specific vulnerabilities which fall into these categories can be accessed via the public database known as **CVE** (Common Vulnerabilities and Exposures). This database is very useful for ensuring that vulnerabilities are assigned a unique identifier and are able to be tracked and fixed in an orderly fashion.

**Social Engineering Attacks**

Social engineering attacks are mostly a result of user error, and they can often be avoided by being careful of one's data and taking proper measures to check an unverified party's authentication.

There are five primary social engineering attacks:

- Phishing: Targeting a large and general group of people by attempting to get them to click a malicious link or perform a malicious action
- Spear Phishing: A subset of phishing which targets a specific set of people (often businesses)
- Pretexting: Using communication with a user to create an image and gain trust, with the intended purpose of getting the user to allow access
- Baiting: Offering a reward, either physical or virtual, to a specific person but instead performing another action
- Tailgating: Entering an open door or insecure location to access a user's device (physical or virtual)

Phishing and Spear Phishing can mostly be prevented by validating the identity of the party who is sending the link/attachment to be opened.

Pretexting and tailgating are most effectively prevented by ensuring the identity and authoriztaion given to a person before trusting them with information.

Baiting is best prevented by being aware of suspicious or unknown devices and avoiding allowing them to connect to one's own devices.

## Technical Development

### Outdated Software

In this activity, students checked software in an Ubuntu VM to determine whether they were: up to date, outdated, or not installed. Since outdated software can often provide vulnerabilities, it is best to update it to the latest available version.

Before checking the versions of the various software, the following commands had to be run to allow the latest versions to be installed if they were not already:

```shell
sudo apt update -y
sudo apt upgrade -y
```

To actually check the versions of software, the name of the software followed by `--version` or some variant is usually used:

INSERT VERSION CHECKS

Below are the results obtained for different software, as well as the possible risks of leaving that software outdated:

| Software | Status | Risk |
| ------ | ------ | ------ |
| OpenSSL | Outdated | OpenSSL controls encryption, which hides sensitive data |
| Firefox | Up To Date | The browser's cookies could be accessed, which store user information and passwords |
| LibreOffice | Outdated | Documents can become corrupted or made public if vulnerable |
| Python | Outdated | Someone could execute remote commands to perform unwanted actions |
| Apache HTTP Server | Not Installed | Content accessed on the internet could be redirected maliciously |
| GIMP | Not Installed | Images could become corrupted or deleted |
| Java | Not Installed | Remote Java scripts could be executed to perform unwanted actions |
| OpenSSH | Outdated | An unauthorized party could connect to the device remotely via SSH |

Note that a piece of software not being installed is more safe than installing it and leaving it out of date because the software's point of contact with the internet is not made until it is installed. Thus, too much unnecessary and unmanaged software could pose the risk of exposing one's device to the broader internet.

As shown above, most of the software was outdated. Although this does not have much of an impact on a VM with in-school use, if these software were downloaded on a more important operating system, then these outdated versions could post various risks. Personal data could possibly be compromised, or the system could be corrupted and manipulated such that it could not be restored to a previous available version.

To actually update this software, running the software's install command once again usually updates it.

For example, Raaj found a method to install the latest version of Java on the virtual machines despite Ubuntu only natively supporting an earlier outdated version. This command is as follows:

`sudo apt install openjdk-21-jdk`

After updating, here is the displayed version, which correlates to the latest available version of the JDK:

INSERT JAVA LATEST VERSION

### Cybersecurity Basics got Devices

### Social Engineering Attacks/Defenses

This is an activity done with a partner in which scenarios of breached security (red slips) must be paired with remedies to the respective problems (the green slips).

INSERT CARDS IMAGE

After reviewing the slips once again after learning about specific social engineering attacks, the obtained answers were exactly the same as those obtained previously.

Interestingly, some attacks did not fall into social engineering, but were rather device vulnerabilities.

## Testing & Evaluation

### Outdated Software

### Cybersecurity Basics for Devices

## Reflection & Analysis