# PixelCrypt — Image Encryption & Decryption System

> **Tagline:** *"Transforming Pixels. Securing Images."*  
> **Architecture:** Pure Client-Side Image Cryptography & Reversible Pixel Manipulation  

---

## 1. Project Overview

**PixelCrypt** is a standalone, browser-based image encryption and decryption application demonstrating key-driven pixel manipulation and modern cryptography. Built with React 19, TypeScript, Tailwind CSS, and the Web Crypto API, the entire cryptographic pipeline operates **100% client-side** in browser memory—ensuring complete privacy with zero server communication and zero external telemetry.

The application strictly implements the core workflow:
```
Upload Image → Extract Pixels → Manipulate Pixels → Encrypt → Encrypted Preview & Export → Decrypt → Bit-Exact Restoration
```

---

## 2. Core Features & Workspaces

PixelCrypt provides four focused, accessible sections:

### 1. Encrypt Workspace
- **Image Upload & Validation**: Drag-and-drop or select PNG, JPEG, or WebP images with defensive validation limits ($\le 25\text{ MB}$, dimensions between $2 \times 2$ and $8192 \times 8192$).
- **Quick Test Patterns**: Pre-configured test rasters (Cyber Shield, Color Gradient, Checkerboard) for immediate evaluation without external files.
- **Key Management**: Custom passphrase input with real-time Shannon entropy calculation and strength estimation, plus one-click 256-bit cryptographic key generation (`crypto.getRandomValues`).
- **Cryptographic Modes**:
  - **Educational Pixel Mode (Primary)**: Visual pixel manipulation using key-derived Fisher-Yates permutation, modular arithmetic ($\pmod{256}$), keystream XOR diffusion, and HMAC-SHA256 integrity tags.
  - **Secure Mode (Secondary)**: Standardized authenticated AES-256-GCM encryption with PBKDF2 (100,000 rounds).
- **Encrypted Preview & Export**: Interactive split-slider comparison with zoom and keyboard navigation, and download of the canonical `.pixelcrypt` binary container or scrambled PNG.

### 2. Decrypt Workspace
- **Container & Image Loading**: Accepts canonical `.pixelcrypt` binary containers or standalone scrambled images.
- **Header Parsing**: Safely unpacks container metadata (mode, dimensions, payload size, integrity tag).
- **Key Verification**: Decrypts using the matching secret passphrase.
- **Exact Plaintext Restoration**: Inverts the mathematical pipeline to restore 100% bit-identical original pixel data.
- **Integrity Safeguards**: Wrong keys or corrupted payloads trigger an immediate, safe failure banner without rendering corrupted rasters.
- **Restored Export**: One-click download of the restored image as a lossless PNG.

### 3. Pixel Matrix Visualizer
- **Micro-Matrix Inspection**: Samples $4 \times 4$ or $8 \times 8$ pixel grids from the image and demonstrates the 4-phase transformation step-by-step:
  - **Phase 0 — Original Plaintext**: Raw RGBA pixel intensities before manipulation.
  - **Phase 1 — Deterministic Permutation**: Spatial pixel swapping via unbiased Fisher-Yates shuffle derived from the key.
  - **Phase 2 — Modular Arithmetic**: Mathematical shift in the finite ring $\mathbb{Z}_{256}$: $C' = (C + S_k) \pmod{256}$.
  - **Phase 3 — Keystream XOR Diffusion**: Reversible bitwise diffusion: $C'' = C' \oplus X_k$.
- **Interactive Scrubber & Auto Play**: Step backward, forward, pause, or auto-advance through phases.

### 4. How It Works
- **Technical Cryptography Guide**: Explains digital image representation, finite-ring operations, deterministic keystream derivation, and the operational differences between Educational Pixel Mode and Secure Mode.

---

## 3. Mathematical Operations & Reversibility

The core educational encryption workflow applies three reversible operations:

1. **Spatial Pixel Permutation**:
   Pixels are rearranged according to a deterministic Fisher-Yates shuffle seeded by a key-derived ChaCha20 DRBG stream:
   $$P_{\text{perm}} = \text{FisherYates}(P_{\text{orig}}, K_{\text{stream}})$$

2. **Modular Arithmetic ($\mathbb{Z}_{256}$)**:
   A key-derived modular offset is added to each color channel (0–255):
   $$C' = (C + S_k) \pmod{256}$$

3. **Keystream XOR Masking**:
   Each byte is bitwise XORed with pseudorandom keystream bytes:
   $$C'' = C' \oplus X_k$$

### Exact Decryption Inversion:
1. **Invert Keystream XOR**: $C' = C'' \oplus X_k$
2. **Invert Modular Shift**: $C = (C' - S_k + 256) \pmod{256}$
3. **Invert Permutation**: $P_{\text{orig}}[\text{perm}[i]] = P_{\text{perm}}[i]$
4. **Integrity Check**: $\text{HMAC-SHA256}(P_{\text{orig}}) \stackrel{?}{=} \text{HeaderTag}$

---

## 4. The Canonical `.pixelcrypt` Binary Container

PixelCrypt packages encrypted data into an authenticated binary container:

```
+-------------------+--------------------+-----------------------+--------------------------+-----------------------+
| Magic (10 Bytes)  | Version (2 Bytes)  | Header Length (4B)    | JSON Metadata (Variable) | Encrypted Payload     |
| "PIXELCRYPT"      | 0x0001             | UInt32 Big-Endian     | UTF-8 Header JSON        | Raw Ciphertext Bytes  |
+-------------------+--------------------+-----------------------+--------------------------+-----------------------+
```

Defensive parsing constraints:
- Enforces magic bytes `PIXELCRYPT` match.
- Maximum header length capped at 64KB (`headerLength <= 65536`) to prevent memory exhaustion.
- Declared dimensions verified within safe limits ($2 \le W, H \le 8192$).

---

## 5. Technology Stack

| Layer | Technology |
|---|---|
| **Framework** | React 19 + TypeScript (Strict Mode) + Vite |
| **Styling** | Tailwind CSS v4 + Lucide React Icons |
| **Image Processing** | HTML5 Canvas API, `ImageData`, `Uint8ClampedArray` |
| **Cryptographic Primitives** | Web Crypto API (`SubtleCrypto`), PBKDF2-SHA256, AES-256-GCM, HMAC-SHA256 |
| **Deterministic PRNG** | RFC 8439 ChaCha20 Counter-Mode DRBG with rejection sampling |
| **Test Framework** | Vitest (35 automated unit tests across 3 suites) |
| **Linter** | Oxlint (0 warnings, 0 errors) |

---

## 6. Project Structure

```
PixelCrypt/
├── public/
│   └── favicon.svg           # Brand cyan shield vector favicon
├── src/
│   ├── components/
│   │   ├── common/           # Dropzone, KeyInput, SampleImages
│   │   ├── comparison/       # ImageCompare (split slider, side-by-side, toggle)
│   │   ├── decrypt/          # DecryptWorkspace
│   │   ├── educational/      # HowItWorks guide
│   │   ├── encrypt/          # EncryptWorkspace
│   │   ├── layout/           # Navbar, Hero, Footer
│   │   └── visualizer/       # PixelMatrixView
│   ├── lib/
│   │   ├── crypto/           # ChaCha20 DRBG, educational crypto, AES-GCM, container
│   │   └── image/            # Canvas extract/render utils, validation
│   ├── tests/                # Vitest unit test suites (35 tests)
│   ├── types/                # TypeScript type declarations
│   ├── App.tsx               # Primary application state and routing
│   ├── index.css             # Tailwind base and theme definitions
│   └── main.tsx              # React DOM entry point
├── index.html                # HTML entry point
├── package.json              # Project scripts and dependencies
├── tsconfig.json             # TypeScript configuration
└── vite.config.ts            # Vite build configuration
```

---

## 7. Installation & Quick Start

### Prerequisites
- Node.js (v18+ recommended)
- npm (v9+)

### Installation
```bash
# Clone or navigate to the repository directory
cd c:/CodeAlpha/PixelCrypt

# Install dependencies
npm install
```

### Development Server
```bash
npm run dev
# Open http://localhost:5173/ in your browser
```

### Running Automated Tests
```bash
npm test
# Executes all 35 core unit and integration tests
```

### Production Build
```bash
npm run build
# Compiles TypeScript and builds optimized production bundle via Vite
```

### Code Linting
```bash
npm run lint
# Verifies codebase with Oxlint (0 warnings, 0 errors)
```

---

## 8. Security Safeguards & Privacy

1. **Zero External Telemetry**: 100% client-side Web Crypto execution. No network requests are made during any operation.
2. **Volatile Memory**: Keys and image rasters reside only in temporary memory. Object URLs are revoked after preview creation and component unmount.
3. **Integrity Validation**: HMAC-SHA256 (Educational Mode) and Galois authentication tags (Secure Mode) reject wrong keys and tampered files prior to canvas rendering.
4. **Boundary Checks**: Strict dimension validation ($2 \times 2$ to $8192 \times 8192$) and container size checks ($\le 25\text{ MB}$) guard against memory exhaustion.

---

## 9. Limitations & Advisory

> **Disclaimer:** PixelCrypt's Educational Pixel Mode is designed to demonstrate image encryption concepts through visual pixel manipulation. It is an educational construction and should not be used as a replacement for standardized cryptographic protocols. For standard confidentiality and integrity requirements, the application includes standardized AES-256-GCM authenticated encryption with PBKDF2 key stretching.
