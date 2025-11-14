# Password Manager

A secure command-line password manager that encrypts and stores your passwords using the Fernet symmetric encryption algorithm.


---

## 🔐 Password Manager

### Features

- 🔐 **Secure Encryption**: Uses Fernet (symmetric encryption) to encrypt passwords before storage
- 💾 **Local Storage**: Passwords are stored locally in an encrypted format
- 👀 **View Passwords**: Decrypt and view all stored passwords
- ➕ **Add Passwords**: Add new account passwords with encryption
- 🔑 **Key Management**: Separate encryption key file for security

### Requirements

- Python 3.x
- `cryptography` library

### Installation

```bash
pip install cryptography
```

### Setup

Before first use, you need to generate an encryption key. Uncomment the `write_key()` function call in `password.py` and run it once:

```python
def write_key():
    key = Fernet.generate_key()
    with open("key.key", "wb") as key_file:
        key_file.write(key)
write_key()
```

After generating the key, comment out the `write_key()` call again to prevent overwriting your key.

### Usage

```bash
python password.py
```

**Commands:**
- `view` - View all stored passwords (decrypted)
- `add` - Add a new password
- `q` - Quit the program

**Example Session:**
```
Would you like to add a new password or view existing ones (view, add), press q to quit? add
Account Name: GitHub
Password: mySecurePassword123
Would you like to add a new password or view existing ones (view, add), press q to quit? view
User: GitHub | Password: mySecurePassword123
Would you like to add a new password or view existing ones (view, add), press q to quit? q
```

### Security Notes

⚠️ **Important Security Considerations:**

1. **Keep `key.key` secure**: If you lose this file, you cannot decrypt your passwords. If someone else gets it, they can decrypt all your passwords.

2. **Backup your key**: Consider backing up `key.key` to a secure location (encrypted USB drive, password manager, etc.)

3. **Never commit sensitive files**: The `.gitignore` file ensures `key.key` and `passwords.txt` are not committed to version control.

4. **File permissions**: On Unix systems, consider setting restrictive permissions:
   ```bash
   chmod 600 key.key passwords.txt
   ```

## File Structure

```
password_manager/
├── password.py          # Password manager application
├── passwords.txt        # Encrypted password storage (not in git)
├── key.key             # Encryption key (not in git)
├── .gitignore          # Git ignore file for sensitive data
└── README.md           # This file
```

---

## Installation (All Projects)

1. Clone this repository:
```bash
git clone https://github.com/AyushDas4890/Password-Manager.git
cd Password-Manager
```

2. Install all required dependencies:
```bash
pip install cryptography requests
```

---

## How It Works

### Password Manager
1. **Encryption**: When you add a password, it's encrypted using Fernet before being stored in `passwords.txt`
2. **Storage Format**: Each entry is stored as `AccountName|encrypted_password`
3. **Decryption**: When viewing passwords, the encrypted data is decrypted using the same key

### Currency Converter
1. **API Request**: The program sends a request to the Free Currency API with the base currency
2. **Data Retrieval**: The API returns current exchange rates for the specified currencies
3. **Display**: The conversion rates are formatted and displayed to the user

---

## License

This project is open source and available for personal use.

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

---

## Author

**Ayush Das**

- GitHub: [@AyushDas4890](https://github.com/AyushDas4890)
