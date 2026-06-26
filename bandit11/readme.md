# Bandit Level 10 → Level 11

## Level Goal

The password for the next level is stored in the file `data.txt`, which contains **Base64-encoded** data.

---

## Commands you may need

| Command  | Explanation                                             |
| -------- | ------------------------------------------------------- |
| `base64` | Encode or decode data using the Base64 encoding scheme. |

---

## Let's try

The challenge states that the contents of `data.txt` are **Base64-encoded**. Base64 is an **encoding** scheme, not an encryption algorithm. Its purpose is to represent binary data using printable ASCII characters.

To recover the original text, decode the file using the `-d` (decode) option:

```bash
base64 -d data.txt
```

### Explanation

* `base64` → Invokes the Base64 utility.
* `-d` → Decodes Base64-encoded input back to its original form.
* `data.txt` → The file containing the encoded data.

Output:

```text
The password is pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```

The password for **bandit11** is:

```text
pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```

---

## Technical Notes

* **Base64 is an encoding format, not encryption.** It does not provide confidentiality and can be reversed without a key.
* Base64 represents binary data using **64 printable characters**:

  * `A–Z`
  * `a–z`
  * `0–9`
  * `+`
  * `/`
* The `=` character is used as **padding** when the input length is not a multiple of 3 bytes.
* Base64 is commonly used in:

  * Email attachments (MIME)
  * JSON Web Tokens (JWT)
  * HTTP Basic Authentication
  * PEM certificates
  * APIs that transport binary data over text-based protocols

---

## Solution

```text
pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```
