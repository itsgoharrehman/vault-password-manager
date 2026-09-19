# vault-password-manager

Enterprise-grade, zero-knowledge client-side password vault. Cryptographic operations are performed locally within the browser runtime using the W3C WebCrypto API with AES-256-GCM encryption and PBKDF2 key derivation. Unencrypted master passwords and credentials never touch external networks or storage layers.

## Architecture and Stack

* **Cryptographic Engine**: WebCrypto API (AES-256-GCM authenticated encryption, PBKDF2 with 100,000 iterations)
* **Runtime**: Client-side Vanilla JavaScript (ES2022)
* **Storage Sync**: Supabase PostgreSQL (stores encrypted ciphertext envelopes only)
* **UI Layer**: Utility CSS, responsive dark mode, drag-and-drop credential reordering

## Key Features

* **Zero-Knowledge Security**: Cryptographic keys are derived in volatile memory via PBKDF2-HMAC-SHA256 and never persisted.
* **AES-256-GCM Encryption**: Each vault entry is encrypted with a unique 96-bit initialization vector (IV) providing confidentiality and ciphertext authentication.
* **Configurable Password Generator**: Customizable character matrices (uppercase, lowercase, digits, symbols) with entropy scoring.
* **Encrypted Import/Export**: Encrypted JSON backups for offline vault porting.

## Getting Started

### Prerequisites
* Web browser supporting the W3C WebCrypto API (all modern standards-compliant browsers)

### Installation
```bash
git clone https://github.com/itsgoharrehman/vault-password-manager.git
cd vault-password-manager
```

### Running Locally
```bash
npx serve .
```

## Security Model

1. **Master Password Input**: Entered into browser memory.
2. **Key Derivation**: PBKDF2 derives a 256-bit symmetric key using a high-entropy salt.
3. **Payload Encryption**: AES-256-GCM generates ciphertext and a 128-bit authentication tag.
4. **Ciphertext Storage**: Only the salt, IV, and ciphertext payload are synced to remote storage.

## Security Policy

Security vulnerabilities should be disclosed directly to `goharrehmanfsd260@gmail.com`.

## Maintainer

* **Gohar Rehman**
* GitHub: [@itsgoharrehman](https://github.com/itsgoharrehman)
* Email: `goharrehmanfsd260@gmail.com`
* Website: [itsgoharrehman.netlify.app](https://itsgoharrehman.netlify.app/)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
