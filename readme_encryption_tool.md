## Encryption:

Encrypting a file requires a password, the file name for the output of the encrypted data and encrypted secret

- use a ket derivation function
- generate a salt
- generate the key using the keysize password and salt
- then encrypt
- combine the base64 encoded value of the key and password
- encrypt it with a user defined password and write the secret value to disk

this password will be used to decrypt the secret file to retrieve access to the initial password and key to decrypt the actual data.

```
$ python encrypto.py --password "mypassword" --filename data.enc --secret secret.key
```

```
$ cat data.enc
dgUQRqT6eErBfnCNhIH+7huXqK.....jZYTm+cNYEWA==
```

```
$ cat secret.key
c2MAAnbLlX3R32GOgbAmdu......5MKgpRMcCAlGPrIA..
```

## Decryption:

Decrypting a file requires the user defined password used to encrypt the secret, the encrypted file name and secret file name

```
$ python decrypto.py --password "mypassword" --filename data.enc --secret secret.key
this is my secure string
```

## Resources:

- https://medium.com/@authmane512/how-to-securely-encrypt-data-in-python-with-nacl-library-591d847e5789
- https://sysadmins.co.za/encryption-and-decryption-with-simple-crypt-using-python/