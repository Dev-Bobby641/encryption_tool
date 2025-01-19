# Encryption Tool

A simple encryption tool that allows users to encrypt and decrypt files using AES encryption in CBC mode.

## Features
- **Encrypt files** using a password.
- **Decrypt encrypted files** with the correct password.
- **AES-256 CBC mode** encryption for secure file handling.
- **Padding and unpadding** of data to ensure proper encryption/decryption.

## Requirements
- Python 3.6 or higher
- Required Python libraries:
    - `pycryptodome` (for AES encryption and decryption)
    - `argparse` (for command-line arguments parsing)

## Installation

1. Clone the repository or download the source code.
   
   ```bash
   git clone https://github.com/yourusername/encryption_tool.git
   cd encryption_tool
   
2. Install the required dependencies using pip.

```bash
pip install pycryptodome
```

## Usage

### Encrypt a File
To encrypt a file, run the following command:

```bash
python main.py encrypt <file_path> <password>
<file_path>: The path to the file you want to encrypt.
<password>: The password you want to use for encryption (it will be padded or truncated to 32 bytes).
```
Example:

```bash
python main.py encrypt "document.txt" "strongpassword"
```

This will encrypt the document.txt file and save the encrypted file with a .enc extension.

### Decrypt a File
To decrypt an encrypted file, run the following command:

```bash
python main.py decrypt <file_path> <password>
<file_path>: The path to the encrypted file (must have the .enc extension).
<password>: The password used to encrypt the file.
```
Example:

```bash
python main.py decrypt "document.txt.enc" "strongpassword"
```

This will decrypt the file and save the original file without the .enc extension.

Command-line Arguments
- -h, --help: Displays help information.
- encrypt: Encrypts the file.
- decrypt: Decrypts the file.

## How it Works

### Encryption:

- The user provides a file and a password.
- The password is padded or truncated to 32 bytes to meet AES encryption key requirements.
- A random 16-byte initialization vector (IV) is generated for CBC mode.
- The file content is encrypted using AES in CBC mode.
- The IV and encrypted content are saved together in the output file.

### Decryption:

- The user provides the encrypted file and password.
- The password is padded or truncated to 32 bytes.
- The IV and encrypted content are extracted from the file.
- The content is decrypted using the AES key derived from the password.
- The decrypted content is saved as the original file (without the .enc extension).

### File Format

Encrypted files have the .enc extension.
Decrypted files will be saved with the same name as the original file, without the .enc extension.

## Example
### Encrypt a file:

```bash
python main.py encrypt "example.txt" "mypassword"
```

This creates example.txt.enc.

### Decrypt the file:

```bash
python main.py decrypt "example.txt.enc" "mypassword"
```

This restores the original example.txt file.
