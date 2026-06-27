# Bandit Level 19 → Level 20

## Level Goal

To gain access to the next level, use the **setuid** binary located in the home directory.

The password for the next level is stored in the usual location:

```text
/etc/bandit_pass/bandit20
```

However, this file can only be read after executing the provided **setuid** program.

---

## Commands you may need

| Command | Explanation                                   |
| ------- | --------------------------------------------- |
| `ls`    | List directory contents.                      |
| `file`  | Identify a file's type.                       |
| `./`    | Execute a program from the current directory. |
| `cat`   | Display file contents.                        |

---

# Let's try

List the files in the home directory:

```bash id="g4yl8w"
ls -l
```

Output:

```text id="5wdr5j"
-rwsr-x--- 1 bandit20 bandit19 ... bandit20-do
```

The permission string begins with:

```text id="4x3cln"
-rwsr-x---
```

The **`s`** in the owner's execute field indicates that the **Set User ID (SUID)** bit is enabled.

Execute the program without arguments to display its usage:

```bash id="6r4kmu"
./bandit20-do
```

The program explains that it executes a command with the privileges of **bandit20**.

Use it to read the password file:

```bash id="lnk6jp"
./bandit20-do cat /etc/bandit_pass/bandit20
```

Output:

```text id="y25hxe"
4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA
```

The output is the password for **bandit20**.

---

## Technical Notes

* **SUID (Set User ID)** is a special Unix permission bit.
* When a binary has the SUID bit set, it executes with the **effective UID (EUID)** of the file owner rather than the user who launched it.
* In this challenge:

  * The binary is owned by **bandit20**.
  * It is executed by **bandit19**.
  * Because of the SUID bit, the process runs with **bandit20's privileges**, allowing it to read `/etc/bandit_pass/bandit20`.
* The real user remains `bandit19`, but the kernel assigns an **effective user ID** of `bandit20` for the lifetime of the process.

---

## Solution

```text id="n6hfxm"
4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA
```
