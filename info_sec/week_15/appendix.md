# 🔐 Identity & Access Management (IAM) in Cloud Computing 💠☁️

> [!IMPORTANT]
> In traditional networks, the perimeter was the firewall.
>
> In cloud computing, **Identity becomes the new perimeter**.

IAM ensures that the **right entity** gets the **right access** to the **right resource** at the **right time**.

---

# 🎯 IAM: The New Security Perimeter 💠🔒

## 💠 Intuition (Why IAM Exists)

Cloud resources are accessible from anywhere through the Internet.

Since traditional network boundaries are disappearing, organizations must rely on identity-based security.

```text
Traditional Security

User
 │
 ▼
Firewall
 │
 ▼
Internal Resources


Cloud Security

User
 │
 ▼
Identity Verification
 │
 ▼
Cloud Resources
```

### System Impact

Identity becomes the primary control point for protecting cloud environments.

---

## 🧪 Core IAM Components

### 🆔 Identity

An identity represents a unique entity.

Examples:

- 👤 User
- 💻 Device
- 🤖 Application
- ⚙️ System Service

---

### 🔑 Authentication

Verifies that an entity is who it claims to be.

Examples:

- Password
- MFA
- Biometrics

---

### 🚪 Authorization

Determines what an authenticated entity is allowed to do.

Examples:

- Read data
- Modify resources
- Delete systems

---

## 🏁 Recap

> [!NOTE]
> IAM = Identity + Authentication + Authorization

---

# 🔑 Authentication Factors 💠🛡️

## 💠 Intuition (Why Authentication Exists)

Before granting access, a system must verify a user's claimed identity.

---

## 🧪 The Three Authentication Factors

| Factor                | Description      | Examples                   |
| --------------------- | ---------------- | -------------------------- |
| 🧠 Something You Know | Knowledge-based  | Password, PIN              |
| 🔐 Something You Have | Possession-based | Smart Card, Security Token |
| 👤 Something You Are  | Inherence-based  | Fingerprint, Face ID       |

---

### Authentication Pyramid

```text
Something You Know
      │
      ▼
Something You Have
      │
      ▼
Something You Are
```

Combining factors increases security.

---

### System Impact

Multiple verification methods significantly reduce unauthorized access.

---

## 🏁 Recap

Strong authentication relies on combining independent factors.

---

# 🔒 Multi-Factor Authentication (MFA) 💠⚡

## 💠 Intuition (Why MFA Matters)

Passwords can be stolen, guessed, or reused.

MFA adds additional verification layers.

---

## 🧪 Authentication Comparison

| Method             | Factors Used      | Security Level |
| ------------------ | ----------------- | -------------- |
| 🔑 Password Only   | Know              | Low            |
| 🔑 + 📱 Token      | Know + Have       | High           |
| 📱 + 👤 Biometrics | Have + Are        | High           |
| 🔑 + 📱 + 👤       | Know + Have + Are | Very High      |

---

### MFA Workflow

```text
Username + Password
          │
          ▼
OTP / Authenticator App
          │
          ▼
Access Granted
```

---

### System Impact

MFA dramatically reduces account takeover and credential theft risks.

---

## 🏁 Recap

> [!IMPORTANT]
> Passwords alone are no longer sufficient for protecting cloud accounts.

---

# 🚪 Access Control Models 💠⚙️

## 💠 Intuition (Why Access Control Exists)

Not every user should have the same permissions.

Access control determines who can do what.

---

# 👥 Role-Based Access Control (RBAC)

## 🧪 How It Works

Permissions are assigned to roles rather than individual users.

---

### Example

| Role             | Permissions         |
| ---------------- | ------------------- |
| 👨‍💻 Developer     | Deploy Applications |
| 🔧 Administrator | Full System Access  |
| 👀 Visitor       | Read-Only Access    |

---

### RBAC Workflow

```text
User
 │
 ▼
Assigned Role
 │
 ▼
Granted Permissions
```

### System Impact

Simplifies permission management at scale.

---

# 🏷️ Attribute-Based Access Control (ABAC)

## 🧪 How It Works

Access decisions are based on attributes.

Examples:

- 🕒 Time
- 🌍 Location
- 💻 Device Type
- 🔒 Security Status

---

### Example Rule

```text
Allow Access If:
Location = Office
AND
Time = Business Hours
```

### System Impact

Provides highly dynamic and context-aware security.

---

# 📜 Policy-Based Access Control (PBAC)

## 🧪 How It Works

Machine-readable policies define access decisions.

---

### Example

```json
{
  "allow": true,
  "role": "developer",
  "resource": "repository"
}
```

### System Impact

Enables automated and scalable governance.

---

## ⚡ Modern Trend

```text
PBAC
  +
ABAC
  =
Dynamic Cloud Security
```

Organizations increasingly combine both models.

---

## 🏁 Recap

| Model   | Decision Based On |
| ------- | ----------------- |
| 👥 RBAC | Role              |
| 🏷️ ABAC | Attributes        |
| 📜 PBAC | Policies          |

---

# ☁️ IAM Challenges in Cloud Computing 💠🔒

## 💠 Intuition (Why IAM Is More Difficult in Cloud)

Cloud environments introduce unique security challenges.

---

## 🧪 Key Challenges

### 🌐 Internet-Exposed Management Interfaces

Cloud consoles and APIs are accessible globally.

Potential targets:

- 🎯 Administrators
- 🔑 Privileged accounts
- ⚙️ Automation systems

---

### 🤝 Shared Responsibility

```text
Cloud Provider
      +
Customer
      =
Secure IAM
```

Both parties contribute to identity security.

---

### 🏢 Different CSP Implementations

Each cloud provider uses different:

- Terminology
- Policies
- IAM architectures

This increases operational complexity.

---

### System Impact

Poor IAM governance can lead to large-scale cloud compromises.

---

## 🏁 Recap

> [!IMPORTANT]
> Effective IAM requires governance, processes, and technology working together.

---

# 🌐 Federated Identity Management 💠🔗

## 💠 Intuition (Why Federation Exists)

Users should not need separate credentials for every service.

Federation enables a single identity to access multiple systems.

---

## 🧪 Definition

Federated Identity Management allows users to authenticate once and access multiple services.

---

### Example

```text
Google Account
      │
      ▼
YouTube
Gmail
Drive
Docs
```

This is commonly called:

### 🔑 Single Sign-On (SSO)

---

### System Impact

Improves user experience while reducing password sprawl.

---

## 🏁 Recap

Federation centralizes identity management across multiple services.

---

# 🔄 Federation Protocols 💠📡

## OAuth 2.0

### Purpose

Authorization delegation.

Allows third-party applications to access resources without sharing passwords.

---

### Example

```text
App
 │
 ▼
Request Access
 │
 ▼
Google Grants Token
 │
 ▼
App Uses Token
```

### System Impact

Reduces password exposure.

---

# 🏷️ SAML (Security Assertion Markup Language)

## Purpose

Authentication and authorization between organizations.

Uses XML-based assertions.

---

### Common Use Case

```text
University Login
       │
       ▼
Learning Platform Access
```

### System Impact

Supports enterprise Single Sign-On.

---

# 🆔 OpenID Connect (OIDC)

## Purpose

Adds identity verification to OAuth 2.0.

---

### Example

```text
OAuth
   +
Identity Layer
   =
OIDC
```

### System Impact

Provides modern web authentication capabilities.

---

## 🏁 Recap

| Protocol     | Purpose                   |
| ------------ | ------------------------- |
| 🔑 OAuth 2.0 | Authorization             |
| 🏷️ SAML      | Enterprise Authentication |
| 🆔 OIDC      | Identity Authentication   |

---

# 🎟️ JSON Web Tokens (JWT) 💠⚡

## 💠 Intuition (Why JWT Exists)

Applications need a secure way to exchange identity and authorization information.

---

## 🧪 JWT Structure

```text
Header.Payload.Signature
```

---

### Components

| Component    | Purpose                     |
| ------------ | --------------------------- |
| 📋 Header    | Token metadata              |
| 📄 Payload   | User claims and permissions |
| ✍️ Signature | Integrity verification      |

---

### Architecture

```text
Header
   │
Payload
   │
Signature
```

All sections are Base64 encoded.

---

### System Impact

JWT enables stateless and scalable authentication systems.

---

## 🏁 Recap

> [!IMPORTANT]
> JWTs carry signed identity information that applications can trust.

---

# 🏢 Managing Identities in the Cloud 💠🔄

## Hub & Spoke Model

### 💠 Intuition

A central identity provider manages authentication.

---

### Architecture

```text
          Identity Provider
                  │
      ┌───────────┼───────────┐
      ▼           ▼           ▼
 Service A   Service B   Service C
```

### Benefits

- 🔒 Centralized control
- 📈 Easier scaling
- 🛠️ Simplified administration

---

# 🕸️ Free Form Model

### Architecture

```text
Identity Provider A ─ Service A

Identity Provider B ─ Service B

Identity Provider C ─ Service C
```

### Challenges

- ⚠️ Complex trust relationships
- 🔄 Difficult administration
- 📉 Reduced consistency

---

### System Impact

Centralized identity architectures simplify governance and auditing.

---

## 🏁 Recap

Hub-and-Spoke architectures are generally easier to manage than Free-Form trust models.

---

# 🔐 Strong Authentication Methods 💠🛡️

## Hard Tokens

### Description

Physical cryptographic devices.

Examples:

- 🔑 Security Keys
- 🔐 Hardware Tokens

### Security Level

⭐⭐⭐⭐⭐

---

## Soft Tokens

### Description

Authenticator applications generating One-Time Passwords (OTP).

Examples:

- 📱 Google Authenticator
- 📱 Microsoft Authenticator

### Security Level

⭐⭐⭐⭐

---

## SMS Authentication

### Description

Verification codes delivered through text messages.

### Risks

- 📡 Message interception
- 📱 SIM swapping attacks

### Security Level

⭐⭐

---

## Biometrics

### Description

Identity verification through physical characteristics.

Examples:

- 👤 Face Recognition
- 👆 Fingerprints
- 👁️ Iris Scans

### Security Level

⭐⭐⭐⭐

---

## Passwordless Authentication

### Example

🔑 FIDO Standard

Uses:

- Hardware keys
- Biometrics
- Cryptographic authentication

---

### System Impact

Passwordless systems significantly reduce phishing attacks.

---

## 🏁 Recap

| Method        | Security  |
| ------------- | --------- |
| 🔑 Hard Token | Highest   |
| 📱 Soft Token | High      |
| 👤 Biometrics | High      |
| SMS           | Moderate  |
| FIDO          | Very High |

---

# 👑 Privileged Identity & Access Management (PIM/PAM) 💠🔒

## 💠 Intuition (Why PIM/PAM Exists)

Administrator accounts represent the highest-value targets in cloud environments.

---

# 👑 PIM (Privileged Identity Management)

## Purpose

Manages privileged identities.

Examples:

- Cloud Administrators
- Security Engineers
- Database Administrators

---

# 🔑 PAM (Privileged Access Management)

## Purpose

Controls privileged access sessions.

Determines:

- Who gets access
- When access is granted
- What actions are allowed

---

## 🛠️ Key Features

### 🔄 Credential Rotation

Automatically changes privileged credentials.

---

### 🔐 MFA Enforcement

Additional verification for privileged accounts.

---

### 📊 Auditing & Reporting

Records all privileged activities.

---

### System Impact

PIM/PAM minimizes insider threats and administrative account compromise.

---

## 🏁 Recap

> [!IMPORTANT]
> Protect privileged accounts more aggressively than standard user accounts.

---

# ⚠️ Privilege Escalation 💠🚨

## 💠 Intuition (Why It Matters)

Attackers often attempt to gain greater permissions after initial access.

---

# ⬆️ Vertical Privilege Escalation

## Definition

A lower-privileged user gains higher-level permissions.

---

### Example

```text
Standard User
      │
      ▼
Administrator
```

### Risk

Full system compromise.

---

# ↔️ Horizontal Privilege Escalation

## Definition

A user accesses resources belonging to another user with the same privilege level.

---

### Example

```text
User A
   │
   ▼
User B's Data
```

### Risk

Unauthorized data exposure.

---

## ⚖️ Comparison

| Type          | Goal                   |
| ------------- | ---------------------- |
| ⬆️ Vertical   | Gain higher privileges |
| ↔️ Horizontal | Access peer resources  |

---

### System Impact

Privilege escalation is a common objective during cloud attacks and must be mitigated through least privilege and continuous monitoring.

---

# 🏁 Final Cyber-Scholar Recap 🌌⚡

> [!IMPORTANT]
> IAM is the foundation of cloud security because identity has replaced the traditional network perimeter.

### Core IAM Components

```text
Identity
    │
Authentication
    │
Authorization
```

### Key Technologies

- 🔑 MFA
- 🌐 Federation
- 🎟️ JWT
- 🆔 OIDC
- 🏷️ SAML
- 🔒 OAuth 2.0

### Security Priorities

- 👤 Strong Authentication
- 🔐 Least Privilege
- 👑 PIM/PAM
- 📜 Access Control Policies
- 🚨 Privilege Escalation Prevention

### Interview Memory Hook

```text
Cloud Security
      =
Identity
      +
Authentication
      +
Authorization
      +
Governance
```

**Remember:** In cloud computing, whoever controls identity often controls the environment. Protect identities as carefully as the infrastructure itself.
