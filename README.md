# 🔐 VaultPKI - Advanced Cryptographic Toolkit

[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**VaultPKI** is a professional-grade, open-source PKI-based cryptographic tool with a modern GUI. Built for security researchers, developers, and organizations requiring robust certificate management and file security.

## ✨ Features

### 🏛️ Public Key Infrastructure
- **Certificate Authority (CA)**: Generate and manage your own local CA
- **User Enrollment**: Issue X.509 certificates signed by the CA
- **PKCS#12 Keystore**: Password-protected identity export (.p12 files)
- **Certificate Chain Validation**: MITM attack prevention

### 🔏 Digital Signatures
- **File Signing**: SHA-256 hashing with ECC signatures
- **Signature Verification**: Complete chain-of-trust validation
- **Metadata Tracking**: Timestamps, nonces, and signer information

### 🔐 Hybrid Encryption
- **AES-256-GCM**: Authenticated encryption for file confidentiality
- **ECDH Key Exchange**: Ephemeral key agreement for perfect forward secrecy
- **HKDF Key Derivation**: Cryptographically strong key wrapping

### 🛡️ Security Protections
- **Certificate Revocation List (CRL)**: Instant certificate invalidation
- **Replay Attack Prevention**: Nonce-based signature freshness
- **Certificate Validation**: Time-bound and chain-of-trust verification
- **Audit Logging**: Complete cryptographic operation history

### 🎨 Modern GUI
- Cyberpunk-themed dark interface
- Six functional pages: Dashboard, Identity, Sign/Verify, Encrypt/Decrypt, Attack Lab, Logs
- Real-time operation feedback
- Professional UX with smooth animations

## 📋 Requirements

- Python 3.11 or higher
- pip package manager

## 🚀 Installation

```bash
# Clone or download the project
cd vaultpki

# Install dependencies
pip install -r requirements.txt
```

## 🎮 Running the Application

```bash
# From the vaultpki directory
python src/app.py
```

## 📖 Quick Start Guide

### 1. Create Certificate Authority
1. Navigate to **Identity & Certificates**
2. Click **Create CA**
3. CA keypair and certificate generated (`ca_cert.pem`, `ca_key.pem`)

### 2. Enroll Users
1. Enter username (e.g., "Alice")
2. Click **Enroll User**
3. Export identity as PKCS#12 file with password

### 3. Sign Files
1. Go to **Sign / Verify**
2. Select file to sign
3. Load signer's PKCS#12 identity
4. Click **Sign File**
5. Signature saved as `.sig` file

### 4. Verify Signatures
1. Select signed file
2. Select signature file
3. Click **Verify Signature**
4. Results show validity, certificate status, and integrity

### 5. Encrypt Files
1. Go to **Encrypt / Decrypt**
2. Select file to encrypt
3. Load recipient's certificate
4. Click **Encrypt File**
5. Encrypted vault saved as `.vault` file

### 6. Decrypt Files
1. Select vault file
2. Load recipient's PKCS#12 identity
3. Click **Decrypt File**
4. Original file restored

## 🧪 Testing Security Features

### Test Certificate Revocation
1. Go to **Attack Lab**
2. Enter certificate serial number
3. Click **Revoke Certificate**
4. Verify that signatures/encryption with revoked cert fail

### Test Replay Attack Prevention
1. Sign a file
2. Click **Simulate Replay Attack**
3. System detects and rejects reused nonce

### Test MITM Prevention
1. Click **Test MITM Validation**
2. System validates certificate chain integrity

## 🏗️ Architecture

```
vaultpki/
├── requirements.txt          # Python dependencies
├── README.md                 # This file
└── src/
    ├── app.py                # Application entry point
    ├── main.py               # Main window setup
    ├── core/                 # Cryptographic backend
    │   ├── pki.py            # CA and certificate management
    │   ├── keystore.py       # PKCS#12 keystore operations
    │   ├── signing.py        # Digital signature logic
    │   ├── hybrid_crypto.py  # Hybrid encryption system
    │   ├── replay_guard.py   # Nonce database (SQLite)
    │   ├── crl.py            # Certificate Revocation List
    │   └── validation.py     # Certificate chain validation
    └── ui/                   # PySide6 GUI
        ├── main_window.py    # Main window and navigation
        └── pages/            # UI pages
            ├── dashboard.py
            ├── identity.py
            ├── sign_verify.py
            ├── encrypt_decrypt.py
            ├── attack_lab.py
            └── logs.py
```

## 🔒 Security Considerations

### Cryptographic Standards
- **ECC P-256**: NIST-approved elliptic curve
- **SHA-256**: Collision-resistant hashing
- **AES-256-GCM**: Authenticated encryption with associated data
- **ECDH**: Ephemeral Diffie-Hellman key exchange
- **HKDF**: HMAC-based key derivation function

### Threat Model
- **MITM Attacks**: Prevented via certificate chain validation
- **Replay Attacks**: Mitigated using nonce tracking
- **Key Compromise**: Limited via certificate revocation
- **Data Confidentiality**: Protected by AES-256-GCM
- **Data Integrity**: Ensured via digital signatures

### Limitations
- **CA Security**: CA private key stored locally (production CAs use HSMs)
- **Nonce Database**: SQLite-based (production systems use distributed databases)
- **CRL Distribution**: Local file (production uses OCSP or distributed CRL)

## 📊 Use Cases

### 1. Secure Document Distribution
Organizations can encrypt sensitive documents to specific recipients using their public key certificates, ensuring only authorized personnel can decrypt.

### 2. Software Supply Chain Security
Developers can sign software releases, allowing users to verify authenticity and integrity before installation.

### 3. Internal PKI Testing
Security teams can simulate PKI scenarios, test certificate validation logic, and practice incident response for compromised certificates.

## 🤝 Contributing

This is an educational and research tool. Feel free to:
- Report bugs or security issues
- Suggest features
- Submit pull requests
- Use in security training

## 📄 License

MIT License - See LICENSE file for details

## ⚠️ Disclaimer

VaultPKI is designed for educational purposes, security research, and private PKI deployments. For production enterprise PKI, consult security professionals and consider commercial solutions with HSM support, OCSP, and distributed infrastructure.

## 🙏 Acknowledgments

Built with:
- [cryptography](https://cryptography.io/) - Python cryptographic library
- [PySide6](https://wiki.qt.io/Qt_for_Python) - Qt for Python GUI framework

---

**Made with 🔥 by security enthusiasts, for security enthusiasts.**
