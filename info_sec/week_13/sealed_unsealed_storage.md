# 🔐🛡️ Sealed Storage & TPM Authorization Protocols

> _TPM sealing binds sensitive data to a trusted machine state, ensuring secrets can only be accessed when the platform integrity remains uncompromised._ 🌌

---

# 💠 Sealed & Unsealed Storage

## 🌌 Intuition — Why Seal Data?

Traditional encryption only protects data confidentiality.

However, attackers may still:

- 💀 Modify the operating system
- 🪤 Inject malware into boot components
- 🔧 Alter the execution environment

Sealed storage solves this by binding encrypted data to a **specific trusted platform state**.

> [!IMPORTANT]
> Sealed data can only be decrypted if the system integrity measurements match expected TPM values.

---

## 🧪 Formal Logic — What Is Sealing?

### 🔒 Sealing

Sealing encrypts data while associating it with TPM PCR values.

### 🔓 Unsealing

Unsealing decrypts data only if the current PCR measurements match the original trusted measurements.

---

# ⚙️ TPM Seal Operation

## 🔐 Sealing Formula

TPM_Seal(PCR1, PCR3, PCR17) -> (Ciphertext, MAC(PCR1, PCR3, PCR17))

### 🧠 Meaning

- 🔒 Data encrypted into ciphertext
- 📜 TPM records PCR integrity measurements
- 🛡️ MAC binds ciphertext to trusted platform state

---

# 🔓 TPM Unseal Operation

## 🔑 Unsealing Formula

Plaintext <- TPM_Unseal(Ciphertext, MAC(PCR1', PCR3', PCR17'))

### 🧠 Meaning

- 📏 TPM checks current PCR values
- 🔍 If PCR values match → decrypt allowed
- ❌ If PCR values differ → decryption denied

---

## 🛠️ Applied Example — Trusted Boot Data Protection

```text id="x9f3qw"
1. Secret encrypted using TPM_Seal
2. PCR values recorded
3. System later boots
4. TPM compares new PCR values
5. Data released only if integrity matches
```

**System Impact:** Malware-modified systems cannot access sealed secrets.

---

## 🏁 Recap — Core Takeaway

- 🔐 Sealing ties data to platform integrity.
- 📜 PCR values act as trusted measurements.
- 🛡️ Secrets remain inaccessible on compromised systems.

---

# 📡🔑 Authorization Session Protocols

## 🌌 Intuition — Why TPM Requires Authorization

TPM protects highly sensitive operations such as:

- 🔑 Key creation
- 🔓 Key loading
- ✍️ Signing
- 🛡️ Secure storage access

Unauthorized access must therefore be prevented using controlled authorization sessions.

---

## 🧪 TPM Authorization Models

| Protocol | Purpose                     |
| -------- | --------------------------- |
| 🆕 OSAP  | Create new TPM objects      |
| 🔓 OIAP  | Access existing TPM objects |

---

## 🔒 Authentication Requirement

When protected commands execute, TPM requires authentication factors such as:

- 🔑 Passwords
- 👤 User authorization
- 🛡️ Key ownership verification

---

## 🛠️ Common Authorization Commands

| Command              | Purpose              |
| -------------------- | -------------------- |
| 🔑 TPM_CreateWrapKey | Create protected key |
| 📦 TPM_LoadKey       | Load encrypted key   |

---

## 🏁 Recap

- 📡 TPM uses controlled authorization sessions.
- 🔐 Sensitive operations require authentication.
- 🛡️ Access control protects TPM secrets.

---

# 🆕🔐 OSAP — Object-Specific Authorization Protocol

## 🌌 Intuition — Creating Secure TPM Objects

OSAP is used when creating new protected TPM objects such as signing keys.

---

## 🧪 Formal Logic — OSAP Workflow

### 🔄 Process

```text id="z2kp7x"
User requests new signing key
        │
        ▼
TPM asks for SRK password
        │
        ▼
New signing key generated
        │
        ▼
Signing key encrypted using SRK
```

---

## 🛠️ Key Concept

| Component      | Role                       |
| -------------- | -------------------------- |
| 🛡️ SRK         | Protects newly created key |
| 🔑 Signing Key | Newly generated object     |
| 🔒 Ciphertext  | Encrypted protected key    |

---

## 🛠️ Applied Example — Secure Signing Key Creation

```text id="v6u8pr"
TPM_CreateWrapKey()
       │
       ▼
User authenticates SRK access
       │
       ▼
TPM encrypts signing key using SRK
```

**System Impact:** Newly created cryptographic keys remain protected immediately after creation.

---

## 🏁 Recap

- 🆕 OSAP creates new TPM-protected objects.
- 🔑 SRK secures newly generated keys.
- 🔒 Keys remain encrypted outside TPM.

---

# 🔓📦 OIAP — Object-Independent Authorization Protocol

## 🌌 Intuition — Accessing Existing Protected Keys

OIAP is used to access previously protected TPM objects.

---

## 🧪 Formal Logic — OIAP Workflow

### 🔄 Process

```text id="y4jw9s"
User submits encrypted signing key
        │
        ▼
TPM requests SRK password
        │
        ▼
TPM decrypts protected key
        │
        ▼
Key loaded for secure use
```

---

## 🛠️ Key Concepts

| Element        | Purpose             |
| -------------- | ------------------- |
| 🔒 Ciphertext  | Encrypted key blob  |
| 🛡️ SRK         | Root decryption key |
| 🔓 TPM_LoadKey | Loads usable key    |

---

## 🛠️ Applied Example — Secure Key Loading

```text id="u3b0mn"
TPM_LoadKey()
      │
      ▼
User authenticates SRK
      │
      ▼
TPM restores signing key internally
```

**System Impact:** Encrypted keys can be safely stored externally and restored securely.

---

## 🏁 Recap

- 🔓 OIAP accesses existing TPM objects.
- 📦 Encrypted keys remain protected during storage.
- 🛡️ TPM securely restores usable keys internally.

---

# 🌐🛡️ TRAP — TPM-based Remote Attestation Protocol

## 🌌 Intuition — Verifying Trusted Systems Remotely

Remote systems need a method to verify that:

- 🔒 The bootloader is trusted
- 💻 Applications remain untampered
- 🛡️ The platform integrity is valid

TRAP enables this through TPM measurements and attestation.

---

# 🧪 Phase 1 — Bootloader Integrity Measurement

## 🔄 Workflow

```text id="e8cw4m"
Bootloader checksum generated
        │
        ▼
Hash extended into PCR2
        │
        ▼
Session key sealed using PCR2
```

---

## 🔐 Bootloader Measurement Formula

h_b = TPM_Hash(M_b)

---

## 🔐 PCR Extension

VPCR2 = TPM_Extend(h_b, PCR2)

---

## 🔐 Key Sealing

ESEAL(K*{AB}) = TPM_SEAL(SEALKEY, K*{AB}, PCR2)

---

## 🛠️ Applied Example

```text id="5vr2xp"
Trusted bootloader measured
        │
        ▼
Measurement stored in PCR2
        │
        ▼
Session key sealed to trusted state
```

**System Impact:** Session keys become inaccessible if the bootloader changes unexpectedly.

---

## 🏁 Recap

- 📏 TPM measures bootloader integrity.
- 🔐 Session keys become bound to trusted PCR values.
- 🛡️ Modified bootloaders invalidate sealed secrets.

---

# 🧪 Phase 2 — Application Integrity Measurement

## 🔄 Workflow

```text id="g7mx2k"
Application checksum created
        │
        ▼
Combined with session key hash
        │
        ▼
Measurement extended into PCR1
```

---

## 🔐 Application Measurement Formula

h*p = TPM_Hash(M_p || K*{AB})

---

## 🔐 PCR Extension

VPCR1 = TPM_Extend(h_p, PCR1)

---

## 🛠️ Applied Example

```text id="4mzn9u"
Trusted application measured
        │
        ▼
Measurement combined with session key
        │
        ▼
PCR1 updated securely
```

**System Impact:** TPM binds application integrity directly to attestation state.

---

## 🏁 Recap

- 📏 TPM measures application integrity.
- 🔗 Measurements become cryptographically chained.
- 🛡️ PCR values reflect trusted execution state.

---

# 🌐✍️ TRAP Remote Attestation Exchange

## 🌌 Intuition — Challenge-Response Trust Verification

The verifier challenges the platform to prove:

- 🔐 Integrity
- 🪪 Authenticity
- 🛡️ Trusted execution state

---

## 🧪 Attestation Workflow

```text id="3ypt4f"
Verifier sends challenge
        │
        ▼
TPM unseals session key
        │
        ▼
Nonce decrypted and validated
        │
        ▼
TPM signs PCR values
        │
        ▼
Verifier checks signature
```

---

# 🔐 Challenge Encryption

EK\*{AB}(N_A)

---

# 🔓 TPM Unseal

K*{AB} = TPM_Unseal(ESEAL(K*{AB}), PCR2)

---

# ✍️ Signed Attestation

Signature = TPM_Sign(VPCR1 || N_B)

---

## 🛠️ Applied Example — Secure Remote Validation

```text id="c7nz0q"
Corporate server sends challenge nonce
        │
        ▼
Client TPM proves trusted platform state
        │
        ▼
Verifier accepts only valid attestation
```

**System Impact:** Remote systems can cryptographically verify platform trustworthiness before granting access.

---

## 🏁 Recap

- 🌐 Remote attestation validates trusted execution remotely.
- ✍️ TPM signs integrity measurements securely.
- 🛡️ Challenge-response prevents replay attacks.

---

# 🏁🌌 Final System Recap

## 💠 Core Security Philosophy

TPM sealed storage and attestation provide:

- 🔐 Integrity-bound encryption
- 📏 Trusted platform measurement
- 🔑 Secure authorization protocols
- 🌐 Remote integrity verification
- 🛡️ Hardware-backed trust enforcement

---

## 🚀 Ultra-Condensed Interview Revision

| Concept          | Key Idea                        |
| ---------------- | ------------------------------- |
| 🔐 Sealing       | Encrypt data tied to PCR values |
| 🔓 Unsealing     | Decrypt only in trusted state   |
| 📜 PCR           | Stores integrity measurements   |
| 🆕 OSAP          | Creates TPM-protected objects   |
| 📦 OIAP          | Loads existing protected keys   |
| 🛡️ SRK           | Root storage encryption key     |
| 🌐 TRAP          | TPM-based remote attestation    |
| ✍️ AIK Signature | Proves integrity authenticity   |

---

> _“Trusted systems do not merely protect secrets — they prove they deserve access to them.”_ 🌌
