# Bandit Level 18 → Level 19

## Level Goal

The password for the next level is stored in a file named `readme` in the home directory.

Unfortunately, the `.bashrc` file has been modified to immediately log you out whenever you log in via SSH.

---

## Commands you may need

| Command | Explanation                                                             |
| ------- | ----------------------------------------------------------------------- |
| `ssh`   | Connect to a remote machine using SSH and optionally execute a command. |
| `cat`   | Display the contents of a file.                                         |

---

# Let's try

Normally, when connecting with SSH, the server starts the user's login shell, which reads initialization files such as `.bashrc`.

In this level, `.bashrc` has been modified to immediately terminate the session, making an interactive login impossible.

However, SSH supports executing a command **directly after authentication**, without starting an interactive shell.

Run:

```bash id="b6x8n3"
ssh -p 2220 bandit18@bandit.labs.overthewire.org "cat readme"
```

### Explanation

* `ssh` → Starts an SSH connection.
* `-p 2220` → Specifies the SSH port.
* `bandit18@bandit.labs.overthewire.org` → Remote user and host.
* `"cat readme"` → Command executed directly on the remote server after authentication.

After entering the password for **bandit18**, SSH executes the command remotely and prints the file contents before the session is terminated.

Output:

```text id="x7h4fy"
KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI
```

The output is the password for **bandit19**.

---

## Technical Notes

* SSH can operate in two modes:

  * **Interactive mode**, where a login shell is started.
  * **Remote command mode**, where a specified command is executed directly.
* In this challenge, using **remote command mode** bypasses the modified `.bashrc` because no interactive shell session is required.
* This feature is commonly used for:

  * Remote administration.
  * Automation scripts.
  * Executing one-off commands on remote systems.

---

## Solution

```text id="7kmg0n"
KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI
```
