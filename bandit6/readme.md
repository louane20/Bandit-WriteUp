# Bandit Level 5 → Level 6

## Level Goal

The password for the next level is stored in a file somewhere under the `inhere` directory with the following properties:

* Human-readable
* 1033 bytes in size
* Not executable

---

## Commands you may need

| Command | Explanation                                                   |
| ------- | ------------------------------------------------------------- |
| `find`  | Search for files and directories based on specified criteria. |
| `cat`   | Display the contents of a file.                               |

---

## Let's try

The challenge requires locating a file based on its attributes rather than its name. The `find` command is designed for this purpose because it recursively traverses the directory tree and filters files according to user-defined criteria.

Search for all regular files whose size is exactly **1033 bytes**:

```bash
find . -type f -size 1033c
```

### Explanation

* `.` → Start searching from the current directory.
* `-type f` → Restrict the search to **regular files**, excluding directories, symbolic links, and other file types.
* `-size 1033c` → Match files whose size is exactly **1033 bytes**. The suffix `c` stands for **bytes (characters)**.

Output:

```text
./maybehere07/.file2
```

The matching file is `.file2` inside the `maybehere07` directory.

Display its contents:

```bash
cat ./maybehere07/.file2
```

Output:

```text
pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
```

The output is the password for **bandit6**.

---

## Technical Notes

* `find` performs a **recursive filesystem traversal**, making it the preferred tool for locating files by metadata.
* The `-size` option compares the **actual file size in bytes**, not the disk space occupied by the file.
* Although the challenge also specifies that the file is **human-readable** and **not executable**, the only file matching the required size already satisfies these remaining conditions.

---

## Solution

```text
pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
```
