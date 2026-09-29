# Digital Forensics Fundamentals

## Overview

Digital forensics focuses on collecting, preserving, examining, and analyzing digital evidence related to cybercrime and other investigations.

## Digital Forensics Process

A common forensic workflow includes:

1. **Collection** – Identify and securely collect digital evidence.
2. **Examination** – Filter and extract relevant data.
3. **Analysis** – Correlate evidence and reconstruct events.
4. **Reporting** – Document methods, findings, and conclusions.

## Types of Digital Forensics

Common areas include:

- Computer forensics
- Mobile forensics
- Network forensics
- Database forensics
- Cloud forensics
- Email forensics

## Evidence Acquisition

Evidence should be collected carefully so that the original data remains unchanged.

Important practices include:

- Obtaining proper authorization before collecting evidence
- Maintaining a chain of custody
- Recording who collected, stored, and accessed evidence
- Using write blockers to prevent accidental changes to storage devices

## Disk and Memory Forensics

### Disk Images

A disk image is a bit-by-bit copy of a storage device.

It can contain:

- Files and documents
- Browser history
- Deleted data
- User activity
- System files

Disk data is generally **non-volatile**, meaning it remains after the system is powered off.

### Memory Images

A memory image captures data stored in RAM.

It may contain:

- Running processes
- Active network connections
- Open files
- Temporary data

RAM is **volatile**, so memory should normally be captured before shutting down a system.

## Common Forensic Tools

### FTK Imager

Used to create and examine forensic disk images.

### Autopsy

Open-source forensic analysis platform used for tasks such as:

- File analysis
- Metadata inspection
- Deleted file recovery
- Keyword searches

### DumpIt

Command-line utility used to capture system memory.

### Volatility

Memory forensics framework used to analyze memory dumps and investigate processes, connections, and other system artifacts.

## Metadata Analysis

Metadata can provide useful information about when and how a file was created.

### PDF Metadata

The `pdfinfo` utility can display information such as:

```bash
pdfinfo example.pdf
```

Possible metadata includes:

- Author
- Creator
- Creation date
- Modification date
- File size
- PDF version

### Image Metadata

EXIF metadata can contain information such as:

- Camera or phone model
- Date and time
- Camera settings
- GPS coordinates

ExifTool can be used to inspect this data:

```bash
exiftool example.jpg
```

## Key Takeaways

- Digital evidence must be collected without altering the original data.
- Chain of custody helps maintain evidence integrity.
- Write blockers help prevent accidental modification of storage devices.
- Disk images preserve non-volatile data.
- Memory images preserve volatile system activity.
- Metadata can reveal useful information about files and images.
- Tools such as FTK Imager, Autopsy, Volatility, `pdfinfo`, and ExifTool are commonly used during forensic investigations.
