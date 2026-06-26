# Bandit Level 4 → Level 5

## Level Goal

The password for the next level is stored in the **only human-readable file** inside the `inhere` directory.

> **Tip:** If your terminal becomes unreadable after displaying a binary file, use the `reset` command to restore it.

---

## Commands you may need

| Command | Explanation                                         |
| ------- | --------------------------------------------------- |
| `file`  | Determine the type of a file based on its contents. |
| `cat`   | Display the contents of a file.                     |

---

## Let's try

The challenge states that only one file is **human-readable**. Instead of opening every file with `cat`, we first identify their types using the `file` command.

The wildcard `*` is expanded by the shell (**pathname expansion** or **globbing**) before the command is executed. It matches every file in the current directory, allowing `file` to inspect all of them at once.

Run:

```bash
file ./*
```

Output:

```text
./-file00: data
./-file01: data
./-file02: OpenPGP Secret Key
./-file03: data
./-file04: data
./-file05: data
./-file06: Non-ISO extended-ASCII text, with NEL line terminators
./-file07: ASCII text
./-file08: data
./-file09: data
```

The `file` command identifies the format of each file by examining its contents instead of relying on its filename or extension.

Among the results, `./-file07` is the only file recognized as **ASCII text**, making it the only human-readable file.

Display its contents:

```bash
cat ./-file07
```

Output:

```text
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
```

The output is the password for **bandit5**.

---

## Technical Notes

* `file` inspects the **contents** of a file using its binary signature (magic numbers), not its filename.
* The `*` character is a **glob wildcard**. Before executing the command, the shell performs **pathname expansion (globbing)** and replaces `*` with every matching filename.
* Using `file` before `cat` is a good practice when the file type is unknown, as displaying binary data may corrupt the terminal output.

---

## Solution

```text
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
```
