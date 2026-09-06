# Server Security

## Overview

The Jellyfin server uses multiple security controls to limit network access and protect administrative functions.

## Current Security Configuration

### UFW (Uncomplicated Firewall)

UFW is enabled as the host-level firewall on the Ubuntu server.

Currently permitted inbound services include:

- SSH (Secure Shell) for remote administration
- TCP (Transmission Control Protocol) port 8096 for Jellyfin client connections

### SSH (Secure Shell)

SSH is used to remotely administer the Ubuntu server from another computer on the local network.

SSH access is restricted by UFW (Uncomplicated Firewall) to devices on the trusted 192.168.0.0/24 local network. Connections to TCP (Transmission Control Protocol) port 22 from outside this subnet are blocked by the server firewall.

SSH connectivity was tested successfully from a Windows PC after the firewall rule was changed.

## Security Improvements Planned

- Review UFW default firewall policies
- Verify only necessary network services are listening
- Review SSH authentication configuration
- Install operating system security updates
- Verify Jellyfin runs using a dedicated service account
- Document and verify all security changes

## Security Principle

This project follows the principle of least privilege: users, services, and network connections should receive only the access required to perform their intended function.
