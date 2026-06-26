# Bandit Level 3 → Level 4

## Level Goal

The password for the next level is stored in a **hidden file** inside the `inhere` directory.

---

## Commands you may need

| Command  | Explanation                                                       |
| -------- | ----------------------------------------------------------------- |
| `cd`     | Change the current working directory.                             |
| `ls -al` | List all files, including hidden ones, with detailed information. |
| `cat`    | Display the contents of a file.                                   |

---

## Let's try

First, list the contents of the home directory:

```bash
ls -al
```

Output:

```text
total 24
drwxr-xr-x   3 root root 4096 Jun 24 14:59 .
drwxr-xr-x 150 root root 4096 Jun 24 15:02 ..
-rw-r--r--   1 root root  220 Feb 13 12:16 .bash_logout
-rw-r--r--   1 root root 3851 Jun 24 14:50 .bashrc
-rw-r--r--   1 root root  807 Feb 13 12:16 .profile
drwxr-xr-x   2 root root 4096 Jun 24 14:59 inhere
```

The challenge indicates that the password is stored inside the `inhere` directory, so move into it:

```bash
cd inhere
```

Since the file is **hidden**, a regular `ls` command will not display it. In Unix/Linux systems, any filename beginning with a dot (`.`) is considered a **hidden file** and is omitted from the default directory listing.

To display hidden files, use the `-a` option. The `-l` option provides a detailed listing, including permissions, owner, group, file size, and modification date.

```bash
ls -al
```

Output:

```text
total 12
drwxr-xr-x 2 root    root    4096 Jun 24 14:59 .
drwxr-xr-x 3 root    root    4096 Jun 24 14:59 ..
-rw-r----- 1 bandit4 bandit3   33 Jun 24 14:59 ...Hiding-From-You
```

A hidden file named `...Hiding-From-You` is revealed.

Display its contents using:

```bash
cat ...Hiding-From-You
```

Output:

```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```

The output is the password for **bandit4**.

---

## Solution

```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```
