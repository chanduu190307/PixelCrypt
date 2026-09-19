# PixelCrypt — Final Project & Quality Audit

**Project:** PixelCrypt — Image Encryption & Decryption System  
**Tagline:** *"Transforming Pixels. Securing Images."*  
**Workspace:** `c:\CodeAlpha\PixelCrypt`  
**Audit Scope:** Final Pre-Push Codebase & Cryptography Verification  
**Final Status:** PASS — READY FOR GITHUB PUSH  

---

## 1. Project Overview & Architecture

PixelCrypt is a focused, client-side educational **image encryption and decryption application** demonstrating key-driven pixel manipulation and modern cryptography.

The application implements the complete processing flow:
```
Upload Image → Extract Pixels → Manipulate Pixels → Encrypt → View/Download Encrypted Image → Decrypt → Bit-Exact Restoration
```

### Primary Sections:
1. **Encrypt**: Upload image, select Educational Pixel Mode (or Secure Mode), configure key, execute encryption, preview encrypted image with split slider, download `.pixelcrypt` container or scrambled PNG.
2. **Decrypt**: Upload `.pixelcrypt` container or encrypted image, enter key, execute decryption, verify cryptographic integrity tag, restore bit-identical original image, download restored PNG.
3. **Pixel Matrix**: Interactive step-by-step 4-phase micro-matrix visualizer demonstrating pixel transformations ($P_{\text{orig}} \to \text{Permutation} \to \text{Modular Shift} \to \text{Keystream XOR}$).
4. **How It Works**: Technical guide detailing digital image representations, mathematical formulas, and mode comparisons.

---

## 2. Features Retained & Verified

- **Image Upload & Validation**: Drag-and-drop, dimension checks ($2 \times 2$ to $8192 \times 8192$), file-size limits ($\le 25\text{ MB}$), format validation (PNG, JPEG, WebP).
- **Pixel Extraction**: HTML5 Canvas `ImageData` RGBA pixel buffer extraction.
- **Pixel Manipulation**:
  - Deterministic Fisher-Yates spatial pixel permutation derived from key via RFC 8439 ChaCha20 DRBG.
  - Reversible finite-field modular arithmetic in $\mathbb{Z}_{256}$: $C' = (C + S_k) \pmod{256}$.
  - Keystream bitwise XOR diffusion: $C'' = C' \oplus X_k$.
- **Encryption & Decryption**: Educational Pixel Mode (primary focus) and authenticated AES-256-GCM (secondary standard).
- **Exact Plaintext Restoration**: 100% bit-level identical recovery of original pixels upon decryption.
- **Integrity Verification**: HMAC-SHA256 integrity tag check ensuring wrong keys or corrupted files are caught and rejected safely.
- **Binary Container Format**: Canonical `.pixelcrypt` container with magic bytes, versioning, and defensive bounds checks.

---

## 3. Cryptographic Verification

1. **Bit-Exact Plaintext Restoration**: Verified that both Educational Pixel Mode and Secure AES-256-GCM Mode achieve 100% exact byte-for-byte equality between original and restored pixel rasters across non-square images, solid images, and mixed-alpha images.
2. **Wrong-Key Rejection**: Verified that entering an incorrect key fails decryption immediately:
   - Educational Mode: HMAC-SHA256 integrity tag mismatch strictly rejects candidate plaintext.
   - Secure Mode: Web Crypto API detects Galois authentication tag failure and throws `OperationError`.
3. **Corrupted File Protection**: Modified ciphertexts are caught and rejected by the integrity check before any canvas allocation occurs.
4. **IV & Salt Freshness**: Every encryption invocation in both modes utilizes `crypto.getRandomValues()` to generate a fresh 16-byte salt and 96-bit random IV.
5. **Alpha Channel Preservation**: RGBA alpha channels remain intact throughout all transformations, preventing canvas premultiplication distortion.

---

## 4. Defensive Security Mechanisms

- **Input Validation**: `validateFile` rejects empty files, unsupported extensions, and oversized files ($> 25\text{ MB}$).
- **Filename Sanitization**: `sanitizeFilename` neutralizes directory traversal sequences and script tags.
- **Dimension Guards**: `validateDimensions` enforces minimum $2 \times 2$, maximum $8192 \times 8192$, and integer constraints.
- **Container Header Bounds**: Enforces maximum header metadata limit of 64KB (`headerLength <= 65536`) to prevent memory exhaustion.
- **Safe Base64 Decoding**: `base64ToBytes` safely handles malformed or truncated Base64 strings without unhandled DOMExceptions.
- **Key Derivation Precondition Checks**: Strict assertions reject empty or whitespace-only keys.
- **Memory Hygiene**: Canvas contexts discard offscreen elements promptly; Object URLs are revoked via `URL.revokeObjectURL`.
- **Zero Server Footprint**: 100% client-side execution; zero network requests.

---

## 5. Automated Test Suite Results

The automated test suite covers the core application functionality:

| Test File | Status | Tests Passed | Focus Area |
|---|---|---|---|
| `src/tests/crypto.test.ts` | **PASS** | 21 / 21 | Core crypto, reversibility, ChaCha20 DRBG, modular math, wrong key, persistence round-trip, boundary checks |
| `src/tests/container.test.ts` | **PASS** | 8 / 8 | `.pixelcrypt` container packing, unpacking, magic bytes, versioning, header limits |
| `src/tests/validation.test.ts` | **PASS** | 6 / 6 | File size limits, dimension limits, format validation, filename sanitization |
| **Total Core Tests** | **PASS** | **35 / 35** | **100% Verification** |

---

## 6. Code Quality & Build Verification

- **Linting (`oxlint`)**: 0 warnings, 0 errors across 25 files with 116 rules.
- **TypeScript Compilation (`tsc -b`)**: 0 type errors.
- **Production Build (`vite build`)**: Clean compilation; production bundle generated successfully.
- **Security Vulnerability Audit (`npm audit`)**: 0 vulnerabilities.
- **Browser Functional Verification**: End-to-end testing confirmed:
  - Clean 4-tab navigation (`Encrypt`, `Decrypt`, `Pixel Matrix`, `How It Works`).
  - Successful image upload, key configuration, and encryption.
  - Encrypted image preview with interactive comparison slider and download options.
  - Transition to Decrypt tab with container metadata.
  - Successful decryption and exact bit-level image restoration.
  - Safe failure handling and rejection banner on wrong keys.
  - Interactive 4-phase micro-matrix visualizer.
  - Educational cryptography guide in How It Works.
  - Zero console errors.

---

## 7. Final Recommendation & Readiness

PixelCrypt is robust, fully verified, free of extraneous dependencies or starter files, and ready for GitHub push.
