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

The filename contains whitespace characters. Before executing a command, the shell parses the command line and performs **word splitting**, where unquoted spaces are treated as argument separators.

For example, the following command would be interpreted as multiple arguments instead of a single filename:

```bash
cat --spaces in this filename--
```

To prevent **word splitting**, we use **shell quoting** by enclosing the filename in double quotes. This ensures the shell passes the entire filename as a single argument to `cat`.

The `./` prefix specifies that the file is located in the current working directory (relative path).

Run:

```bash
cat ./"--spaces in this filename--"
```

Output:

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

The output is the password for **bandit3**.

---

## Solution

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```
