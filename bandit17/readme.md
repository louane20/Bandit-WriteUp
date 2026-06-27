# Bandit Level 16 → Level 17

## Level Goal

The credentials for the next level can be retrieved by submitting the current level's password to **one of the ports between 31000 and 32000** on `localhost`.

The challenge consists of two steps:

1. Identify which ports are open.
2. Determine which service uses **SSL/TLS** and returns the SSH private key for the next level.

---

## Commands you may need

| Command            | Explanation                                                |
| ------------------ | ---------------------------------------------------------- |
| `nmap`             | Discover hosts, open ports, and identify running services. |
| `openssl s_client` | Establish an SSL/TLS connection to a remote service.       |
| `ssh`              | Connect to a remote host using SSH.                        |
| `cat`              | Display file contents.                                     |

---

# Let's try

Since the target service is listening on an **unknown port** between `31000` and `32000`, begin by scanning the entire range with **Nmap**.

```bash
nmap -sV -p 31000-32000 localhost
```

### Explanation

* `nmap` → Network discovery and port scanning utility.
* `-sV` → Performs **service version detection**, identifying the application running on each open port.
* `-p 31000-32000` → Restricts the scan to ports **31000–32000**.
* `localhost` → Scan the local machine.

Output:

```text
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
```

---

## Identify the correct service

The scan reveals two SSL-enabled services:

* **31518** → `ssl/echo`
* **31790** → `ssl/unknown`

The `ssl/echo` service simply echoes any input it receives and therefore cannot provide the next credentials.

The service running on **31790** is unidentified but responds differently, making it the most likely candidate.

Connect using OpenSSL:

```bash
openssl s_client -connect localhost:31790
```

After the TLS handshake completes, submit the current password:

```text
BfMYroe26WYalil77FoDi9qh59eK5xNr
```

The server responds with an **SSH private key**.

Save the entire key into a file named:

```text
key.private
```

---

## Authenticate using the private key

Use the retrieved key to authenticate as **bandit17**.

```bash
ssh -i key.private -p 2220 bandit17@bandit.labs.overthewire.org
```

### Explanation

* `-i key.private` → Specifies the SSH private key used for authentication.
* `-p 2220` → Connects to the SSH service on port 2220.
* `bandit17@bandit.labs.overthewire.org` → Target account.

Authentication succeeds without requiring a password.

---

## Retrieve the password

Display the password for the next level:

```bash
cat /etc/bandit_pass/bandit17
```

Output:

```text
pWXMAZoxGC8JmDMfmT5MGEsobMM3vnj2
```

The output is the password for **bandit17**.

---

## Technical Notes

* **Nmap** performs **service fingerprinting** with the `-sV` option by interacting with open ports and comparing responses against its signature database.
* The `echo` service simply returns any received data unchanged, making it useful for testing but not for this challenge.
* `openssl s_client` is commonly used to manually interact with SSL/TLS-enabled services after completing the TLS handshake.
* The service on port **31790** returns an **OpenSSH private key**, which is then used for **public key authentication** instead of password authentication.
* SSH authenticates the client by proving possession of the private key corresponding to the public key stored on the server.

---

## Solution

```text
pWXMAZoxGC8JmDMfmT5MGEsobMM3vnj2
```
