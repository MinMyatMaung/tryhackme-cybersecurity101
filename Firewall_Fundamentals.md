# Firewall Fundamentals

## Overview

A **firewall** is a security control that monitors and filters incoming and outgoing network traffic. It acts as a barrier between a trusted system or network and untrusted networks such as the Internet.

Firewalls use predefined rules to determine whether traffic should be **allowed, denied, or forwarded**. Modern firewalls can also perform advanced inspection, application filtering, intrusion prevention, and threat detection.

## Types of Firewalls

### Stateless Firewall
- Operates mainly at **OSI Layers 3 and 4**
- Filters packets using predefined rules
- Does not remember previous connections
- Processes traffic quickly
- Useful for basic, high-speed packet filtering

### Stateful Firewall
- Operates at **OSI Layers 3 and 4**
- Tracks active connections using a **state table**
- Makes decisions based on previous traffic
- Provides better context and security than stateless filtering

### Proxy Firewall
- Operates at **Layer 7 — Application Layer**
- Acts as an intermediary between users and external networks
- Inspects packet contents
- Can provide content filtering and application control
- Helps hide internal IP addresses from external systems

### Next-Generation Firewall (NGFW)
- Operates across **Layers 3–7**
- Performs deep packet inspection
- Includes intrusion prevention capabilities
- Can detect malicious patterns and anomalies
- Supports SSL/TLS inspection
- May use threat intelligence to identify malicious traffic

## Firewall Rules

Firewall rules determine how specific network traffic should be handled.

Common rule components include:

- **Source Address** — IP address where the traffic originates
- **Destination Address** — IP address receiving the traffic
- **Port** — Network service port
- **Protocol** — TCP, UDP, ICMP, etc.
- **Action** — Allow, deny, or forward
- **Direction** — Inbound or outbound traffic

## Firewall Actions

### Allow

Permits traffic matching the rule.

Example:

```text
Action: Allow
Source: 192.168.1.0/24
Destination: Any
Protocol: TCP
Port: 80
Direction: Outbound
```

This allows devices on the network to send HTTP traffic.

### Deny

Blocks traffic matching the rule.

Example:

```text
Action: Deny
Source: Any
Destination: 192.168.1.0/24
Protocol: TCP
Port: 22
Direction: Inbound
```

This blocks incoming SSH traffic.

### Forward

Redirects traffic to another system or network segment.

Example:

```text
Action: Forward
Source: Any
Destination: 192.168.1.8
Protocol: TCP
Port: 80
Direction: Inbound
```

This forwards HTTP traffic to a web server.

## Rule Direction

### Inbound Rules

Control traffic entering a system or network.

Example:

```text
Allow inbound TCP port 80
```

This could allow users to access a web server.

### Outbound Rules

Control traffic leaving a system or network.

For example, an organization could block outbound SMTP traffic from every system except its authorized mail server.

### Forwarding Rules

Redirect traffic between systems or network segments.

These are commonly used on firewalls that also function as routers or gateways.

---

# Windows Defender Firewall

Windows includes a built-in firewall called **Windows Defender Firewall**.

It supports:

- Inbound rules
- Outbound rules
- Application-based rules
- Port and protocol filtering
- Custom firewall rules
- Different security profiles depending on the network

## Network Profiles

Windows Firewall uses different profiles depending on the network environment.

### Private Network

Used for trusted networks such as a home network.

### Public Network

Used for untrusted networks such as:

- Coffee shops
- Airports
- Restaurants
- Public Wi-Fi

Public profiles can use stricter firewall settings to reduce exposure.

## Creating a Custom Windows Firewall Rule

In the lab, an outbound firewall rule was created to block web traffic.

The rule blocked:

```text
TCP 80
TCP 443
```

These ports are commonly associated with:

```text
80  → HTTP
443 → HTTPS
```

The basic process was:

1. Open **Windows Defender Firewall with Advanced Security**
2. Select **Outbound Rules**
3. Select **New Rule**
4. Choose **Custom**
5. Apply the rule to all programs
6. Select **TCP**
7. Enter remote ports:

```text
80,443
```

8. Choose **Block the connection**
9. Apply the rule to the desired network profiles
10. Give the rule a name and save it

After enabling the rule, web traffic using these ports was blocked, confirming that the firewall rule worked.

---

# Linux Firewalls

Linux provides firewall functionality through the **Netfilter** framework.

Netfilter supports:

- Packet filtering
- Network Address Translation (NAT)
- Connection tracking
- Traffic control

Several Linux firewall utilities use Netfilter.

## iptables

`iptables` is a traditional Linux firewall management utility used to configure Netfilter rules.

## nftables

`nftables` is the modern successor to `iptables`.

It provides improved:

- Packet filtering
- NAT configuration
- Rule management

## firewalld

`firewalld` provides firewall management using predefined network **zones** and rule sets.

## UFW

**UFW — Uncomplicated Firewall** provides a simplified interface for managing Linux firewall rules.

It is especially useful for users who do not want to work directly with complex `iptables` rules.

### Check Firewall Status

```bash
sudo ufw status
```

### Enable UFW

```bash
sudo ufw enable
```

### Disable UFW

```bash
sudo ufw disable
```

### Allow Outgoing Traffic by Default

```bash
sudo ufw default allow outgoing
```

This allows outgoing connections unless another rule specifically blocks them.

### Block Incoming SSH

```bash
sudo ufw deny 22/tcp
```

Port `22` is commonly used by SSH.

### Display Firewall Rules

```bash
sudo ufw status numbered
```

Example:

```text
[1] 22/tcp     DENY IN     Anywhere
[2] 22/tcp     DENY IN     Anywhere (v6)
```

### Delete a Firewall Rule

```bash
sudo ufw delete 2
```

Using numbered rules makes firewall management easier.

---

## Key Takeaways

- Firewalls control incoming and outgoing network traffic.
- Firewall decisions are based on rules involving IP addresses, ports, protocols, directions, and actions.
- **Stateless firewalls** evaluate packets independently.
- **Stateful firewalls** track connection states.
- **Proxy firewalls** inspect application-layer traffic.
- **Next-generation firewalls** provide deep packet inspection and advanced threat protection.
- Windows provides **Windows Defender Firewall** for managing network traffic.
- Linux uses the **Netfilter** framework with tools such as `iptables`, `nftables`, `firewalld`, and `ufw`.
- Custom firewall rules can significantly reduce a system's attack surface by limiting unnecessary network access.
