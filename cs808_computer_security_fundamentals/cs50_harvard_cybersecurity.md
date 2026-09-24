# Lecture 0 - Securing Accounts

## 1. Fundamental Security Concepts

- **Authentication vs. Authorization:**
  - Authentication is the process of proving who you are (e.g., using a username and password)

  - Authorization determines what access level or permissions you have once your identity is authenticated

- **The Usability vs Security Trade-off:**

  The central balancing act in cybersecurity.

  Enhancing security (e.g., requiring 64-character passwords or strict rate limits) often increases friction for users, whereas prioritizing convenience can introduce severe vulnerabilities

- **Relativity and Resources:**

  Security is not absolute; it is about raising the bar and increasing the cost, time, and effort required for an adversary to gain unauthorized access

## 2. Password Mathematics & Strength

Password security relies on exponential growth in total possibilities:

- 4-Digit Numeric PIN:

  $10^4 = 10,000$ possibilities. A simple script can test all combinations in milliseconds.

- 4-Letter Code (Case-Sensitive):

  $52^4 \approx 7.3 \text{ million}$ possibilities. Automated scripts crack this in seconds.

- 4-Character Code (Letters, Digits, Punctuation):

  $94^4 \approx 78 \text{ million}$ possibilities. Takes several minutes to crack.

- 8-Character Complex Password:

  $94^8 \approx 6 \text{ quadrillion}$ possibilities. Brute-forcing becomes computationally infeasible, making the attack take years or lifetimes.

## 3. Cyber Attack Vectors

- **Dictionary Attack:**

  An attacker uses automated software and a pre-compiled wordlist (dictionary) to systematically guess common words or language terms

- **Brute-Force Attack:**

  Software tries every possible combination of letters, numbers, and symbols until the correct password is found

- **Credential Stuffing:**

  Attackers take stolen username and password pairs from previously breached databases and automatically test them across other popular websites, exploiting widespread password reuse

- **Social Engineering:**

  Psychological manipulation that tricks individuals into voluntarily handing over sensitive information (e.g., prompting someone to write down a password or disclose security answers)

- **Phishing:**

  Technical social engineering using fraudulent emails or cloned, realistic-looking web interfaces (e.g., fake Gmail or PayPal login pages) to capture credentials or two-factor codes

- **SIM Swapping:**

  Convincing a mobile carrier to transfer a victim's phone number to an attacker's SIM card, enabling the attacker to intercept SMS-based authentication codes

- **Malware & Keylogging:**

  Malicious software installed on a device that records keystrokes and transmits entered passwords and single-use codes directly to an attacker's server

- **Machine-in-the-Middle (MitM):**

  Intercepting or eavesdropping on unencrypted or compromised communications passing through intermediate network nodes (routers, servers, ISPs)

## 4. NIST Guidelines & Defensive Recommendations

The National Institute of Standards and Technology (NIST) provides industry best practices for account security:

- **Minimum & Maximum Lengths:**

  Passwords must be at least 8 characters long, and services should support up to 64 characters (including ASCII, spaces, and Unicode/emojis). Long passphrases or sentences are easier for humans to remember while providing massive combinatorial complexity.

- **Breach & Dictionary Screening:**

  Authentication systems must check new passwords against known compromised password corpuses, dictionary words, repetitive sequences (e.g., 1235abcd, 0000), and context-specific terms (e.g., "Gmail password")

- **Eliminate Hints & Personal Questions:**

  Systems should not store hints or prompt for secret questions (e.g., "first pet's name"), as this information is easily discoverable via social media or public records

- **Stop Mandatory Expirations:**

  Forcing users to change passwords every 30–90 days leads to predictable, weak variations (e.g., Password1 to Password2), degrading security

- **Rate Limiting:**

  Implementing account lockouts or exponential delays after consecutive failed login attempts (e.g., 10 failed attempts) severely throttles brute-force tools

## 5. Multi-Factor Authentication (MFA) & Defense Tools

- **Three Authentication Factors:**
  - Knowledge Factor: Something you know (e.g., password, PIN)

  - Possession Factor: Something you have (e.g., physical key fob, smartphone, authenticator app)

  - Inherence Factor: Something you are (e.g., biometrics like fingerprints or facial recognition)

- **True 2FA vs. Two-Step Verification:**

  True 2FA requires at least two distinct factor types (e.g., knowledge + possession), whereas two-step verification may simply require two passwords.

- **One-Time Passwords (OTP):**

  Time-synchronized codes sent via app, SMS, or hardware token. Authenticator apps and push notifications are preferred over SMS, as SMS is vulnerable to SIM swapping.

- **Single Sign-On (SSO):**

  Logging into services via trusted providers (e.g., Google or Facebook) using cryptographic verification without exposing your actual password to third-party sites.

- **Password Managers:**

  Software (such as Bitwarden, 1Password, or built-in OS tools like Apple Keychain and Google Password Manager) that generates, encrypts, and auto-fills unique, complex passwords for every site, protected by a single, strong master password. They also mitigate phishing by refusing to auto-fill on lookalike domain names.

- **Passkeys:**

  An emerging standard leveraging asymmetric cryptography (public/private key pairs) tied to device biometrics, eliminating traditional passwords and protecting against phishing entirely. (Note: Avoid voice-recognition biometrics due to the rise of AI audio deepfakes).

---

# Lecture 1 - Securing Data

## 1. Password Hashing & Salting (Server-Side Security)

- **Cleartext Risk:**

  Storing passwords in plain text on servers exposes all user credentials if the database is breached.

- **One-Way Hashing:**

  Servers pass passwords through a mathematical hash function (such as SHA-2 or SHA-3) to convert them into fixed-length, non-reversible strings. Upon login, the server hashes the user's input and compares it against the stored hash value.

- **Rainbow Tables & Dictionary Attacks:**

  Attackers can pre-calculate hashes for dictionary words or common passwords to rapidly reverse hashes.

- **Salting:**

  To prevent identical passwords (e.g., two users choosing "cherry") from producing identical hashes, systems append a unique, random string (a "salt") to each password prior to hashing.

- **"Forgot Password" Red Flag:**

  If a website emails your actual original password when you request a reset, it means the server stores passwords in plaintext or decryptable form rather than standard one-way hashes — a major security flaw.

## 2. Cryptography Fundamentals: Codes, Ciphers, & Symmetric Encryption

- **Codes vs Ciphers:**
  - Codes substitute entire words or phrases with code words defined in a pre-shared codebook.

  - Ciphers operate algorithmically on individual letters, characters, or bits.

- **Symmetric (Secret Key) Encryption:**
  - Both the sender and receiver use the same secret key to encrypt and decrypt messages.

  - Examples include historical ciphers like the Caesar Cipher (rotational shift) as well as modern standards like AES (Advanced Encryption Standard) and Triple DES.

- **The Shared Secret Problem:**
  Symmetric encryption assumes both parties already share a secret key, creating a chicken-and-egg problem for communicating securely over an untrusted network.

## 3. Public Key (Asymmetric) Cryptography & Key Exchange

- **Public/Private Key Pairs:**

  Asymmetric encryption uses two mathematically linked keys. The public key can be freely shared with anyone to encrypt messages, while the private key is kept secret by the owner to decrypt those messages.

- **RSA Algorithm:**

  Uses the product ($n$) of two large prime numbers ($p$ and $q$) and modular arithmetic. Factoring $n$ back into $p$ and $q$ is computationally infeasible for modern computers.

- **Diffie-Hellman Key Exchange:**
  A mathematical protocol allowing two parties who have never met to establish a shared secret key over an insecure network without transmitting the secret itself.

## 4. Digital Signatures & Passkeys (WebAuthn)

- **Digital Signatures:**

  Created by taking a document's hash and encrypting it with the sender's private key. Recipients verify the signature using the sender's public key, guaranteeing authenticity integrity, and non-repudiation.

- **Passkeys:**

  A passwordless authentication standard built on asymmetric cryptography. The user's device generates a site-specific public/private key pair unlocked by biometrics (fingerprint/Face ID) or a device PIN. The server stores only the public key, eliminating server-side password leaks and phishing risks.

## 5. Data Protection: Transit, End-to-End, & Rest

- **Encryption in Transit (HTTPS/TLS):**

  Encrypts data moving between a user and a server, protecting against machine-in-the-middle eavesdropping. However, the service provider (e.g., email server) can still read the unencrypted content.

- **End-to-End Encryption (E2EE):**

  Ensures data is encrypted on the sender's device and decrypted only on the recipient's device (e.g., iMessage, WhatsApp). Neither internet service providers nor middle servers can read the ciphertext.

- **Standard Deletion vs. Secure Deletion:**
  - Standard Deletion: Dragging a file to the Recycle Bin/Trash or emptying it merely deletes the file index reference, leaving the actual 0s and 1s intact on disk until overwritten.

  - Secure Deletion: Overwrites the disk blocks with zeros, ones, or random patterns

- **Encryption at Rest (Full-Disk Encryption):**

  Technologies like FileVault or BitLocker scramble the entire hard drive when the device is locked or powered off. If a device is stolen or resold, the data remains inaccessible

- **Ransomware:**

  Malicious actors abuse encryption by scrambling a victim's files and demanding payment for the decryption key.

## 6. Quantum Computing Threats

- Qubits:

  Unlike classical binary bits ($0$ or $1$), quantum bits can represent $0$ and $1$ simultaneously (superposition).

- Impact on Cryptography:

  Quantum algorithms will exponentially accelerate brute-forcing and could break asymmetric protocols like RSA, driving the need for post-quantum cryptography.
