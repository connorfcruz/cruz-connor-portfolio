# Subnetting and Maintaining Multiple LANs

### Making Separate Networks Communicate



### When Networks Break: Diagnosing and Fixing Problems

In this activity, a broken network was examined, the problem was diagnosed, and a solution was made.

**Initial Observations**

To start, the network topology was examined:

INSERT TOPOLOGY

As seen above, the connection between the router and Switch1 seemed to be down, but there may also be hidden connection failures. To check for these, **ping** was used.

To confirm that ping was working, PC0 pinged PC1 (on the same switch), which was expected to work:

INSERT PING 11

Since this worked, there is not a problem with the ping command.

Next, a PC under the other router and the other router itself were pinged to check for problems communicating with that subnet:

INSERT PING 2.10 2.1

Both of these failed, implying that there is likely a connection failure connected to Switch1, which supports what was deduced from the topology.

Finally, pings were made from PC2 on the other subnet to diagnose exactly where the problem is:

INSERT PING 2.11 2.1

Communication with the other device on the same subnet worked, meaning that Switch1 is configured correctly. However, the ping to the switch itself failed, suggesting that there is a problem with the IP address assigned by the router. Thus, there must be a problem between the router and Switch1.

The configs of the GigabitEthernet ports of the router were then checked to see any disparity between the switch configurations:

INSERT GIGA0
INSERT GIGA1

The only notable difference is that the port status for GigabitEthernet0/0/1 (Switch1) is off. This is the problem in the network.

**Fixing the Problem**

To fix this, the router's CLI was opened, and GigabitEthernet0/0/1 was opened. Next, the command `no shutdown` was entered to activate the connection:

INSERT TERMINAL STUFF

**Checking Status Afterwards**

When checking the config of GigabitEthernet0/0/1, the port status was set to **On**, implying that the problem was fixed:

INSERT ON CONNECTION

The part of the topology which was previously red also turned green, showing that the connection is UP:

INSERT TOPOLOGY FIXED

Finally, `ping` was run again from PC0 to the other subnet's switch and PC3:

INSERT FINAL PING

Since these pings were successful, the network was successfully fixed.

**Solution Explanation**

Through checking ping, router configurations, and the network topology visualization, the problem was diagnosed to be between the router and Switch1. `ping` especially supported this, as communication was only possible up to the point between the router and Switch1 from a device on Switch0. To look for a solution, differences in switch configuration were checked, since Switch0 was successfully connected and was a good benchmark to compare to. The problem was found to be that the status of the port connected to Switch1 was **OFF**. To fix this, the CLI of the router was used to run the `no shutdown` command, which activates a port. After this fix, any ping run successfully worked, and the network topology showed a green connection between the router and Switch1, confirming that the problem was fixed.