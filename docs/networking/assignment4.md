# Implementing Seurity for Devices

## Project Overview

**Problem Statement:**

INSERT

**Objectives:**

INSERT

**Success Criteria:**

INSERT

## Design & Planning

INSERT PASSWORD ALGORITHM

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

Afterwards, the command `sudo usermod -aG sudo \[USERNAME\]` was run to allow administrator privileges to the newly created account.

Here is the result of running both commands:

INSERT CREATED USER

## Testing & Evaluation

INSERT

## Reflection & Analysis

INSERT