# 🔓 Encryption

Encryption in aleph.im uses the [ECIES standard](https://en.wikipedia.org/wiki/Integrated\_Encryption\_Scheme), using the [ECIES Js library](https://github.com/ecies/js) on SECP256K1 and a fork of [ECCrypto](https://github.com/bitchan/eccrypto) for others.

Content is encrypted for a specific public key and can be decrypted with the same account private key that was used for encryption.&#x20;

| ENDPOINTS                               |                                              |
| --------------------------------------- | -------------------------------------------- |
| [Encrypt](encrypt.md)                   | [.encrypt()](encrypt.md)                     |
| [Encrypt for self](encrypt-for-self.md) | [.encrypt\_for\_self()](encrypt-for-self.md) |
| [Decrypt](decrypt.md)                   | [.decrypt()](decrypt.md)                     |
