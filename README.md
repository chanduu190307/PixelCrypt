# 🔐 PixelCrypt — Image Encryption & Decryption

<p align="center">
  <strong>Client-Side Image Encryption, Decryption & Pixel-Level Visualization</strong>
</p>

<p align="center">
  A privacy-focused browser application that demonstrates how digital images can be transformed, encrypted, authenticated, and restored entirely on the client.
</p>

<p align="center">

![PixelCrypt](https://img.shields.io/badge/PixelCrypt-Image%20Security-00d9ff?style=for-the-badge)

![Status](https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge)

</p>

<p align="center">

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7.x-646CFF?style=flat-square&logo=vite&logoColor=white)
![Web Crypto API](https://img.shields.io/badge/Web%20Crypto%20API-Native-4285F4?style=flat-square)
![AES-256-GCM](https://img.shields.io/badge/AES--256--GCM-Secure-00C853?style=flat-square)
![PBKDF2](https://img.shields.io/badge/PBKDF2-HMAC--SHA256-orange?style=flat-square)
![HMAC-SHA256](https://img.shields.io/badge/HMAC-SHA256-Integrity-red?style=flat-square)
![Tests](https://img.shields.io/badge/Tests-35%20Passing-success?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)

</p>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Application Experience](#-application-experience)
- [Core Features](#-core-features)
- [Educational Pixel Mode](#-educational-pixel-mode)
- [AES-256-GCM Secure Mode](#-aes-256-gcm-secure-mode)
- [PixelCrypt Container Format](#-pixelcrypt-container-format)
- [Security Architecture](#-security-architecture)
- [Privacy Architecture](#-privacy-architecture)
- [Image Restoration](#-image-restoration)
- [Application Data Flow](#-application-data-flow)
- [Architecture](#-architecture)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Running the Application](#-running-the-application)
- [Testing](#-testing)
- [Quality Verification](#-quality-verification)
- [Error Handling](#-error-handling)
- [Security Considerations](#-security-considerations)
- [Performance & Resource Management](#-performance--resource-management)
- [Accessibility](#-accessibility)
- [Project Highlights](#-project-highlights)
- [Development Workflow](#-development-workflow)
- [Repository Hygiene](#-repository-hygiene)
- [Limitations](#-limitations)
- [Production Considerations](#-production-considerations)
- [Contributing](#-contributing)
- [License](#-license)
- [Project Status](#-project-status)

---

# 🔎 Overview

**PixelCrypt** is a modern client-side web application for exploring image encryption and decryption through direct manipulation of image pixel data.

The project combines:

- Educational pixel-level encryption
- Authenticated image containers
- AES-256-GCM secure encryption
- Pixel transformation visualization
- Password-based key derivation
- Integrity verification
- Exact image restoration
- Browser-native cryptographic APIs
- Client-side privacy
- Automated testing
- Production build verification

PixelCrypt is designed to make image encryption understandable while maintaining strong engineering and security practices.

The core encryption and decryption workflows operate entirely inside the user's browser.

---

# ✨ Application Experience

PixelCrypt provides four primary application areas.

### 🔐 Encrypt

Upload an image, provide an encryption key, select an encryption mode, and generate an encrypted PixelCrypt container.

### 🔓 Decrypt

Load a valid PixelCrypt container, provide the correct key, verify its integrity, and restore the original image.

### 🧩 Pixel Matrix

Visualize how individual image pixels change through the educational encryption pipeline.

### 📖 How It Works

Understand the cryptographic and pixel-processing concepts used by PixelCrypt.

---

# 🚀 Core Features

## 🔐 Image Encryption

PixelCrypt supports image encryption directly inside the browser.

```text
Image
   ↓
Validation
   ↓
Pixel Extraction
   ↓
Key Derivation
   ↓
Permutation / Transformation
   ↓
Encryption
   ↓
Integrity Protection
   ↓
PIXELCRYPT Container
