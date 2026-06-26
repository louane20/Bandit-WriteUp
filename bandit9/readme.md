# Bandit Level 8 → Level 9

## Level Goal

The password for the next level is stored in the file `data.txt` and is the **only line that occurs exactly once**.

---

## Commands you may need

| Command | Explanation                                       |
| ------- | ------------------------------------------------- |
| `sort`  | Sort lines of text alphabetically.                |
| `uniq`  | Filter or report repeated lines in a sorted file. |

---

## Let's try

The challenge asks for the only line that appears **exactly once** in `data.txt`.

The `uniq` command can identify unique or duplicate lines, but it only compares **adjacent** lines. Therefore, the input **must be sorted first** so that identical lines are grouped together.

Run:

```bash
sort data.txt | uniq -u
```

### Explanation

* `sort data.txt` → Sorts all lines alphabetically, ensuring identical lines become adjacent.
* `|` → Pipes the sorted output to the next command.
* `uniq -u` → Prints only the lines that appear **exactly once**.

Output:

```text
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```

The output is the password for **bandit9**.

---

## Technical Notes

* `uniq` **does not search the entire file** for duplicates. It only compares **consecutive (adjacent) lines**.
* Without sorting, duplicate lines scattered throughout the file would not be detected correctly.
* The pipeline follows a common Unix pattern:

  1. **Transform** the data (`sort`).
  2. **Filter** the result (`uniq`).

For example:

```text
apple
banana
apple
```

Running:

```bash
uniq
```

would produce:

```text
apple
banana
apple
```

because the two `apple` lines are **not adjacent**.

After sorting:

```text
apple
apple
banana
```

`uniq -u` correctly returns:

```text
banana
```

---

## Solution

```text
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```
