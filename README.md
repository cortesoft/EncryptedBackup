# EncryptedBackup
A repo to hold encrypted things I would need to bootstrap access to things.

## Requirements

- OpenSSL with PBKDF2 support (OpenSSL 1.1.1+ or LibreSSL 3.1+)
- Bash
- tar, git

These come standard on macOS and most Linux distributions.

## Usage

### Storing files

Place any files you want to back up into the `unencrypted/` directory (create it if it doesn't exist):

```
mkdir -p unencrypted
cp ~/some-important-file.txt unencrypted/
```

### Encrypting and pushing

```
./encrypt-and-push
```

You'll be prompted to enter and confirm a password. The script will:

1. Encrypt the `unencrypted/` directory into a file called `encrypted`
2. Commit and push to all git remotes
3. Delete the `unencrypted/` directory

### Decrypting

```
./decrypt
```

Enter your password and the files will be restored to `unencrypted/`.

## Encryption details

- AES-256-CBC via OpenSSL
- PBKDF2 key derivation with 600,000 iterations and random salt
