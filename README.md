# VaultText — Text Encryption and Decryption Website

VaultText is a beginner-friendly cybersecurity mini project that lets users encrypt and decrypt text in their web browser using a passphrase.

## Features

- Encrypt plain text with a passphrase.
- Decrypt a previously generated VaultText package.
- AES-256-GCM authenticated encryption.
- PBKDF2-SHA-256 key derivation with 310,000 iterations.
- A fresh random salt and initialization vector are generated for each encryption.
- Copy results, clear fields, and show or hide the passphrase.
- Responsive interface for desktop and mobile.
- No server, account, database, or external API is required.

## Technologies Used

- HTML5 — page structure
- CSS3 — responsive user interface
- JavaScript — application logic
- Web Crypto API — cryptographic operations provided by the browser

## Run the Project

1. Download or clone this repository.
2. Open the project folder in Visual Studio Code.
3. Open `index.html` using the VS Code Live Server extension.
4. Enter the text and a strong passphrase.
5. Click **Encrypt text** and save the encrypted package.
6. To recover the original text, choose **Decrypt**, paste the complete package, and enter the same passphrase.

You can also open the page from a secure HTTPS host. Modern browsers generally restrict Web Crypto on ordinary local files, so use Live Server or HTTPS if encryption is unavailable.

## How It Works

1. The browser generates a cryptographically secure 16-byte random salt and 12-byte random IV.
2. PBKDF2 with SHA-256 derives a 256-bit AES key from the user's passphrase and salt.
3. AES-GCM encrypts the text and authenticates the encrypted data.
4. The app packages the salt, IV, and ciphertext into a text string beginning with `VAULTTEXT1:`.
5. During decryption, the app extracts the values, derives the same key from the passphrase, and asks AES-GCM to authenticate and decrypt the package.

## Important Security Notes

- Keep your passphrase private and use a long, unique passphrase.
- Store the encrypted package safely. The application does not keep a copy on a server.
- If you lose the passphrase, the original text cannot be recovered.
- A wrong passphrase or modified encrypted package causes decryption to fail.
- This is an educational project and has not undergone an independent security audit. Do not use it as the sole protection for highly sensitive production data.

## Project Structure

```
Text-Encryption-Decryption/
├── index.html
└── README.md
```

## Viva / Project Explanation

**What is the purpose of this project?**  
It demonstrates how cryptography can protect confidential text. A user encrypts a message with a passphrase and later decrypts it using the same passphrase.

**Why AES-256-GCM?**  
AES is a widely used symmetric encryption algorithm. GCM provides confidentiality and authentication, helping detect incorrect keys or tampering.

**What is PBKDF2?**  
PBKDF2 is a password-based key derivation function. It applies repeated hashing with a random salt to make deriving an encryption key from a passphrase more computationally expensive.

**Does the project send data to a server?**  
No. The encryption and decryption operations run in the browser using the Web Crypto API.

---

Created as a cybersecurity learning project.
