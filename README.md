# Password Manager

A secure command-line password manager that encrypts and stores your passwords using the Fernet symmetric encryption algorithm from the `cryptography` library.

## Features

- 🔐 **Secure Encryption**: Uses Fernet (symmetric encryption) to encrypt passwords before storage
- 💾 **Local Storage**: Passwords are stored locally in an encrypted format
- 👀 **View Passwords**: Decrypt and view all stored passwords
- ➕ **Add Passwords**: Add new account passwords with encryption
- 🔑 **Key Management**: Separate encryption key file for security

## Requirements

- Python 3.x
- `cryptography` library

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd password_manager
```

2. Install the required dependencies:
```bash
pip install cryptography
```

## Setup

Before first use, you need to generate an encryption key. Uncomment the `write_key()` function call in `password.py` and run it once:

```python
def write_key():
    key = Fernet.generate_key()
    with open("key.key", "wb") as key_file:
        key_file.write(key)
write_key()
```

After generating the key, comment out the `write_key()` call again to prevent overwriting your key.

## Usage

Run the program:
```bash
python password.py
```

### Commands

- **`view`** - View all stored passwords (decrypted)
- **`add`** - Add a new password
- **`q`** - Quit the program

### Example Session

```
Would you like to add a new password or view existing ones (view, add), press q to quit? add
Account Name: GitHub
Password: mySecurePassword123
Would you like to add a new password or view existing ones (view, add), press q to quit? view
User: GitHub | Password: mySecurePassword123
Would you like to add a new password or view existing ones (view, add), press q to quit? q
```

## File Structure

```
password_manager/
├── password.py          # Main application code
├── passwords.txt        # Encrypted password storage (not in git)
├── key.key             # Encryption key (not in git)
└── README.md           # This file
```

## Security Notes

⚠️ **Important Security Considerations:**

1. **Keep `key.key` secure**: If you lose this file, you cannot decrypt your passwords. If someone else gets it, they can decrypt all your passwords.

2. **Backup your key**: Consider backing up `key.key` to a secure location (encrypted USB drive, password manager, etc.)

3. **Never commit sensitive files**: The `.gitignore` file ensures `key.key` and `passwords.txt` are not committed to version control.

4. **File permissions**: On Unix systems, consider setting restrictive permissions:
   ```bash
   chmod 600 key.key passwords.txt
   ```

## How It Works

1. **Encryption**: When you add a password, it's encrypted using Fernet before being stored in `passwords.txt`
2. **Storage Format**: Each entry is stored as `AccountName|encrypted_password`
3. **Decryption**: When viewing passwords, the encrypted data is decrypted using the same key

## License

This project is open source and available for personal use.

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

