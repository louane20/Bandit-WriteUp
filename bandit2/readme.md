# Bandit Level 1 → Level 2

## Level Goal

The password for the next level is stored in a file called `-` located in the home directory.

---

## Commands you may need

| Command | Explanation                     |
| ------- | ------------------------------- |
| `ls`    | List files and directories.     |
| `cat`   | Display the contents of a file. |

---

## Let's try

First, list the files in the current directory:

```bash
ls
```

Output:

```text
-
```

The file is named `-`. Since `-` is usually interpreted as standard input by many commands, we need to specify its relative path.

Display the file content using:

```bash
cat ./-
```

Output:

```text
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
```

We have successfully found the password for **bandit2**.

---

## Solution

```text
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
```
