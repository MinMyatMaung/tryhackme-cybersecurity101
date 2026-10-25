# CyberChef Basics

CyberChef is a browser-based cybersecurity tool designed for transforming, decoding, encoding, and analyzing data. It works like a **Swiss Army knife for cyber tasks**, supporting simple operations such as Base64 and XOR as well as encryption-related operations such as AES and RSA.

CyberChef can be used directly online or downloaded and run locally for offline analysis.

## Main Areas

CyberChef is divided into four main sections:

- **Operations** – Contains the available tools and transformations.
- **Recipe** – Allows multiple operations to be combined and executed in sequence.
- **Input** – Where text, files, or folders are loaded for processing.
- **Output** – Displays the results after the recipe is executed.

## Operations

CyberChef provides a large collection of operations that can be searched and added to a recipe.

Common examples include:

- `From Morse Code` – Converts Morse code into readable text.
- `URL Encode / URL Decode` – Converts characters to and from URL percent encoding.
- `To Base64 / From Base64` – Encodes or decodes Base64 data.
- `To Hex` – Converts text into hexadecimal values.
- `To Decimal` – Converts text into decimal character values.
- `ROT13` – Applies a Caesar-style character rotation.
- `Extract IP addresses` – Finds IPv4 and IPv6 addresses.
- `Extract URLs` – Finds URLs in supplied data.
- `Extract email addresses` – Identifies email addresses.
- `To/From UNIX Timestamp` – Converts between readable dates and UNIX timestamps.

## Recipes

A **recipe** is a sequence of operations applied to the input data.

CyberChef allows users to:

- Drag operations into the recipe area
- Configure operation settings
- Save and load recipes
- Clear recipes
- Manually process data using **BAKE!**
- Enable **Auto Bake** to process input automatically

Recipes are useful when data needs to go through several transformations in a specific order.

## Input and Output

The Input area accepts:

- Typed or pasted text
- Individual files
- Entire folders
- Multiple input tabs

The Output area displays the processed result and allows users to:

- Save the output
- Copy raw output
- Replace the current input with the output
- Expand the output pane

## Basic CyberChef Workflow

A useful workflow when analyzing data is:

1. **Define the objective**  
   Determine what you are trying to discover or convert.

2. **Provide the input**  
   Paste or upload the data into CyberChef.

3. **Select operations**  
   Choose operations that match the suspected data format or encoding.

4. **Analyze the result**  
   Check whether the output makes sense.

5. **Repeat if necessary**  
   Modify the recipe or try another operation until the expected result is found.

For example, if an unknown string is discovered during an investigation, possible decoding operations such as Base64, ROT13, Base85, or ROT47 can be tested.

## Base Encoding

Base encodings represent binary data using readable ASCII characters.

Common examples include:

- Base64
- Base85
- Base58
- Base62

For example:

```text
THM → VEhN
```

In Base64, the original data is converted into binary, divided into 6-bit groups, converted to decimal indexes, and finally mapped to characters from the Base64 character set.

## Security Use Cases

CyberChef can be useful for:

- Decoding suspicious strings
- Analyzing malware-related data
- Extracting indicators of compromise
- Finding IP addresses, URLs, and email addresses
- Converting hexadecimal or decimal data
- Working with timestamps
- Investigating encoded URLs
- Performing quick data transformations during incident response

## Key Takeaway

CyberChef simplifies many common cybersecurity data-processing tasks by allowing operations to be combined into reusable recipes. Instead of using several separate command-line tools or scripts, analysts can quickly inspect, decode, transform, and extract information from data within one interface.
