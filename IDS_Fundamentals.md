# Intrusion Detection Systems (IDS) & Snort

## Overview

An **Intrusion Detection System (IDS)** monitors network or system activity for suspicious or malicious behavior.

While a firewall controls traffic entering and leaving a network, an IDS focuses on detecting suspicious activity that may have already passed through the firewall.

A simple comparison:

- **Firewall:** Acts like a security guard at the entrance of a building.
- **IDS:** Acts like surveillance cameras monitoring activity inside the building.

When an IDS detects suspicious activity, it generates an alert for security administrators. Unlike an Intrusion Prevention System (IPS), an IDS normally does not automatically block the activity.

---

## Types of IDS

### Host-Based IDS (HIDS)

A **HIDS** is installed directly on individual systems.

It monitors activities related to that specific host, such as:

- System changes
- Suspicious processes
- File activity
- Security events

**Advantages**
- Detailed visibility into individual hosts
- Useful for endpoint monitoring

**Disadvantages**
- Must be installed and managed on every host
- Can consume system resources

---

### Network-Based IDS (NIDS)

A **NIDS** monitors network traffic between multiple systems.

Instead of monitoring only one computer, it analyzes traffic moving throughout the network.

**Advantages**
- Centralized network monitoring
- Can detect attacks affecting multiple systems
- Provides visibility into network communications

---

## IDS Detection Methods

### Signature-Based Detection

Signature-based IDS compares network traffic against known attack patterns called **signatures**.

If traffic matches a stored signature, the IDS generates an alert.

**Advantages**
- Fast detection
- Effective against known attacks
- Usually produces fewer false positives

**Limitation**
- Cannot easily detect new or zero-day attacks without an existing signature.

---

### Anomaly-Based Detection

Anomaly-based IDS first establishes a baseline of normal network or system behavior.

It then detects activity that significantly differs from that baseline.

**Advantages**
- Can detect unknown or zero-day attacks
- Does not depend entirely on known signatures

**Disadvantages**
- Can generate more false positives
- Requires tuning to properly define normal behavior

---

### Hybrid IDS

A **Hybrid IDS** combines signature-based and anomaly-based detection.

It can:

- Detect known attacks using signatures
- Detect unusual or unknown behavior using anomaly detection

This provides broader detection capabilities.

---

# Snort IDS

**Snort** is a widely used open-source network intrusion detection system.

Snort can inspect network traffic and compare it against predefined or custom rules to identify suspicious activity.

Snort rules can be used to detect:

- Port scans
- Suspicious network connections
- ICMP traffic
- Known attack patterns
- Specific protocols
- Custom network activity

Snort also allows administrators to create their own detection rules.

---

## Snort Modes

### Packet Sniffer Mode

Packet Sniffer Mode captures and displays packets traveling through the network.

It does not necessarily perform intrusion detection.

It is useful for:

- Network troubleshooting
- Traffic analysis
- Monitoring network communications

---

### Packet Logging Mode

Packet Logging Mode captures network traffic and stores it for later analysis.

Traffic can be stored in **PCAP format**, allowing security analysts to investigate previous events.

This is useful during:

- Incident response
- Digital forensics
- Root cause analysis

---

### Network Intrusion Detection System Mode

NIDS Mode is Snort's primary IDS functionality.

Snort:

1. Captures network traffic.
2. Compares the traffic against configured rules.
3. Detects matching attack patterns.
4. Generates alerts.

---

# Snort Configuration

Important Snort files may be stored under:

```bash
/etc/snort
```

Snort 3 installations may use different directories depending on how Snort was installed.

A common configuration file is:

```bash
/etc/snort/snort.lua
```

Custom and default rules are typically stored inside:

```bash
/etc/snort/rules/
```

---

# Snort Rule Structure

Example Snort rule:

```text
alert icmp any any -> 127.0.0.1 any (msg:"Loopback Ping Detected"; sid:10003; rev:1;)
```

The basic rule structure contains:

```text
Action Protocol Source-IP Source-Port -> Destination-IP Destination-Port (Rule Options)
```

### Action

```text
alert
```

Tells Snort to generate an alert when traffic matches the rule.

### Protocol

```text
icmp
```

Specifies which network protocol the rule should inspect.

Other protocols may include TCP and UDP.

### Source IP

```text
any
```

Traffic can originate from any IP address.

### Source Port

```text
any
```

Traffic can originate from any port.

### Destination IP

```text
127.0.0.1
```

Specifies the destination address that Snort should monitor.

### Destination Port

```text
any
```

The traffic can reach any destination port.

---

## Rule Metadata

Rule options are placed inside parentheses.

### Message

```text
msg:"Loopback Ping Detected";
```

Defines the alert message displayed when the rule matches.

### Signature ID

```text
sid:10003;
```

The **SID** uniquely identifies the Snort rule.

### Revision

```text
rev:1;
```

Tracks the version of the rule.

If the rule is modified, the revision number should normally be increased.

---

# Creating a Custom Snort Rule

Custom Snort rules can be added to:

```bash
/etc/snort/rules/local.rules
```

Open the file:

```bash
sudo nano /etc/snort/rules/local.rules
```

Example custom rule:

```text
alert icmp any any -> 127.0.0.1 any (msg:"Loopback Ping Detected"; sid:10003; rev:1;)
```

This rule generates an alert whenever ICMP traffic is sent to the loopback address.

---

# Running Snort

Snort can monitor an interface in real time:

```bash
sudo snort -q -l /var/log/snort -i lo -A alert_fast -c /etc/snort/snort.lua
```

Important options:

```text
-q
```

Runs Snort in quiet mode.

```text
-l /var/log/snort
```

Defines the logging directory.

```text
-i lo
```

Specifies the network interface to monitor.

```text
-A alert_fast
```

Uses the fast alert output format.

```text
-c /etc/snort/snort.lua
```

Specifies the Snort configuration file.

---

## Testing the Custom Rule

Ping the loopback address:

```bash
ping 127.0.0.1
```

Because the custom rule monitors ICMP traffic going to `127.0.0.1`, Snort should generate an alert similar to:

```text
"Loopback Ping Detected"
```

This confirms that the rule is functioning correctly.

---

# Analyzing PCAP Files with Snort

Snort can also analyze previously captured network traffic.

Example:

```bash
sudo snort -q -l /var/log/snort -r Task.pcap -A alert_fast -c /etc/snort/snort.lua
```

The `-r` option tells Snort to read traffic from a PCAP file instead of monitoring live network traffic.

This is useful for:

- Forensic investigations
- Analyzing previous attacks
- Reviewing suspicious traffic
- Testing detection rules

---

# Key Takeaways

- Firewalls control network traffic, while IDS solutions detect suspicious activity.
- HIDS monitors individual hosts.
- NIDS monitors network traffic across multiple systems.
- Signature-based detection identifies known attacks.
- Anomaly-based detection identifies deviations from normal behavior.
- Hybrid IDS combines both detection methods.
- Snort is an open-source IDS capable of monitoring live traffic and analyzing PCAP files.
- Snort detection logic is controlled through rules.
- Custom Snort rules can detect specific network activity.
- Snort alerts security administrators when traffic matches a detection rule.
