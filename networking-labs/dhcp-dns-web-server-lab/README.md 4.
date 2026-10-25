# DHCP, DNS, and Web Server Configuration

## 1. Overview

This project demonstrates the configuration of a multi-subnet network using Cisco Packet Tracer. The network separates client devices from infrastructure servers into two IPv4 subnets connected through a central router.

The project focuses on configuring and verifying three essential network services: Dynamic Host Configuration Protocol (DHCP), Domain Name System (DNS), and Hypertext Transfer Protocol (HTTP).

## 2. Learning Objectives

- Configure router interfaces to connect two IPv4 subnets.
- Configure default gateways for client and server networks.
- Deploy a DHCP server to assign IP configuration dynamically to client devices.
- Configure DHCP relay using `ip helper-address` to forward DHCP requests across subnets.
- Configure a DNS A record to map a domain name to an IPv4 address.
- Configure an HTTP web server and verify access using a domain name.
- Test network connectivity using `ipconfig`, `ping`, and DNS lookup tools.

## 3. Tools and Environment

- **Simulation Tool:** Cisco Packet Tracer
- **Course:** Network 1
- **Academic Level:** Level 4 — Computer Engineering
- **Protocols and Services:** IPv4, DHCP, DNS, HTTP, ICMP

## 4. Network Topology

The topology consists of two IPv4 subnets connected through router R1.

- **Client Network (`192.168.1.0/24`):** Contains client PCs connected through switch SW1.
- **Server Network (`192.168.2.0/24`):** Contains the DHCP, DNS, and Web servers connected through switch SW2.
- **Router R1:** Provides routing between the client and server subnets.

The DHCP server is located on a different subnet from the clients. Therefore, DHCP relay is required on the client-facing router interface to forward DHCP requests to the server.

## 5. IP Addressing Table

| Device | Role / Interface | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| R1 | Client-facing interface | `192.168.1.1` | `255.255.255.0` | N/A |
| R1 | Server-facing interface | `192.168.2.1` | `255.255.255.0` | N/A |
| DHCP Server | Static IP | `192.168.2.2` | `255.255.255.0` | `192.168.2.1` |
| DNS Server | Static IP | `192.168.2.3` | `255.255.255.0` | `192.168.2.1` |
| Web Server | Static IP | `192.168.2.4` | `255.255.255.0` | `192.168.2.1` |
| Client PCs | DHCP clients | `192.168.1.10–192.168.1.59`* | `255.255.255.0` | `192.168.1.1` |

*The client address range assumes that the DHCP pool starts at `192.168.1.10` and allocates 50 consecutive addresses without exclusions. Confirm the actual pool configuration before publishing.*

**Note:** Verify the router interface names against the actual Packet Tracer topology and configuration.

## 6. Configuration Summary

### DHCP Configuration

A DHCP pool named `CLIENTS` was configured with the following parameters:

- **Starting IP Address:** `192.168.1.10`
- **Subnet Mask:** `255.255.255.0`
- **Default Gateway:** `192.168.1.1`
- **DNS Server:** `192.168.2.3`
- **Maximum Number of Users:** 50

DHCP allows client devices to obtain their IP configuration automatically instead of requiring manual configuration on each PC.

### DHCP Relay Configuration

The `ip helper-address` command was configured on the router interface connected to the client network, pointing to the DHCP server at `192.168.2.2`.

DHCP clients initially send broadcast requests. Because routers do not normally forward these broadcasts between subnets, DHCP relay forwards the requests to the remote DHCP server.

### DNS Configuration

An A record was configured on the DNS server to associate:

- **Domain Name:** `www.network.com`
- **IPv4 Address:** `192.168.2.4`

This allows clients to access the web server using its domain name instead of entering its IP address directly.

### HTTP Web Server Configuration

HTTP service was enabled on the Web server at `192.168.2.4`.

The default web page was customized to display:

> Welcome to Network 1 – Computer Engineering

## 7. Verification and Test Results

The following checks were performed from the client network. The results below should match the actual screenshots and test outputs included with the project.

1. **IP Configuration:** Used `ipconfig` to inspect the client's assigned IP address, default gateway, and DNS server.
2. **Connectivity Testing:** Used `ping` to test connectivity to the default gateway and the relevant servers.
3. **DNS Resolution:** Tested whether `www.network.com` resolved to `192.168.2.4`.
4. **Web Access:** Opened `http://www.network.com` in the client browser to verify access to the customized web page.

## 8. Screenshots and Evidence

Screenshots documenting the configuration and verification process are stored in the `screenshots/` directory.

- **Router Interfaces:** `screenshots/Router_Interfaces_Verification.jpg`
- **DHCP Pool Configuration:** `screenshots/DHCP_configuration.jpg`
- **Client IP Configuration:** `screenshots/IP_configuration.png.jpg`
- **DNS Record Configuration:** `screenshots/DNS_configuration.jpg`
- **Connectivity and DNS Tests:** `screenshots/DNS_NSLOOKUP_Test.jpg`
- **Web Server Access:** `screenshots/Web_Server_Access_Verification.png.jpg`

Ensure that these filenames match the actual files in the repository and that each screenshot supports the corresponding claim.

## 9. Troubleshooting and Challenges

During DHCP server configuration, some input fields and labels were not visible in the Packet Tracer interface.

**Resolution:** Switching the application from Dark Theme to Classic (Light) Theme restored the visibility of the interface elements and allowed configuration to continue.

## 10. Key Lessons Learned

- DHCP relay enables clients to obtain IP configuration from a DHCP server located on another subnet.
- Default gateways allow devices to communicate with destinations outside their local subnet.
- DNS A records map domain names to IPv4 addresses.
- HTTP allows clients to retrieve web content from a web server.
- Testing and documenting network behavior is an important part of verifying a network configuration.

## 11. Project Status

**Status:** Completed implementation and verification, subject to the evidence provided.

This project was developed as part of the Network 1 practical lab requirements for Level 4 Computer Engineering.

