# Network Architecture

## Current Architecture

The Jellyfin server operates as a self-hosted service on the local home network. Client devices connect to the server over the LAN, while administrative access is performed using SSH.

```mermaid
flowchart TD
    Internet["Internet"]
    Router["Home Router"]
    Server["HP EliteDesk 800 G5<br/>Ubuntu Server 24.04 LTS"]
    UFW["UFW Firewall"]
    Jellyfin["Jellyfin Server<br/>TCP 8096"]
    SSH["SSH Administration<br/>TCP 22"]
    Clients["Local Clients<br/>TV / PC / Phone"]

    Internet --> Router
    Router --> Server
    Server --> UFW
    UFW --> Jellyfin
    UFW --> SSH
    Jellyfin --> Clients
```

## Architecture Notes

- The server uses a wired Ethernet connection.
- The server resides on the `192.168.0.0/24` private network.
- UFW provides host-level firewall protection.
- Jellyfin accepts client connections using TCP port 8096.
- SSH provides command-line administration of the Ubuntu server.
- The server's exact private IP address is intentionally omitted.
