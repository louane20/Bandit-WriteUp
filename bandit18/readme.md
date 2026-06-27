# Bandit Level 17 → Level 18

## Level Goal

There are two files in the home directory:

* `passwords.old`
* `passwords.new`

The password for the next level is stored in `passwords.new` and is **the only line that differs** between the two files.

> **Note:** If you receive `Byebye!` when logging into `bandit18`, this behavior is expected and relates to the next challenge.

---

## Commands you may need

| Command | Explanation                                                   |
| ------- | ------------------------------------------------------------- |
| `diff`  | Compare two files line by line and display their differences. |

---

# Let's try

The challenge requires identifying the only line that changed between two versions of the same file.

The `diff` utility compares files line by line and reports all detected differences.

Run:

```bash
diff passwords.new passwords.old
```

### Explanation

* `diff` → Compares two text files.
* `passwords.new` → The updated file.
* `passwords.old` → The original file.

Output:

```text
42c42
< OQxXZjELndr90zuhOTDYBEomI0SZITXI
---
> qOg5pVOjPx9x9VccyYBADiT4xxyoUB8D
```

### Understanding the output

The first line:

```text
42c42
```

means:

* `42` (left) → Line **42** in `passwords.new`.
* `c` → **Change** operation.
* `42` (right) → Line **42** in `passwords.old`.

The symbols used by `diff` have the following meanings:

* `<` → Line from the **first** file (`passwords.new`).
* `>` → Line from the **second** file (`passwords.old`).
* `---` → Separator between the two versions.

Since the challenge specifies that the password is stored in **`passwords.new`**, the correct value is the line prefixed with `<`:

```text
OQxXZjELndr90zuhOTDYBEomI0SZITXI
```

---

## Technical Notes

* `diff` implements a comparison algorithm (based on the **Longest Common Subsequence (LCS)** problem) to identify insertions, deletions, and modifications between two text files.
* Common operation codes include:

  * `c` → **Change**
  * `a` → **Add**
  * `d` → **Delete**
* The order of the files matters. Running:

```bash
diff passwords.new passwords.old
```

is different from:

```bash
diff passwords.old passwords.new
```

because the `<` and `>` markers are reversed.

---

## Solution

```text
OQxXZjELndr90zuhOTDYBEomI0SZITXI
```
