# Bandit Level 0 → Level 1

## Level Goal

The password for the next level is stored in a file called `readme` located in the home directory.

Use this password to log into **bandit1** using SSH.

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
readme
```

The `readme` file looks interesting. Display its content using:

```bash
cat readme
```

Output:

```text
Congratulations on your first steps into the bandit game!!

The password you are looking for is:

6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```

We have successfully found the password for **bandit1**.

---

## Solution

```text
6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```
