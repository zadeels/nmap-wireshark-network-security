# Network Security Assessment — Nmap & Wireshark

## Project Overview

This project presents a network security assessment conducted within an isolated virtual lab environment using VMware Workstation and Ubuntu Server. The assessment aimed to identify accessible TCP services, analyse network traffic, and evaluate the effectiveness of firewall controls in restricting unnecessary incoming connections.

Nmap was used to scan TCP ports 22, 80, and 443, while Wireshark was used to analyse the corresponding packet behaviour. Uncomplicated Firewall (UFW) was configured on Ubuntu Server to restrict incoming network access, and additional scans were conducted to evaluate the effectiveness of the firewall configuration.

## Tools and Technologies

- **Nmap** — TCP port scanning and service identification
- **Wireshark** — Network traffic capture and packet analysis
- **Ubuntu Server** — Target virtual machine
- **VMware Workstation** — Virtual lab environment
- **UFW** — Linux firewall configuration
- **OpenSSH Server and Nginx** — Services configured on the target machine

## Lab Environment

The assessment was conducted using a Windows host and an Ubuntu Server virtual machine connected through a VMware host-only network (VMnet1). The Windows host was used to conduct network scanning and packet analysis, while Ubuntu Server provided the target services.

The assessment focused on TCP ports 22 (SSH), 80 (HTTP), and 443 (HTTPS).

## Methodology

1. Installed and configured OpenSSH Server and Nginx on Ubuntu Server.
2. Conducted an initial Nmap scan to identify accessible TCP ports.
3. Used Wireshark to analyse TCP handshakes and connection reset responses.
4. Configured UFW to deny incoming connections by default, with an exception for SSH on TCP port 22.
5. Repeated Nmap scans and Wireshark captures to compare network behaviour before and after firewall deployment.

## Key Findings

| TCP Port | Service | Before Firewall | After Firewall |
|---|---|---|---|
| 22 | SSH | Open | Open |
| 80 | HTTP | Open | Filtered |
| 443 | HTTPS | Closed | Filtered |

The initial assessment identified SSH and HTTP as open, while HTTPS was closed. Following the deployment of UFW, SSH remained accessible while HTTP became filtered. Wireshark packet captures supported these findings by showing successful TCP connections before firewall configuration and unanswered connection attempts after deployment.

## Project Documentation

- [Full Network Security Assessment Report](report/network-security-assessment.pdf)
- [Screenshots and Packet Analysis Evidence](screenshots/)
- [Nmap Scan Results](scans/)
- [Lab Notes](notes/lab-notes.txt)

## Limitations

The assessment was conducted in an isolated virtual lab environment and focused on three TCP ports. No vulnerability exploitation, UDP scanning, or application-level security testing was performed.
