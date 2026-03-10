# 📝 Writeup: DISKO 1 (picoCTF)

## Objective
Find the hidden flag inside the disk image file `disko-1.dd`.

## Reconnaissance and Analysis (Methodology)
Based on the challenge description, the author provided a very clear hint: **"hint: Maybe Strings could help?"**.

This implies that the flag is not encoded or hidden using complex techniques (such as steganography or file system structures) but is simply a plaintext string scattered somewhere inside the disk image file (RAW format).

Instead of having to mount this drive or use complex forensics analysis tools like Autopsy or FTK Imager, we can use the `strings` tool in Linux to extract all readable text strings from this binary file.

## Exploitation (Solution)

**Step 1:** Open the Terminal (in a Linux or WSL environment).

**Step 2:** Use the `strings` command combined with `grep` to filter out the picoCTF flag format (which usually starts with `picoCTF{`).

The command syntax will be as follows:
```bash
strings disko-1.dd | grep "picoCTF{"
```

*(Note: If you encounter difficulties with large image files, string loops may contain a lot of noise characters. You can use the command `grep -a -o -E 'picoCTF\{.*?\}'` to search using Regular Expressions directly via grep to accurately output the flag.)*

**Step 3:** Observe the results from the Terminal
The system scans through the binary file system and prints the string matching the search:
```bash
$ grep -a -i -o -E 'picoCTF\{.*?\}' disko-1.dd
picoCTF{1t5_ju5t_4_5tr1n9_be6031da}
```

## 🚩 Result (Flag)
`picoCTF{1t5_ju5t_4_5tr1n9_be6031da}`
