# Writeup: Glory of the Garden
- **Hint:** "What is a hex editor?"

## Objective
Find the flag hidden inside the image file `garden.jpg`.

## Analysis & Solution

1. **Initial Approach:** 
   The challenge provides a JPEG image file and a hint related to a "hex editor". This indicates that the flag information is not in the normally displayed image part, but is hidden within the binary data of the image file.

2. **Reconnaissance Technique:**
   Instead of using a hex editor immediately, the simplest and most common way to find hidden text strings in a binary file is to use the `strings` tool in Linux/Unix. The `strings` command extracts all printable character sequences from the file.

3. **Execution:**
   Run the `strings` command on the image file and search for the standard flag format (which is `picoCTF{` in this case):
   
   ```bash
   strings garden.jpg | grep "picoCTF"
   ```

## Flag
`picoCTF{more_than_m33ts_the_3y398ee229a}`
