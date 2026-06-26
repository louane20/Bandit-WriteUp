# Bandit Level 12 → Level 13

## Level Goal

The password for the next level is stored in the file `data.txt`, which is a **hexdump** of a file that has been **repeatedly compressed**.

---

## Commands you may need

| Command  | Explanation                                 |
| -------- | ------------------------------------------- |
| `mktemp` | Create a unique temporary directory.        |
| `cp`     | Copy files.                                 |
| `mv`     | Rename or move files.                       |
| `xxd`    | Create or reverse a hexadecimal dump.       |
| `file`   | Identify a file's format from its contents. |
| `gzip`   | Compress or decompress gzip archives.       |
| `bzip2`  | Compress or decompress bzip2 archives.      |
| `tar`    | Create or extract tar archives.             |
| `cat`    | Display file contents.                      |

---

# Let's try

The challenge states that `data.txt` is a **hexdump**, not the original file. Before extracting the compressed layers, we must first reconstruct the binary data.

Since multiple decompression steps are required, create a temporary working directory to avoid modifying files in the home directory.

```bash
mktemp -d
cd /tmp/tmp.xxxxxxxxxx
cp ~/data.txt .
```

---

## Step 1 — Reverse the hexdump

Convert the hexadecimal representation back into its original binary format.

```bash
xxd -r data.txt > data.bin
```

### Explanation

* `xxd -r` performs the **reverse operation** of a hexadecimal dump.
* The output is redirected to `data.bin`.

Identify the file type:

```bash
file data.bin
```

Output:

```text
data.bin: gzip compressed data
```

---

## Step 2 — Decompress the Gzip archive

Rename the file with the appropriate extension before using `gzip`.

```bash
mv data.bin data.gz
gzip -d data.gz
```

Identify the new file:

```bash
file data
```

Output:

```text
data: bzip2 compressed data
```

---

## Step 3 — Decompress the Bzip2 archive

```bash
mv data data.bz2
bzip2 -d data.bz2
```

Check the result:

```bash
file data
```

Output:

```text
data: gzip compressed data
```

---

## Step 4 — Decompress the second Gzip archive

```bash
mv data data.gz
gzip -d data.gz
```

Identify the extracted file:

```bash
file data
```

Output:

```text
data: POSIX tar archive
```

---

## Step 5 — Extract the first TAR archive

```bash
tar -xf data
```

A new archive appears:

```text
data5.bin
```

Identify it:

```bash
file data5.bin
```

Output:

```text
data5.bin: POSIX tar archive
```

Extract it:

```bash
tar -xf data5.bin
```

---

## Step 6 — Decompress the second Bzip2 archive

A new file is created:

```text
data6.bin
```

Identify it:

```bash
file data6.bin
```

Output:

```text
data6.bin: bzip2 compressed data
```

Rename and decompress:

```bash
mv data6.bin data.bz2
bzip2 -d data.bz2
```

Identify the output:

```bash
file data
```

Output:

```text
data: POSIX tar archive
```

---

## Step 7 — Extract the second TAR archive

```bash
tar -xf data
```

A new file appears:

```text
data8.bin
```

Check its format:

```bash
file data8.bin
```

Output:

```text
data8.bin: gzip compressed data
```

---

## Step 8 — Decompress the final Gzip archive

```bash
mv data8.bin data.gz
gzip -d data.gz
```

Identify the resulting file:

```bash
file data
```

Output:

```text
data: ASCII text
```

Display its contents:

```bash
cat data
```

Output:

```text
The password is qQYQiHOBPR8zR61qxYqX45quvihF2uzk
```

The password for **bandit13** is:

```text
qQYQiHOBPR8zR61qxYqX45quvihF2uzk
```

---

## Technical Notes

* A **hexdump** is a hexadecimal representation of binary data.
* `xxd -r` reconstructs the original binary file from its hexadecimal representation.
* The `file` command identifies file formats by inspecting their **magic numbers**, allowing the next decompression tool to be selected correctly.
* `gzip`, `bzip2`, and `tar` each process different archive formats, requiring the correct utility at every stage.
* Using a temporary directory created with `mktemp -d` prevents accidental modification of files outside the working environment.

---

## Solution

```text
qQYQiHOBPR8zR61qxYqX45quvihF2uzk
```
