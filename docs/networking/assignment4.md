# Implementing Seurity for Devices

## Project Overview

**Problem Statement:**

INSERT

**Objectives:**

INSERT

**Success Criteria:**

INSERT

## Design & Planning

INSERT STUDENT NOTES

### Password Algorithm Design

Using the concepts of **length, unpredictability, and uniqueness**, a memorable password algorithm was created.

Here is the algorithm:

1. Add '!!' at the start of the password.
2. Take the name of the service or website used and reverse it.
    1. Take the reversed name and remove every other letter/character, starting with the second one (e.g. Amazon -> nozamA -> nzm).
    2. Set every letter to lowercase.
3. If the service name starts with a vowel, take the string "XaZ". Else, take the string 'CfC'.
4. Take the strings obtained in (2) and (3). Starting with the one obtained in (2), interweave the letters of each string, alternating from (2) to (3). (e.g. 'nzm' + 'XaZ' = 'nXzamZ'). Append this to the password.
5. Append the string 'LemonadeDollarSign$$' to the end of the password.
6. Final output should look similar to '!!nXzamZLemonadeDollarSign$$'.

**Pros and Cons of the Algorithm**

Pros:

- This algorithm is very easily memorizable and applied, so it can work with a variety of services.
- The password produced is fairly long, which helps against brute force.

Cons:

- The strings like 'XaZ' can be changed to something more personal to the user. The same applies to other parts.
- If a hacker recognizes the pattern in a compromised password, then they can brute force the minimum 6 characters of the string generated from (2) and (3).

## Technical Development

### Changing the Default Password in the Ubuntu VM

This segment involves:

1. Setting a new password for the ubuntu superuser
2. Creating a new account on the Ubuntu VM
3. Changing the new account's password
4. Locking the ubuntu account for security

**Changing the Ubuntu Password**

On a normal user's operating system, doing similar steps is very important because oftentimes, the superuser has a predictable or default password which is often unconfigured. Thus, setting one's own username and password allows for only specified users to obtain administrator privileges.

When the Ubuntu VM was first created, the default credentials were the username **ubuntu**, and the password **ubuntu**, which is very unsecure.

To change the password for *ubuntu*, the `passwd` command was used.

After entering the current password, a new password was then set successfully (note that it cannot be seen for security reasons).

INSERT UBUNTU PASSWORD CHANGE SCREENSHOT

To test if the password was changed, a command requiring admin privileges (using `sudo`) was run. The new password worked successfully.

INSERT PASSWORD SUCCESS WITH LS ROOT

**Configuring a New User**

To create the new account on the VM, the command `sudo adduser \[USERNAME\]` was run.

Afterwards, the command `sudo usermod -aG sudo [USERNAME]` was run to allow administrator privileges to the newly created account.

Here is the result of running both commands:

INSERT CREATED USER

**Locking Ubuntu for Security**

It is helpful to lock the *ubuntu* account since its credentials are often predictable. Most of the time, when the administrator account is still accessible, it has a predictable password such as *ubuntu* or *admin*. To do so on Ubuntu, `sudo passwd -l ubuntu` is used:

INSERT PASSWORD LOCKING

As shown below, the *ubuntu* account cannot be accessed:

INSERT LOCKED UBUNTU

### Enabling MFA in the Ubuntu VM

To confirm that the created user (connor) has superuser permissions, `sudo ls /` was run:

INSERT SUDO LS /

To download the tools for authentication (specifically Google), `sudo apt update` and `sudo apt install libpam-google-authenticator -y` were run.

Then, to use the uathenticator, the command `google-authenticator` was used, ultimately resulting in the generation of a secret key, as well as a QR code storing that secret key for the system.

INSERT QR PICTURE

Note that the secret key is used to generate a 6-digit code which changes every 30 seconds, known as a **time-based one-time password** (TOTP). These are very difficult to guess because of rate limiting and the password resetting every 30 seconds.

To simulate the TOTP, [this website](https://totp.danhersam.com) was used. As shown below, a 6 digit code was generated:

INSERT TOTP PICTURE

***NOTE: IN PRACTICE, DO NOT SHOW THE SECRET KEY TO ANYONE. THIS IS A CLASSROOM SIMULATION.***

When running `google-authenticator` once again, the 6 digit code was inserted, and MFA was successfully established:

INSERT WORKING CODE

**Enabling MFA for SSH**

To enable MFA in establishing SSH connections, `sudo nano /etc/ssh/sshd_config` was run, and *KbdInteractiveAuthentication* was enabled. Note that for additional password verification, *PasswordAuthentication* must also be enabled.

INSERT NANO THING

Next, to add the authenticator to SSH verification, `sudo nano/etc/pam.d/sshd` was run, and authenticator verification was required by inserting `auth required pam_google_authenticator.so`.

INSERT OTHER NANO THING

Note that SSH has to be reset after this using `sudo systemctl restart ssh`.

Finally, to test the password and authenticator MFA when using ssh, `ssh [USERNAME]@localhost` was used to establish a remote connection. As shown below, this first required a verification code, then the user's password, so the MFA was successful.

INSERT SSH MFA TEST

### Patching Ubuntu

This section details the process of patching software in the Ubuntu VM.

To check for available software updates, it is recommended to run `sudo apt update` every time a Linux operating system is used.

Next, to see what software has available updates, `sudo apt list --upgradable` is used. As shown below, there were very many packages (37) which could be updated.

INSERT UPGRADABLE SOFTWARE

To actually perform the upgrades on the desired software, the command `sudo apt upgrade` is executed. Note that after performing the *upgrade* command, a record of the upgrade is appended to the **history.log** file, whch can be found under `/var/log/apt/history.log`. However, this file has much content and is thus hard to navigate, so it is useful to search for important keywords using the *grep* command.

This most recent upgrade was executed on October 13th, so it can be confirmed that an upgrade did happen on that day by using `grep "2025-10-13" /var/log/apt/history.log`:

INSERT GREP OUTPUT

Displayed above, the upgrade took approximately 1 minute.

Similarly, updates on other dates can also be viewed:

INSERT OTHER GREP OUTPUT

Every package which is newly installed or updated is listed in lines starting with "Install:". Hence, `grep "Install:" /var/log/apt/history.log` is used to list all of the installs.

## Testing & Evaluation

INSERT

## Reflection & Analysis

INSERT