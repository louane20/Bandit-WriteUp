# Bandit Level 9 → Level 10

## Level Goal

The password for the next level is stored in the file `data.txt` in one of the few **human-readable strings**, preceded by several `=` characters.

---

## Commands you may need

| Command   | Explanation                                               |
| --------- | --------------------------------------------------------- |
| `strings` | Extract printable character sequences from a binary file. |
| `grep`    | Search for lines matching a specified pattern.            |

---

## Let's try

The challenge indicates that `data.txt` contains mostly **binary data**, with only a few human-readable strings embedded within it.

Displaying the file with `cat` would produce unreadable output. Instead, use the `strings` command, which extracts only printable ASCII character sequences from a binary file.

Run:

```bash id="x3l5mz"
strings data.txt | grep ====
```

### Explanation

* `strings data.txt` → Scans the binary file and extracts sequences of printable characters.
* `|` → Pipes the extracted strings to the next command.
* `grep ====` → Filters the output, displaying only lines containing several `=` characters, as specified in the challenge.

Output:

```text id="q59o7g"
========== the
========== password
Y========== is
========== B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

The line matching the challenge format contains the password immediately after the `=` characters.

The password for **bandit10** is:

```text id="q0jg0m"
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

---

## Technical Notes

* `strings` is commonly used during **binary analysis** and **reverse engineering** to extract readable text from executable files, libraries, memory dumps, or other binary data.
* By default, `strings` prints sequences of **at least four printable characters**, ignoring binary bytes.
* The pipeline combines:

  * **Extraction** (`strings`)
  * **Pattern matching** (`grep`)
* This is a common workflow in digital forensics and malware analysis to quickly locate embedded messages, URLs, credentials, or configuration strings.

---

## Solution

```text id="4zjlwm"
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```
