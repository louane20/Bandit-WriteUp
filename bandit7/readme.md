# Bandit Level 6 → Level 7

## Level Goal

The password for the next level is stored **somewhere on the server** and has the following properties:

* Owned by user `bandit7`
* Owned by group `bandit6`
* 33 bytes in size

---

## Commands you may need

| Command | Explanation                                         |
| ------- | --------------------------------------------------- |
| `find`  | Search for files and directories based on metadata. |
| `cat`   | Display the contents of a file.                     |

---

## Let's try

Unlike the previous level, the file is not located in the current directory. The challenge states that it can be **anywhere on the server**, so the search must start from the root directory (`/`).

Use the `find` command to search for files matching all the required properties:

```bash id="fr7nby"
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

### Explanation

* `/` → Start searching from the root of the filesystem.
* `-type f` → Search only for **regular files**.
* `-user bandit7` → Match files owned by the user **bandit7**.
* `-group bandit6` → Match files whose group owner is **bandit6**.
* `-size 33c` → Match files whose size is exactly **33 bytes** (`c` = bytes).
* `2>/dev/null` → Redirect **standard error (file descriptor 2)** to `/dev/null`, suppressing permission denied messages generated while traversing protected directories.

Output:

```text id="s9c2ja"
/var/lib/dpkg/info/bandit7.password
```

The matching file is located at:

```text id="xzk7ww"
/var/lib/dpkg/info/bandit7.password
```

Display its contents:

```bash id="h82v7j"
cat /var/lib/dpkg/info/bandit7.password
```

Output:

```text id="rslhza"
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```

The output is the password for **bandit7**.

---

## Technical Notes

* `find` supports combining multiple predicates, allowing files to be filtered simultaneously by **owner**, **group**, **type**, and **size**.
* The redirection operator `2>` redirects **stderr** (standard error). Since many system directories are inaccessible to the current user, `find` would normally print numerous **Permission denied** messages.
* `/dev/null` is a special device file that discards everything written to it, making it useful for suppressing unwanted output.

---

## Solution

```text id="lkkz5u"
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```
