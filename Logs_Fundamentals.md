### Log Analysis

Logs are digital records of activity within systems, applications, and networks. They act like digital footprints that help security teams understand what happened during an incident and trace suspicious activity.

Logs are commonly used for:

- Security monitoring and anomaly detection
- Incident investigation and digital forensics
- Troubleshooting system or application issues
- Performance monitoring
- Auditing and compliance

### Common Log Types

- **System Logs** — OS startup, shutdown, drivers, hardware events, and system errors
- **Security Logs** — Authentication, authorization, account changes, policy changes, and suspicious activity
- **Application Logs** — Application activity, updates, changes, and errors
- **Audit Logs** — User actions, data access, system changes, and policy enforcement
- **Network Logs** — Incoming/outgoing traffic, network connections, and firewall activity
- **Access Logs** — Access to web servers, databases, applications, and APIs

### Log Analysis

Log analysis is the process of reviewing logs to find useful information, unusual behavior, or signs of malicious activity.

Because logs can contain thousands of events, analysts use both manual and automated techniques to filter and investigate relevant events.

## Windows Event Logs

Windows records many operating system activities in separate log categories. These logs can be viewed and analyzed using **Event Viewer**.

### Main Windows Log Types

- **Application** — Records application errors, warnings, compatibility issues, and other application-related events.
- **System** — Records operating system events such as startup/shutdown, driver problems, hardware issues, and services.
- **Security** — Records security-related activity such as authentication, account changes, and security policy changes.

### Event Viewer

**Event Viewer** is a built-in Windows utility used to view, search, and filter event logs.

Important event log fields include:

- **Description** — Detailed information about the event
- **Log Name** — The log category where the event was recorded
- **Logged** — Date and time of the event
- **Event ID** — Unique identifier for a specific type of activity

### Important Windows Event IDs

| Event ID | Description |
|---|---|
| **4624** | Successful user login |
| **4625** | Failed user login |
| **4634** | User logged off |
| **4720** | User account created |
| **4722** | User account enabled |
| **4724** | Password reset attempt |
| **4725** | User account disabled |
| **4726** | User account deleted |

Event IDs make investigations easier because analysts can filter logs for specific activity. For example, filtering for **4624** shows successful login events.

---

## Web Server Access Logs

Web servers record requests made by users. These logs can help identify suspicious activity, errors, accessed resources, and the source of requests.

A typical Apache access log can be found at:

```bash
/var/log/apache2/access.log
```

### Common Access Log Fields

- **IP Address** — Source IP making the request
- **Timestamp** — Time the request occurred
- **HTTP Method** — Action such as `GET` or `POST`
- **URL** — Requested resource
- **Status Code** — Server response
- **User-Agent** — Information about the user's browser and operating system

Example:

```text
172.16.0.1 - - [06/Jun/2024:13:58:44] "GET /products HTTP/1.1" 404
```

---

## Manual Log Analysis Commands

### `cat`

Displays the contents of a log file.

```bash
cat access.log
```

It can also combine multiple log files:

```bash
cat access1.log access2.log > combined_access.log
```

### `grep`

Searches a log file for specific strings or patterns.

```bash
grep "192.168.1.1" access.log
```

This is useful for finding activity related to a specific IP address, URL, username, or other indicator.

### `less`

Allows large log files to be viewed page by page.

```bash
less access.log
```

Useful controls:

- `Space` — Next page
- `b` — Previous page
- `/pattern` — Search for a value
- `n` — Next search result
- `N` — Previous search result

These tools provide a simple way to manually inspect and filter logs during investigations.
