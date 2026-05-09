# picoCTF: Flag in Flame

## Category
Forensics

## Difficulty
Easy

---

## Description

The SOC team discovered a suspiciously large log file after a recent breach.  
Instead of normal logs, the file contains a huge block of encoded text.
The goal is to analyze the file and uncover any hidden information inside it.

---

## Solution

### 1. Initial analysis

First, I identified the file type using the `file` command:

```bash
file logs.txt
```

Output:

```bash
logs.txt: ASCII text, with very long lines (65536), with no line terminators
```

This indicates a large single-line text file, likely encoded data.

2. Data inspection

I inspected the file content using:

```bash
cat logs.txt
```

The output showed a large encoded string. Based on its structure, it appeared to be Base64 encoded.

3. Base64 decoding

I decoded the file using:

```bash
cat logs.txt | base64 -d > output.jpg
```

This produced an image file.

## Hidden image

![output](files/output.jpg)

4. Hidden data analysis

Opening the image revealed a black stripe containing hex-encoded data:

```7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F62653836303237397D```

5. Hex decoding

Using CyberChef > From Hex, the decoded output revealed the flag.

## Flag
---

picoCTF{forensics_analysis_is_amazing_be860279}

---

# Tools Used
1. file
2. cat
3. base64
4. CyberChef

---

