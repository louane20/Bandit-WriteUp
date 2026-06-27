# Bandit Level 15 → Level 16

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to **port 30001** on `localhost` using an **SSL/TLS encrypted connection**.

> **Note:** If you encounter messages such as `DONE`, `RENEGOTIATING`, or `KEYUPDATE`, refer to the **CONNECTED COMMANDS** section of the `openssl s_client` manual.

---

## Commands you may need

| Command            | Explanation                                         |
| ------------------ | --------------------------------------------------- |
| `openssl s_client` | Establish an SSL/TLS connection to a remote server. |

---

## Let's try

Unlike the previous level, the service on port **30001** requires an **SSL/TLS** connection. A plain TCP connection with `nc` is insufficient because the server expects the client to perform a **TLS handshake** before exchanging any application data.

Use the OpenSSL client to establish the encrypted connection:

```bash
openssl s_client -connect localhost:30001
```

### Explanation

* `openssl s_client` → Launches an SSL/TLS client.
* `-connect localhost:30001` → Connects to the service running on `localhost` over TCP port `30001`.

When the TLS handshake completes successfully, the connection remains open and waits for input.

Submit the current level's password:

```text
pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7
```

Output:

```text
Correct!
kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V
```

The output is the password for **bandit16**.

---

## Technical Notes

* **SSL/TLS** is a cryptographic protocol that provides:

  * **Confidentiality** through encryption.
  * **Integrity** using message authentication.
  * **Authentication** via digital certificates.
* Before any application data is exchanged, the client and server perform a **TLS handshake** to negotiate:

  * The TLS version.
  * The cipher suite.
  * Session keys.
* `openssl s_client` is commonly used to:

  * Test SSL/TLS services.
  * Inspect server certificates.
  * Debug TLS handshakes.
* Unlike `nc`, which opens a raw TCP socket, `openssl s_client` implements the complete TLS protocol on top of TCP.

---

## Solution

```text
kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V
```
