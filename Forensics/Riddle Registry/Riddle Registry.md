# Writeup: Riddle Registry

## Description

> Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered.
> Find the PDF file here Hidden Confidential Document and uncover the flag within the metadata.

---

## Analysis and Walkthrough

### Step 1: Initial Approach and Basic Information Check
The challenge provides us with a PDF file (`confidential (2).pdf`) and gives a very clear hint: *"uncover the flag within the metadata"*.

> **Note:** Metadata refers to hidden information about a file (for example: creation date, author, software used to create the file, etc.) that is usually not immediately visible when simply opening the file with a standard PDF reader.

### Step 2: Extracting Metadata
To view the metadata of a PDF file, we can use a specialized command-line tool like `exiftool`, or simply by reading the raw file contents using any `text editor`.

Using the `exiftool` command on Kali Linux (or WSL environment):
```bash
exiftool "confidential (2).pdf"
```

### Step 3: Discovering Anomalous Data
While inspecting the return results from the PDF file's metadata table, specifically within the **Author** field, a mysterious string characters emerges:

> **Author**: `cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV9lZTQ1NDk1MH0=`

### Step 4: Decryption
In CTF competitions, when encountering a string consisting of uppercase letters, lowercase letters, numbers, and specifically ending with the equals sign `=`, it is highly probable that the string is encoded using the **Base64** format.

You can decode it by using online Base64 decoding tools like [CyberChef](https://gchq.github.io/CyberChef/) or just quickly using the `base64 -d` command in the Terminal:

```bash
echo "cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV9lZTQ1NDk1MH0=" | base64 -d
```

### Result:
After performing the decryption, the resulting string perfectly matches the standard flag format:
`picoCTF{puzzl3d_m3tadata_f0und!_ee454950}`

---

## 🚩 Flag
```text
picoCTF{puzzl3d_m3tadata_f0und!_ee454950}
```
