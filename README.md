# 🔐 PixelCrypt — Image Encryption & Decryption

<p align="center">
  <img src="https://img.shields.io/badge/PixelCrypt-Image%20Encryption%20%26%20Decryption-06B6D4?style=for-the-badge" alt="PixelCrypt">
  <img src="https://img.shields.io/badge/Status-Production%20Ready-16A34A?style=for-the-badge" alt="Production Ready">
</p>

<p align="center">
  <strong>A modern client-side image encryption and decryption application built for secure processing, cryptography education, pixel visualization, and exact image restoration.</strong>
</p>

<p align="center">
  React · TypeScript · Vite · Web Crypto API · AES-256-GCM · PBKDF2 · HMAC-SHA256
</p>

<p align="center">

![Frontend](https://img.shields.io/badge/Frontend-React-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![Language](https://img.shields.io/badge/Language-TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Build](https://img.shields.io/badge/Build-Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Crypto](https://img.shields.io/badge/Cryptography-Web%20Crypto%20API-4285F4?style=for-the-badge)
![Tests](https://img.shields.io/badge/Tests-35%20Passing-16A34A?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-2563EB?style=for-the-badge)

</p>

<p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-features">Features</a> •
  <a href="#-encryption-modes">Encryption</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-security">Security</a> •
  <a href="#-testing">Testing</a>
</p>

---

# ✨ Overview

**PixelCrypt** is a client-side image encryption and decryption application designed to make image cryptography understandable while providing a standardized authenticated-encryption workflow.

The application combines an **Educational Pixel Mode** for visualizing pixel-level transformations with an **AES-256-GCM Secure Mode** for authenticated encryption using the browser's native Web Crypto API.

PixelCrypt processes image data locally in the browser. The core application does not require a backend, database, or image-upload service.

### 🔐 Core Capabilities

- 🖼️ Image encryption and decryption
- 🎓 Educational pixel-level encryption mode
- 🔒 AES-256-GCM secure encryption mode
- 🧮 Interactive Pixel Matrix visualization
- 📦 Dedicated `.pixelcrypt` encrypted container
- 🛡️ HMAC-SHA256 integrity protection
- 🔑 PBKDF2-HMAC-SHA256 key derivation
- 🚫 Wrong-key rejection
- 🧱 Tamper and corruption detection
- ♻️ Exact image restoration
- 💻 Client-side processing
- ♿ Keyboard and ARIA accessibility support
- 🧪 Automated testing and browser verification

---

# 🎯 Application Experience

```text
                         👤 USER
                            │
                            ▼
                ┌─────────────────────────┐
                │       PIXELCRYPT        │
                │                         │
                │  Encrypt • Decrypt      │
                │  Pixel Matrix           │
                │  How It Works           │
                └────────────┬────────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼
        ┌──────────┐   ┌───────────┐   ┌───────────┐
        │  ENCRYPT │   │  DECRYPT  │   │  LEARN    │
        └────┬─────┘   └─────┬─────┘   └─────┬─────┘
             │               │               │
             ▼               ▼               ▼
        IMAGE DATA      .PIXELCRYPT      PIXEL MATRIX
             │               │          & EXPLANATIONS
             └───────────────┼───────────────┘
                             │
                             ▼
                     RESTORED / ENCRYPTED
                           IMAGE DATA
