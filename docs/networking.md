# Network Configuration

## Overview

The Jellyfin server is connected to the local network using a wired Ethernet connection. The server is administered through the Linux command line and can also be accessed remotely over the local network using SSH.

## Network Interface

- **Primary Interface:** eno1
- **Connection Type:** Wired Ethernet
- **IPv4 Network:** 192.168.0.0/24
- **Address Assignment:** DHCP
- **Wi-Fi Interface:** wlp2s0 (currently disabled)

> The server's exact IP address is intentionally omitted from public documentation.

## Jellyfin Network Services

Jellyfin was verified to be listening on the following ports:

| Protocol | Port | Purpose |
| --- | --- | --- |
| TCP | 8096 | Jellyfin web interface and client connections |
| UDP | 7359 | Jellyfin local-network discovery |

## Firewall

Ubuntu's Uncomplicated Firewall (UFW) is enabled on the server.

Current required access includes:

- SSH for remote server administration
- TCP port 8096 for Jellyfin client access

## Future Improvements

- Configure a DHCP reservation for the Jellyfin server
- Restrict SSH access to trusted local-network addresses
- Review whether UDP 7359 should be permitted for local Jellyfin discovery
- Document remote-access architecture if remote Jellyfin access is added
