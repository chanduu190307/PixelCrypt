# 🔐 PixelCrypt — Image Encryption & Decryption System

<p align="center">
  <strong>Secure, Client-Side Image Encryption & Decryption Through Pixel-Level Cryptographic Processing</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/Web%20Crypto%20API-Supported-4285F4" alt="Web Crypto API" />
  <img src="https://img.shields.io/badge/AES--256--GCM-Secure%20Mode-00A67E" alt="AES-256-GCM" />
  <img src="https://img.shields.io/badge/HMAC--SHA256-Integrity-8A2BE2" alt="HMAC-SHA256" />
  <img src="https://img.shields.io/badge/Tests-35%20Passing-success" alt="Tests" />
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="MIT License" />
</p>

<p align="center">
  A modern browser-based application for encrypting and decrypting images locally,
  combining educational pixel-level transformations with authenticated AES-256-GCM encryption.
</p>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Project Purpose](#-project-purpose)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [How PixelCrypt Works](#-how-pixelcrypt-works)
- [Encryption Modes](#-encryption-modes)
- [Educational Pixel Mode](#-educational-pixel-mode)
- [AES-256-GCM Secure Mode](#-aes-256-gcm-secure-mode)
- [How Encryption Works](#-how-encryption-works)
- [How Decryption Works](#-how-decryption-works)
- [Pixel Matrix Visualization](#-pixel-matrix-visualization)
- [Security Architecture](#-security-architecture)
- [Privacy Architecture](#-privacy-architecture)
- [Image Processing Pipeline](#-image-processing-pipeline)
- [Container Format](#-pixelcrypt-container-format)
- [Application Architecture](#-application-architecture)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Running the Application](#-running-the-application)
- [Testing](#-testing)
- [Security Verification](#-security-verification)
- [Input Validation](#-input-validation)
- [Accessibility](#-accessibility)
- [Performance](#-performance)
- [Error Handling](#-error-handling)
- [Educational Value](#-educational-value)
- [Security Considerations](#-security-considerations)
- [Limitations](#-limitations)
- [Future Improvements](#-future-improvements)
- [Development Workflow](#-development-workflow)
- [Repository Hygiene](#-repository-hygiene)
- [Contributing](#-contributing)
- [License](#-license)
- [Project Status](#-project-status)

---

# 🔎 Overview

**PixelCrypt** is a client-side image encryption and decryption application designed to demonstrate how cryptographic transformations can be applied to digital image data.

The application allows users to:

- Upload an image.
- Encrypt the image locally.
- Download the encrypted result.
- Decrypt previously encrypted images.
- Restore the original image exactly.
- Visualize pixel-level transformations.
- Learn how encryption and integrity protection work.
- Use AES-256-GCM for authenticated secure encryption.
- Understand the difference between educational cryptographic transformations and authenticated encryption.

PixelCrypt performs its processing directly inside the user's browser.

```text
User
  │
  ▼
Image Upload
  │
  ▼
Browser Memory
  │
  ├── Educational Pixel Mode
  │
  └── AES-256-GCM Secure Mode
  │
  ▼
Encrypted Container
  │
  ▼
Local Download
```

No application server is required for the core encryption and decryption workflow.

---

# 🎯 Project Purpose

PixelCrypt was designed around three main objectives:

### 1. Image Security

Provide a practical interface for encrypting image data using cryptographic transformations.

### 2. Cryptography Education

Make otherwise abstract concepts such as:

- Pixel permutation
- Modular arithmetic
- XOR
- Keystream generation
- Hash-based integrity
- Key derivation
- Authenticated encryption

visually understandable.

### 3. Privacy

Keep image processing inside the browser so that the user's image does not need to be uploaded to a backend server.

---

# ✨ Key Features

## 🖼️ Image Encryption

Encrypt supported images directly in the browser.

## 🔓 Image Decryption

Decrypt PixelCrypt containers and reconstruct the original image.

## 🔐 Two Encryption Modes

PixelCrypt provides two distinct modes:

- Educational Pixel Mode
- AES-256-GCM Secure Mode

## 🧮 Pixel Matrix

Visualize how individual pixels are transformed during the educational encryption process.

## 📚 How It Works

An interactive educational section explains the cryptographic pipeline.

## 🛡️ Integrity Protection

Encrypted data is authenticated to detect:

- Wrong passwords
- Modified encrypted files
- Corrupted containers
- Invalid payloads

## 🔒 Client-Side Processing

Images are processed locally inside the browser.

## ♻️ Exact Restoration

A valid encrypted image can be decrypted back to the original pixel data.

## ♿ Accessibility

The interface includes keyboard navigation, ARIA labels, accessible controls, and keyboard-operable visualization controls.

---

# 🧰 Tech Stack

## Frontend

| Technology | Purpose |
|---|---|
| React | User interface |
| TypeScript | Type-safe application development |
| Vite | Development server and production bundling |
| CSS / Tailwind-compatible utilities | Styling and responsive UI |
| HTML5 Canvas | Image decoding and pixel manipulation |

## Cryptography

| Technology | Purpose |
|---|---|
| Web Crypto API | Browser-native cryptographic operations |
| AES-256-GCM | Authenticated secure encryption |
| PBKDF2-HMAC-SHA256 | Password-based key derivation |
| HMAC-SHA256 | Educational Mode integrity protection |
| SHA-256 | Cryptographic hashing |
| `crypto.getRandomValues()` | Cryptographically secure randomness |
| ChaCha20 counter-mode construction | Deterministic educational stream generation |

## Development & Testing

| Tool | Purpose |
|---|---|
| Vitest | Automated testing |
| TypeScript Compiler | Type checking |
| Vite | Production build |
| npm | Dependency management |
| Git | Version control |
| GitHub | Source-code hosting |

---

# ⚙️ How PixelCrypt Works

PixelCrypt has two different cryptographic paths.

```text
                    ┌──────────────────────┐
                    │     Image Upload     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Decode Image Pixels  │
                    └──────────┬───────────┘
                               │
                               ▼
                     ┌─────────────────────┐
                     │ Select Encryption   │
                     │       Mode          │
                     └──────────┬──────────┘
                                │
                  ┌─────────────┴─────────────┐
                  │                           │
                  ▼                           ▼
        ┌──────────────────┐        ┌──────────────────┐
        │ Educational      │        │ AES-256-GCM      │
        │ Pixel Mode       │        │ Secure Mode      │
        └────────┬─────────┘        └────────┬─────────┘
                 │                           │
                 ▼                           ▼
        Pixel Transformation         Authenticated
        + Integrity Protection       Encryption
                 │                           │
                 └─────────────┬─────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ PixelCrypt Container │
                    └──────────┬───────────┘
                               │
                               ▼
                         Local Download
```

---

# 🔐 Encryption Modes

PixelCrypt intentionally provides two modes for different purposes.

| Feature | Educational Pixel Mode | AES-256-GCM Secure Mode |
|---|---|---|
| Main purpose | Cryptography education | Authenticated encryption |
| Pixel transformations | Yes | No direct visualization |
| Pixel permutation | Yes | No |
| Modular transformation | Yes | No |
| XOR / keystream | Yes | Internal cipher operation |
| HMAC integrity | Yes | No |
| AES-256-GCM | No | Yes |
| Password-based key derivation | Yes | Yes |
| Tamper detection | Yes | Yes |
| Pixel Matrix visualization | Yes | No |
| Recommended for real confidentiality | Educational only | Yes |

The educational mode exists primarily to demonstrate cryptographic concepts.

The AES-256-GCM mode provides a standard authenticated encryption construction using the browser's Web Crypto API.

---

# 🧮 Educational Pixel Mode

Educational Pixel Mode demonstrates how image pixels can be transformed through multiple cryptographic stages.

The conceptual pipeline is:

```text
Original Image
      │
      ▼
Extract RGBA Pixels
      │
      ▼
Pixel Permutation
      │
      ▼
Modular Transformation
      │
      ▼
XOR With Keystream
      │
      ▼
HMAC-SHA256 Integrity
      │
      ▼
Encrypted Pixel Data
```

---

# 🔀 Pixel Permutation

The first educational transformation changes the ordering of pixels.

A deterministic permutation is generated from cryptographic stream material.

The application uses a Fisher-Yates style shuffle.

Conceptually:

```text
Original:

P0 P1 P2 P3 P4 P5 P6 P7

Permutation:

P5 P2 P7 P0 P6 P1 P4 P3
```

The permutation changes where pixels appear without changing the underlying pixel values.

---

# ➕ Modular Transformation

After permutation, the pixel values undergo a modular transformation.

For each byte:

```text
Yᵢ = (Pᵢ + Sᵢ) mod 256
```

Where:

- `Pᵢ` = original pixel byte
- `Sᵢ` = generated transformation value
- `Yᵢ` = transformed byte

Because image channels are represented using byte values from `0` to `255`, arithmetic is performed modulo `256`.

Example:

```text
Pᵢ = 240
Sᵢ = 40

Yᵢ = (240 + 40) mod 256
Yᵢ = 24
```

---

# 🔢 XOR / Keystream Transformation

The transformed byte is then combined with a generated keystream.

```text
Cᵢ = Yᵢ XOR Kᵢ
```

Where:

- `Yᵢ` = transformed byte
- `Kᵢ` = keystream byte
- `Cᵢ` = encrypted byte

XOR is reversible:

```text
Cᵢ XOR Kᵢ = Yᵢ
```

Therefore, during decryption, the same keystream can be used to recover the transformed data.

---

# 🔄 Educational Decryption

Decryption reverses the transformations.

```text
Encrypted Data
      │
      ▼
Verify HMAC
      │
      ▼
XOR With Same Keystream
      │
      ▼
Reverse Modular Transformation
      │
      ▼
Reverse Pixel Permutation
      │
      ▼
Original Pixel Data
```

The operations are reversed in the opposite order from encryption.

---

# 🧠 Deterministic Stream Generation

Educational Mode requires reproducible cryptographic stream material.

PixelCrypt uses a deterministic ChaCha20 counter-mode construction for stream generation.

The generated stream is used for:

- Pixel permutation
- Modular transformation values
- XOR keystream generation

The permutation process uses rejection sampling so that Fisher-Yates selections are not biased by simple modulo reduction.

Conceptually:

```text
Password
   │
   ▼
Derived Key Material
   │
   ▼
ChaCha20 Counter-Mode Stream
   │
   ├──► Permutation Stream
   │
   ├──► Transformation Stream
   │
   └──► XOR Keystream
```

---

# 🔐 AES-256-GCM Secure Mode

AES-256-GCM provides authenticated encryption.

The browser's Web Crypto API performs the core AES-GCM operation.

The secure pipeline is:

```text
Password
   │
   ▼
PBKDF2-HMAC-SHA256
   │
   ▼
256-bit Encryption Key
   │
   ▼
AES-256-GCM
   │
   ├── Plain Image Data
   ├── Random IV
   └── Authentication
          │
          ▼
     Ciphertext + Tag
```

AES-GCM provides both:

1. Confidentiality
2. Integrity/authentication

A modified ciphertext or incorrect authentication data causes decryption to fail.

---

# 🔑 Password-Based Key Derivation

PixelCrypt does not directly use a user's password as an AES encryption key.

Instead, the password is processed through:

```text
PBKDF2-HMAC-SHA256
```

with:

```text
Iterations: 100,000
Salt: 16 bytes
Derived Key: 256 bits
```

Conceptually:

```text
User Password
      │
      ▼
Random Salt
      │
      ▼
PBKDF2-HMAC-SHA256
      │
      ▼
256-bit Encryption Key
```

The salt is stored with the encrypted container because it does not need to remain secret.

---

# 🎲 Cryptographic Randomness

PixelCrypt uses:

```text
crypto.getRandomValues()
```

for cryptographic randomness.

Random values are used for values such as:

- Encryption salts
- AES-GCM IVs
- Cryptographic stream material where required

The application does not use ordinary predictable random number generation for cryptographic secrets.

---

# 📦 PixelCrypt Container Format

Encrypted images are stored in a PixelCrypt container.

The container contains metadata required for decryption.

Conceptually:

```text
┌──────────────────────────────┐
│ Magic Identifier             │
├──────────────────────────────┤
│ Version                      │
├──────────────────────────────┤
│ Encryption Mode              │
├──────────────────────────────┤
│ Image Metadata               │
├──────────────────────────────┤
│ Salt / IV / Crypto Metadata  │
├──────────────────────────────┤
│ Integrity Information        │
├──────────────────────────────┤
│ Encrypted Payload            │
└──────────────────────────────┘
```

The container uses:

```text
Magic Identifier: PIXELCRYPT
Version: v1
Maximum Header Metadata: 64 KB
```

---

# 🛡️ Container Validation

Before decryption, PixelCrypt validates the container.

Validation includes checks for:

- Correct magic identifier
- Supported version
- Valid metadata
- Valid encryption mode
- Valid dimensions
- Valid payload boundaries
- Valid cryptographic metadata
- Integrity/authentication data

Malformed containers are rejected instead of being blindly processed.

---

# 🔒 Security Architecture

PixelCrypt uses multiple layers of protection.

```text
                  PixelCrypt Security
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
   Key Derivation    Encryption      Integrity
        │                │                │
        ▼                ▼                ▼
    PBKDF2          AES-256-GCM      HMAC-SHA256
        │                │                │
        └────────────────┼────────────────┘
                         │
                         ▼
                  Validation Layer
                         │
                         ▼
                  Secure Container
```

---

# 🔏 Integrity Protection

Educational Mode uses:

```text
HMAC-SHA256
```

to protect the encrypted payload against modification.

If encrypted data is modified:

```text
Stored HMAC
     ≠
Calculated HMAC
```

Decryption is rejected.

---

# ❌ Wrong-Key Detection

PixelCrypt does not simply attempt to interpret decrypted bytes as an image.

Authentication is performed before accepting the decrypted data.

Therefore, an incorrect password should cause authentication failure rather than producing silently corrupted output.

---

# 🧪 Tamper Detection

Encrypted containers are tested against modification.

For example:

```text
Original Encrypted Payload
          │
          ▼
       HMAC A

Modified Encrypted Payload
          │
          ▼
       HMAC B

HMAC A ≠ HMAC B
       │
       ▼
Decryption Rejected
```

---

# 🔐 Key Protection

Passwords and cryptographic keys are processed in application memory.

PixelCrypt does not intentionally transmit encryption keys to a backend server.

The application also avoids exposing cryptographic secrets in logs.

---

# 🕵️ Privacy Architecture

PixelCrypt is designed around local browser processing.

```text
                 USER DEVICE
┌─────────────────────────────────────────┐
│                                         │
│  Image                                  │
│    │                                    │
│    ▼                                    │
│  Browser Memory                         │
│    │                                    │
│    ├── Encryption                       │
│    ├── Decryption                       │
│    ├── Pixel Processing                 │
│    └── Integrity Verification           │
│                                         │
│    ▼                                    │
│  Local Download                         │
│                                         │
└─────────────────────────────────────────┘
                 │
                 X
          No upload required
```

The core encryption workflow does not require a remote image-processing backend.

---

# 🖼️ Image Processing Pipeline

The image processing pipeline is:

```text
Image File
    │
    ▼
Browser File API
    │
    ▼
Image Decoder
    │
    ▼
HTML Canvas
    │
    ▼
RGBA Pixel Buffer
    │
    ▼
Cryptographic Transformation
    │
    ▼
Encrypted Payload
    │
    ▼
PixelCrypt Container
    │
    ▼
Download
```

During decryption:

```text
PixelCrypt File
      │
      ▼
Container Parser
      │
      ▼
Validation
      │
      ▼
Authentication
      │
      ▼
Decryption
      │
      ▼
RGBA Pixel Buffer
      │
      ▼
Canvas
      │
      ▼
Restored Image
```

---

# 🔄 Exact Image Restoration

For a valid encrypted container and correct key, PixelCrypt is designed to restore the original pixel data exactly.

The conceptual property is:

```text
Decrypt(Encrypt(Image)) = Image
```

For byte-level verification:

```text
Original Byte Array
        =
Decrypted Byte Array
```

The test suite includes exact round-trip verification.

---

# 🧮 Pixel Matrix Visualization

The **Pixel Matrix** tab provides an educational visualization of the encryption pipeline.

The visualization demonstrates:

```text
Original
   ↓
Permutation
   ↓
Modular Shift
   ↓
XOR / Keystream
```

The matrix can be used to inspect small pixel regions.

Example:

```text
Original Matrix

[ 12  45  91  23 ]
[ 88  17  64  31 ]
[ 42  90  11  77 ]
[ 51  29  83  14 ]


        ↓


Permutation

[ 91  12  23  45 ]
[ 64  88  31  17 ]
[ 11  42  77  90 ]
[ 83  51  14  29 ]


        ↓


Modular Shift

[ ... ]
[ ... ]
[ ... ]
[ ... ]


        ↓


XOR / Keystream

[ ... ]
[ ... ]
[ ... ]
[ ... ]
```

The Pixel Matrix is intended as an educational visualization rather than a cryptanalysis or security-analysis dashboard.

---

# 📚 How It Works

The **How It Works** section explains the cryptographic concepts used by the application.

Topics include:

- Image pixels
- Pixel permutation
- Modular arithmetic
- XOR
- Keystreams
- Password-based key derivation
- HMAC
- AES-GCM
- Authentication
- Integrity
- Client-side processing

---

# 🏗️ Application Architecture

PixelCrypt follows a modular frontend architecture.

```text
React Application
│
├── Layout
│   ├── Navbar
│   └── Application Shell
│
├── Workspaces
│   ├── Encrypt Workspace
│   └── Decrypt Workspace
│
├── Visualizers
│   ├── Pixel Matrix
│   └── Image Comparison
│
├── Educational Components
│   └── How It Works
│
├── Common Components
│   ├── Dropzone
│   ├── Key Input
│   ├── Buttons
│   └── UI Utilities
│
└── Libraries
    ├── Cryptography
    ├── Image Processing
    └── Container Processing
```

---

# 🧩 Component Architecture

The React application is divided into functional areas.

### Layout

Responsible for:

- Application navigation
- Page structure
- Global layout

### Encryption Workspace

Responsible for:

- Image upload
- Mode selection
- Password input
- Encryption execution
- Download handling

### Decryption Workspace

Responsible for:

- Encrypted container upload
- Password input
- Authentication
- Decryption
- Image restoration

### Pixel Matrix

Responsible for:

- Pixel visualization
- Transformation stages
- Educational inspection

### How It Works

Responsible for:

- Cryptography explanations
- Encryption pipeline
- Educational content

---

# 🔐 Cryptography Architecture

The cryptographic implementation is separated from the UI.

```text
React UI
   │
   ▼
Crypto Service Layer
   │
   ├── Educational Crypto
   │
   ├── AES-GCM
   │
   ├── PBKDF2
   │
   ├── HMAC
   │
   └── Randomness
```

This separation allows the interface to remain independent from the underlying cryptographic operations.

---

# 📁 Project Structure

```text
PixelCrypt/
│
├── public/
│   └── favicon.svg
│
├── src/
│   │
│   ├── assets/
│   │
│   ├── components/
│   │   ├── common/
│   │   ├── educational/
│   │   ├── layout/
│   │   ├── visualizer/
│   │   └── workspace/
│   │
│   ├── lib/
│   │   ├── crypto/
│   │   │   ├── aesGcm.ts
│   │   │   └── ...
│   │   └── image/
│   │
│   ├── tests/
│   │   ├── crypto/
│   │   ├── image/
│   │   └── ...
│   │
│   ├── types/
│   │   └── crypto.ts
│   │
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
│
├── .gitignore
├── .oxlintrc.json
├── index.html
├── LICENSE
├── package.json
├── package-lock.json
├── PROJECT_AUDIT.md
├── FINAL_SECURITY_AUDIT.md
├── README.md
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.node.json
└── vite.config.ts
```

---

# 💻 Installation

## Prerequisites

Install:

- Node.js
- npm
- Git

Check the installed versions:

```bash
node --version
npm --version
git --version
```

---

# 📥 Clone the Repository

```bash
git clone https://github.com/chanduu190307/PixelCrypt.git
```

Navigate into the project:

```bash
cd PixelCrypt
```

---

# 📦 Install Dependencies

```bash
npm install
```

---

# ▶️ Running the Application

Start the development server:

```bash
npm run dev
```

Vite will provide a local development URL.

Open that URL in your browser.

---

# 🏭 Production Build

Create a production build:

```bash
npm run build
```

The generated production files are placed in:

```text
dist/
```

---

# 👀 Preview Production Build

After building:

```bash
npm run preview
```

---

# 🧪 Testing

PixelCrypt uses automated tests to verify important application behavior.

Run the test suite:

```bash
npm test
```

Current verification:

```text
35 / 35 tests passing
```

The tests cover areas including:

- Encryption/decryption behavior
- Container persistence
- Wrong-key rejection
- Tampered payload rejection
- Educational Mode boundaries
- Image round-trip behavior

---

# 🔬 Test Categories

## Encryption Tests

Verify that input images can be transformed into encrypted containers.

## Decryption Tests

Verify that valid encrypted containers can be restored.

## Integrity Tests

Verify that tampered encrypted payloads are rejected.

## Authentication Tests

Verify that incorrect passwords are rejected.

## Persistence Tests

Verify that encrypted containers can be exported and later imported.

## Educational Mode Tests

Verify expected input and transformation boundaries.

---

# 🌐 Browser Verification

The application has been verified through browser-based workflows covering:

- Encrypt tab
- Decrypt tab
- Pixel Matrix
- How It Works
- Image upload
- Encryption
- Decryption
- Wrong-password handling
- Pixel Matrix visualization
- Autoplay visualization
- Exact image restoration

The verification also checked for browser console errors and warnings.

---

# 🧬 Exact Round-Trip Verification

PixelCrypt was tested using generated image patterns.

Example workflow:

```text
Original Image
      │
      ▼
    Encrypt
      │
      ▼
Encrypted Container
      │
      ▼
    Decrypt
      │
      ▼
Restored Image
      │
      ▼
Byte Comparison
```

The byte-level comparison verifies:

```text
Original Pixels === Restored Pixels
```

The verification included:

- Small synthetic image patterns
- Larger generated image patterns
- Full pixel-buffer comparison

---

# 🛡️ Security Verification

The project was audited for several classes of issues.

## Secret Scanning

The repository was checked for:

- API keys
- Access tokens
- Passwords
- Private credentials
- Hard-coded secrets

No credentials or secrets were intentionally committed.

## Dependency Audit

```bash
npm audit
```

Current verification:

```text
0 vulnerabilities
```

## Linting

```bash
npm run lint
```

Current verification:

```text
0 errors
0 warnings
```

## Production Build

```bash
npm run build
```

The production TypeScript/Vite build completes successfully.

---

# 🔍 Input Validation

PixelCrypt validates uploaded image and encrypted-container data before processing.

Validation includes:

- File type
- File size
- Image dimensions
- Container structure
- Container version
- Encryption metadata
- Payload boundaries
- Authentication data

---

# 📏 Input Limits

The application uses defensive processing limits.

Current documented limits include:

```text
Maximum Upload Size: 25 MB
Maximum Image Dimension: 8192 × 8192
Maximum Container Header Metadata: 64 KB
```

These limits help reduce excessive memory usage and malformed-input risks.

---

# 🧹 Filename Sanitization

Downloaded filenames are sanitized to reduce risks from malicious filename content.

The application avoids unsafe path-like or script-like filename behavior.

---

# ♻️ Resource Management

Browser-created object URLs are cleaned up when they are no longer required.

The upload interface also handles repeated selection of the same file.

This helps reduce unnecessary browser resource retention.

---

# ♿ Accessibility

PixelCrypt includes accessibility improvements such as:

- Keyboard-operable controls
- ARIA labels
- Accessible file dropzones
- Keyboard navigation
- Accessible navigation state
- Keyboard-operable image comparison controls

The goal is to ensure that core application functionality is not dependent solely on mouse interaction.

---

# ⚡ Performance

PixelCrypt performs its image-processing operations locally in the browser.

Performance considerations include:

- Controlled input limits
- Efficient typed-array processing
- Browser-native cryptography
- Object URL cleanup
- Avoiding unnecessary resource retention
- Modular cryptographic functions

Large images can still require significant browser memory because image processing requires pixel buffers.

---

# ❌ Error Handling

PixelCrypt handles invalid operations such as:

- Unsupported files
- Oversized images
- Invalid containers
- Unsupported container versions
- Incorrect passwords
- Authentication failures
- Tampered encrypted data
- Corrupted payloads
- Invalid metadata

Errors are surfaced to the user instead of silently producing incorrect output.

---

# 🎓 Educational Value

PixelCrypt is designed not only as a utility but also as a learning platform.

It demonstrates concepts such as:

### Cryptography

- Encryption
- Decryption
- Key derivation
- Authentication
- Integrity
- Cryptographic randomness

### Computer Graphics

- Pixels
- RGBA channels
- Image buffers
- Canvas processing

### Algorithms

- Fisher-Yates permutation
- Rejection sampling
- Modular arithmetic
- XOR operations

### Web Development

- React
- TypeScript
- Web APIs
- File APIs
- Canvas APIs
- Web Crypto API

---

# ⚖️ Educational Mode vs Secure Mode

PixelCrypt intentionally separates educational transformations from standard authenticated encryption.

## Educational Mode

Designed to make cryptographic concepts visible.

It demonstrates:

```text
Permutation
     ↓
Modular Transformation
     ↓
XOR
     ↓
Integrity Protection
```

## Secure Mode

Uses:

```text
PBKDF2-HMAC-SHA256
          ↓
     AES-256-GCM
          ↓
Authenticated Ciphertext
```

For applications requiring standard authenticated encryption, the AES-256-GCM mode is the relevant implementation.

---

# 🔐 Security Philosophy

PixelCrypt follows several security principles:

### 1. Validate Before Processing

Untrusted input should be validated before expensive or sensitive operations.

### 2. Authenticate Encrypted Data

Encrypted data should not be trusted merely because it can be parsed.

### 3. Use Cryptographic Randomness

Security-sensitive random values should come from browser cryptographic APIs.

### 4. Minimize Data Exposure

Image processing is performed locally.

### 5. Fail Closed

Authentication failures and malformed containers should result in rejection rather than accepting potentially corrupted data.

### 6. Separate Education From Security Claims

Educational cryptographic transformations are presented as educational mechanisms and should not be confused with standardized authenticated encryption.

---

# 🧱 Threat Model

PixelCrypt considers threats such as:

```text
Threat
  │
  ├── Wrong Password
  │
  ├── Modified Ciphertext
  │
  ├── Corrupted Container
  │
  ├── Malformed Metadata
  │
  ├── Oversized Input
  │
  └── Malicious Filename
```

Defensive controls include:

```text
Threat
  │
  ▼
Validation
  │
  ▼
Authentication
  │
  ▼
Safe Processing
```

---

# ⚠️ Security Considerations

PixelCrypt is designed as a browser-based cryptography project.

It should not be described as:

```text
"unhackable"
"100% secure"
"impossible to break"
```

Security depends on multiple factors including:

- Password strength
- Browser security
- Device security
- Operating-system security
- User behavior
- Implementation correctness
- Cryptographic configuration

The application provides cryptographic protections, but no software should be considered absolutely immune to compromise.

---

# 🚧 Limitations

Current limitations include:

- Processing occurs in browser memory.
- Very large images can consume substantial RAM.
- Educational Mode is primarily intended for learning.
- Secure Mode relies on browser Web Crypto support.
- Losing the password can make encrypted data unrecoverable.
- Client-side applications remain dependent on the security of the user's device and browser.

---

# 🚀 Future Improvements

Potential future enhancements include:

- Additional image formats
- Batch image encryption
- Folder-based processing
- Drag-and-drop batch operations
- More detailed cryptographic visualizations
- Additional container versions
- Web Worker-based heavy processing
- Progressive image processing
- Improved mobile interface
- Additional automated browser tests
- More educational cryptography demonstrations
- Optional encrypted metadata
- Additional authenticated encryption algorithms

---

# 🧪 Project Audit

PixelCrypt underwent a final engineering and security audit.

The audit covered:

```text
Project Structure
        ↓
Dead Code
        ↓
Unused Assets
        ↓
Accessibility
        ↓
Cryptography
        ↓
Input Validation
        ↓
Error Handling
        ↓
Testing
        ↓
Linting
        ↓
Production Build
        ↓
Dependency Audit
        ↓
Secret Scanning
        ↓
Browser Verification
```

---

# 🧹 Repository Cleanup

Unused project artifacts were removed during the final cleanup.

Removed examples include:

```text
Unused Vite assets
Unused React assets
Unused SVG assets
Unused legacy favicon
Unused component interfaces
Unused state
Unused properties
```

The project was also checked for dead references and unnecessary files.

---

# 📦 Repository Hygiene

The repository excludes generated and local-only files such as:

```text
node_modules/
dist/
coverage/
.env
.env.*
logs/
temporary files
IDE-specific files
```

Sensitive configuration should never be committed.

---

# 🔄 Development Workflow

Recommended development workflow:

```text
1. Clone Repository
        ↓
2. Install Dependencies
        ↓
3. Start Development Server
        ↓
4. Implement Feature
        ↓
5. Run Tests
        ↓
6. Run Linter
        ↓
7. Run Production Build
        ↓
8. Review Security
        ↓
9. Review Git Changes
        ↓
10. Commit Changes
        ↓
11. Push to GitHub
```

Useful commands:

```bash
npm install
npm run dev
npm test
npm run lint
npm run build
npm audit
git status
```

---

# 📝 Development Principles

The project follows these principles:

- Type-safe development
- Modular architecture
- Client-side privacy
- Explicit validation
- Authenticated encryption
- Automated testing
- Clean repository structure
- Accessible user interface
- Minimal unnecessary dependencies
- Clear separation between educational and secure cryptographic functionality

---

# 🤝 Contributing

Contributions are welcome.

A typical contribution workflow is:

```text
Fork
  ↓
Create Feature Branch
  ↓
Implement Changes
  ↓
Run Tests
  ↓
Run Linter
  ↓
Run Production Build
  ↓
Create Pull Request
```

Before submitting changes, verify:

```bash
npm test
npm run lint
npm run build
npm audit
```

---

# 📄 License

This project is licensed under the MIT License.

See:

```text
LICENSE
```

for the complete license text.

---

# 📊 Project Status

| Area | Status |
|---|---|
| React Application | ✅ Complete |
| TypeScript | ✅ Complete |
| Image Encryption | ✅ Implemented |
| Image Decryption | ✅ Implemented |
| Educational Pixel Mode | ✅ Implemented |
| AES-256-GCM Mode | ✅ Implemented |
| PBKDF2 Key Derivation | ✅ Implemented |
| HMAC Integrity | ✅ Implemented |
| Pixel Matrix | ✅ Implemented |
| How It Works | ✅ Implemented |
| Input Validation | ✅ Implemented |
| Error Handling | ✅ Implemented |
| Accessibility | ✅ Implemented |
| Automated Tests | ✅ 35 Passing |
| Linting | ✅ 0 Errors / 0 Warnings |
| Production Build | ✅ Passing |
| Dependency Audit | ✅ 0 Vulnerabilities |
| Secret Scan | ✅ Clean |
| Browser Verification | ✅ Passed |
| Repository Cleanup | ✅ Completed |

---

# 🔗 Repository

GitHub:

https://github.com/chanduu190307/PixelCrypt

---

# ⚡ Quick Start

```bash
git clone https://github.com/chanduu190307/PixelCrypt.git

cd PixelCrypt

npm install

npm run dev
```

Then open the local Vite development URL in your browser.

---

# 🧭 Application Flow

The complete user flow is:

```text
                    ┌─────────────────┐
                    │    PixelCrypt    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   Upload Image  │
                    └────────┬────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Select Encryption    │
                  │       Mode           │
                  └──────────┬───────────┘
                             │
                 ┌───────────┴───────────┐
                 │                       │
                 ▼                       ▼
        ┌────────────────┐      ┌────────────────┐
        │ Educational    │      │ AES-256-GCM    │
        │ Pixel Mode     │      │ Secure Mode    │
        └───────┬────────┘      └───────┬────────┘
                │                       │
                └───────────┬───────────┘
                            │
                            ▼
                   ┌─────────────────┐
                   │ Encrypted File  │
                   └────────┬────────┘
                            │
                            ▼
                     Local Download
                            │
                            ▼
                   ┌─────────────────┐
                   │ Upload Again     │
                   └────────┬────────┘
                            │
                            ▼
                       Decryption
                            │
                            ▼
                   ┌─────────────────┐
                   │ Original Image  │
                   └─────────────────┘
```

---

# 🏁 Final Project Summary

**PixelCrypt** combines modern frontend engineering, image processing, browser-native cryptography, and cryptography education into a single client-side application.

The project demonstrates:

```text
React
  +
TypeScript
  +
Vite
  +
Canvas Image Processing
  +
Web Crypto API
  +
AES-256-GCM
  +
PBKDF2-HMAC-SHA256
  +
HMAC-SHA256
  +
Pixel-Level Transformations
  +
Automated Testing
  +
Security Validation
```

The result is a browser-based image encryption and decryption system that allows users to explore how cryptographic transformations work while providing an authenticated AES-256-GCM encryption mode for standard secure encryption use cases.

---

<p align="center">
  <strong>🔐 PixelCrypt — Encrypt. Visualize. Understand.</strong>
</p>

<p align="center">
  Built with React, TypeScript, Vite, Web Crypto API, and a focus on privacy, cryptography, and education.
</p>
