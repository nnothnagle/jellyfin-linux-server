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

Remote administration is performed using SSH.

SSH access is restricted by UFW (Uncomplicated Firewall) to devices on the trusted `192.168.0.0/24` local network.

Public-key authentication has been configured for the administrative user. The private key is stored on the administrator's workstation and protected with a passphrase. Only the corresponding public key is stored on the server.

SSH password authentication has been disabled to reduce the risk of password-based attacks.

The SSH configuration was validated before being reloaded. Key-based authentication was successfully tested from a separate terminal, and password authentication was independently verified as disabled.

## System Maintenance and Verification

- Verified UFW default policy is deny incoming and allow outgoing.
- Installed all available standard Ubuntu package updates.
- Rebooted the server and verified SSH and Jellyfin returned automatically.
- Verified Secure Boot is enabled.
- Attempted the available UEFI dbx Secure Boot security update. The update was reported as failed because fwupd could not verify the installed dbx version after reboot. Further investigation is pending.

## Security Principle

This project follows the principle of least privilege: users, services, and network connections should receive only the access required to perform their intended function.
