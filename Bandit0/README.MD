# Bandit Level 0 

## Level Goal

The goal of this level is to log into the game using SSH.

- Host: `bandit.labs.overthewire.org`
- Port: `2220`
- Username: `bandit0`
- Password: `bandit0`

---

## Commands you may need

| Command | Explanation |
|---------|-------------|
| `ssh` | Connect to a remote machine using Secure Shell (SSH). |

---

## Let's try

First, open a terminal.

Then connect to the Bandit server using SSH:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

When prompted, enter the password:

```text
bandit0
```

After authentication, you are successfully logged in as **bandit0**.

The password for the next level can then be found according to the instructions of Level 1.

---

## Solution

Successfully logged into the Bandit server as **bandit0**.
