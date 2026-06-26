# Bandit Level 11 → Level 12

## Level Goal

The password for the next level is stored in the file `data.txt`, where all lowercase (`a-z`) and uppercase (`A-Z`) letters have been **rotated by 13 positions (ROT13)**.

---

## Commands you may need

| Command | Explanation                                              |
| ------- | -------------------------------------------------------- |
| `cat`   | Display the contents of a file.                          |
| `tr`    | Translate or replace characters from one set to another. |

---

## Let's try

The challenge states that the text has been encoded using **ROT13**, a substitution cipher that rotates each alphabetical character by **13 positions**.

For example:

```text
A → N
B → O
...
N → A
O → B

a → n
b → o
...
n → a
o → b
```

Since the English alphabet contains **26 letters**, rotating by 13 positions is symmetric. Applying ROT13 **twice** restores the original text.

To decode the file, use the `tr` command:

```bash id="u48l4g"
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### Explanation

* `cat data.txt` → Sends the file contents to the standard output.
* `|` → Pipes the output to the next command.
* `tr` → Performs **character-by-character translation**.
* `'A-Za-z'` → Defines the source character set (uppercase and lowercase letters).
* `'N-ZA-Mn-za-m'` → Defines the destination set, rotating each letter by 13 positions.

Output:

```text id="b8r8py"
The password is GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

The password for **bandit12** is:

```text id="5b3l9u"
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

---

## Technical Notes

* **ROT13** is a special case of the **Caesar cipher**, where the shift is exactly **13**.
* Because the alphabet contains 26 letters, ROT13 is **self-inverse**: applying the transformation twice returns the original text.
* `tr` performs **character translation**, replacing each character from the source set with the corresponding character in the destination set.
* Unlike encryption algorithms, ROT13 provides **no cryptographic security** and is commonly used only to obfuscate text.

---

## Solution

```text id="4oxrr8"
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```
