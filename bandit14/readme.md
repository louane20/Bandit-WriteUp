# Bandit Level 13 → Level 14

## Level Goal

The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`.

Instead of receiving the password directly, this level provides a **private SSH key** that must be used to authenticate as `bandit14`.

---

## Commands you may need

| Command | Explanation                            |
| ------- | -------------------------------------- |
| `scp`   | Securely copy files over SSH.          |
| `ssh`   | Connect to a remote machine using SSH. |
| `cat`   | Display the contents of a file.        |

---

# Let's try

A private SSH key named `sshkey.private` is available in the home directory of `bandit13`.

Since the key is required on the local machine, copy it using `scp`:

```bash id="g4gsr8"
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```

### Explanation

* `scp` → Securely copies files over SSH.
* `-P 2220` → Specifies the SSH port.
* `bandit13@bandit.labs.overthewire.org:sshkey.private` → Source file on the remote server.
* `.` → Save the file in the current local directory.

After entering the password for `bandit13`, the private key is downloaded.

Output:

```text id="wjh8uk"
sshkey.private                100% 2602    11.4KB/s   00:00
```

---

## Logging in with the private key

SSH allows authentication using a **private key** instead of a password.

The `-i` option specifies the identity file to use during authentication.

Initially, the following command was executed:

```bash id="s3yd9h"
ssh -i bandit14_key -p 2220 bandit14@bandit.labs.overthewire.org
```

Output:

```text id="a8gnmn"
Warning: Identity file bandit14_key not accessible: No such file or directory.
```

### Explanation

The file `bandit14_key` does not exist. SSH therefore cannot load the specified identity file and falls back to **password authentication**.

Using the correct filename resolves the issue:

```bash id="2jhv0h"
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

SSH successfully authenticates using the private key without prompting for a password.

---

## Retrieve the password

Once logged in as `bandit14`, display the password:

```bash id="hbd4oq"
cat /etc/bandit_pass/bandit14
```

Output:

```text id="18j5op"
aaWecNkG4FhxJQxz07uiwzVP6bJiYS65
```

The output is the password for **bandit14**.

---

## Technical Notes

* SSH supports multiple authentication mechanisms, including **password authentication** and **public key authentication**.
* A **private key** must always remain secret. Its corresponding **public key** is installed on the remote server (typically in `~/.ssh/authorized_keys`).
* During authentication, the SSH server verifies that the client possesses the matching private key without transmitting the key itself over the network.
* The `-i` option instructs the SSH client to use a specific identity file instead of the default keys stored in `~/.ssh/`.

---

## Solution

```text id="pibfhb"
aaWecNkG4FhxJQxz07uiwzVP6bJiYS65
```
