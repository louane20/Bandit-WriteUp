# Bandit Level 7 → Level 8

## Level Goal

The password for the next level is stored in the file `data.txt` next to the word `millionth`.

---

## Commands you may need

| Command | Explanation                                |
| ------- | ------------------------------------------ |
| `cat`   | Display the contents of a file.            |
| `grep`  | Search for lines matching a given pattern. |

---

## Let's try

The challenge specifies that the password is located on the same line as the word **`millionth`** inside `data.txt`.

Instead of reading the entire file manually, we can use `grep` to search for the matching line.

Run:

```bash
cat data.txt | grep millionth
```

### Explanation

* `cat data.txt` → Sends the contents of `data.txt` to the standard output.
* `|` (**pipe**) → Redirects the standard output of the first command to the standard input of the second command.
* `grep millionth` → Filters the input and prints only the line containing the pattern `millionth`.

Output:

```text
millionth       VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```

The second column is the password for **bandit8**.

> **Note:** Since `grep` can read files directly, the pipeline is optional. The following command produces the same result and is more efficient:

```bash
grep millionth data.txt
```

This avoids creating an unnecessary pipeline, as `grep` opens and reads the file itself.

---

## Technical Notes

* A **pipe (`|`)** connects the standard output (**stdout**) of one process to the standard input (**stdin**) of another process.
* `grep` performs **pattern matching** and prints every line containing the specified pattern.
* When `grep` receives a filename as an argument, it reads the file directly. Therefore, using `cat` before `grep` in this case is considered an **unnecessary use of `cat` (UUOC)**.

---

## Solution

```text
VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```
