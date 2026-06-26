# Bandit Level 14 → Level 15

## Level Goal

The password for the next level can be retrieved by submitting the password of the current level to **port 30000** on `localhost`.

---

## Commands you may need

| Command | Explanation                          |
| ------- | ------------------------------------ |
| `nc`    | Create TCP/UDP connections (Netcat). |

---

# Let's try

The challenge requires connecting to a service listening on **TCP port 30000** of the local machine (`localhost`) and sending the current level's password.

`Netcat` (`nc`) is often referred to as the **Swiss Army knife of networking** because it can establish TCP/UDP connections, send data, receive responses, and interact with network services.

Connect to the service:

```bash
nc -v localhost 30000
```

### Explanation

* `nc` → Launches Netcat.
* `-v` → Enables **verbose mode**, displaying connection details.
* `localhost` → Refers to the local machine (`127.0.0.1`).
* `30000` → The TCP port where the service is listening.

Output:

```text
Connection to localhost (127.0.0.1) 30000 port [tcp/*] succeeded!
```

Once the TCP connection is established, enter the current level's password:

```text
aaWecNkG4FhxJQxz07uiwzVP6bJiYS65
```

The server validates the password and returns the password for the next level:

```text
Correct!
pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7
```

The output is the password for **bandit15**.

---

## Technical Notes

* **Netcat (`nc`)** is a low-level networking utility capable of opening raw TCP or UDP connections.
* `localhost` resolves to the loopback IP address `127.0.0.1`, meaning the client communicates with a service running on the same machine.
* Once the TCP connection is established, anything typed into the terminal is transmitted directly to the remote service through the socket.
* This challenge demonstrates a simple **client-server interaction**, where:

  1. The client connects to a TCP socket.
  2. The client sends the current password.
  3. The server validates the input.
  4. The server returns the password for the next level.

---

## Solution

```text
pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7
```
