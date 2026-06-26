# Bandit Level 2 → Level 3

## Level Goal

The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory.

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
--spaces in this filename--
```

The filename contains spaces, so we need to enclose it in quotes when using the `cat` command.

Display the file content using:

```bash
cat ./"--spaces in this filename--"
```

Output:

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

We have successfully found the password for **bandit3**.

---

## Solution

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```
