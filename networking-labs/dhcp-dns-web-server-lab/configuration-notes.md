# Router Configuration Notes (R1)

This file provides a quick reference for the router configuration used in the DHCP, DNS, and Web Server lab.

> **Important:** Verify the interface names in your Packet Tracer topology before using these commands. The example below uses `GigabitEthernet0/0` for the client network and `GigabitEthernet0/1` for the server network.

## 1. Enter Privileged and Global Configuration Modes

```text
Router> enable
Router# configure terminal
```

## 2. Configure the Client Network Interface

The client network is `192.168.1.0/24`. The router interface acts as the clients' default gateway.

```text
Router(config)# interface GigabitEthernet0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# ip helper-address 192.168.2.2
Router(config-if)# no shutdown
Router(config-if)# exit
```

The `ip helper-address` command forwards DHCP requests to the DHCP server at `192.168.2.2`.

## 3. Configure the Server Network Interface

The server network is `192.168.2.0/24`.

```text
Router(config)# interface GigabitEthernet0/1
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# end
```

## 4. Verify the Router Interfaces

```text
Router# show ip interface brief
```

Check that the interfaces have the expected IP addresses and that their status is `up` and protocol is `up`.

## 5. Save the Configuration

```text
Router# copy running-config startup-config
```

Press Enter if the router asks you to confirm the destination filename.

## 6. Expected IP Address Summary

| Network | Interface | IP Address |
|---|---|---|
| Client network | `GigabitEthernet0/0` | `192.168.1.1/24` |
| Server network | `GigabitEthernet0/1` | `192.168.2.1/24` |
| DHCP server | — | `192.168.2.2/24` |

**Note:** These commands document the intended configuration. Ensure they match the configuration in your actual Packet Tracer project.
