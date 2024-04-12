## Aufgabe 2
Die Datei [email.txt](./email.txt) wird als Schlüssel genutz für folge Aufgaben. Der kryptograifsche Fingerabdruck mit den MD5 Verfahren kann mit dem folgenden Kommando erzeugt und in die Datei [md5_email.txt](./md5_email.txt) gespeichert werden:

```bash
openssl dgst -md5 email.txt > md5_email.txt
```

Der kryptograifsche Fingerabdruck mit den SHA3-256 Verfahren kann mit dem folgenden Kommando erzeugt und in die Datei [sha3-256_email.txt](./sha3-256_email.txt) gespeichert werden:

```bash
openssl dgst -sha3-256 email.txt > sha3-256_email.tx
```

## Aufgabe 3
Mit dem folgendem Kommando wird die Datei [email.txt](./email.txt) mittels des AES-256 Verfahren verschlüsselt. Als Schlüssel wird die zu verschlüsselnde Datei benutzt.

```bash
openssl enc -aes-256-cbc -in email.txt -out aes-256-cbc_email.txt -pass file:email.txt
```

Die [aes-256-cbs_email.txt](./aes-256-cbc_email.txt) Datei kann mithilfe des folgenden Kommandso wieder entschlüsselt werden:

```bash
openssl enc -d -aes-256-cbc -in aes-256-cbc_email.txt -out decr.txt -pass file:email.txt 
```

## Aufagbe 4
| OS                | Software (Library)  | Algorithms      |
| ----------------- | ------------------- | --------------- |
| Win, Linux, MacOS | OpenSSL             | SHA AES RSA TLS |
| Win               | Microsoft CryptoAPI | SHA AES RSA TLS |
| Linux, MacOS, Win | GnuPG               | SHA AES RSA TLS |
| Linux, MacOS, Win | LibreSSL            | SHA AES RSA TLS |
| Linux, MacOS, Win | Botan               | SHA AES RSA TLS |

## Aufgabe 5
Der folgenden Kommando generiert einen [Private Key](./keys/private_key.pem), welche den [Public Key](./keys/public_key.pem) ebenfalls beinhaltet.
```bash
openssl genrsa -out keypair.pem 1024
```

Der [Public Key](./keys/public_key.pem) muss vom [Private Key](./keys/private_key.pem) extrahiert werden:
```bash
openssl rsa -in private_key.pem -pubout -out public_key.pem
```

Das gerade erstellte Schlüssel Paar kann mit den folgenden zwei Kommandos genutzt werden um die Datei [email.txt](./email.txt) zu verschlüsseln in die Datei [public_key_enc_email.txt](./private_key_enc_email.txt) und zu entschlüsseln in die Datei dec_email.txt
```bash
openssl pkeyutl -encrypt -pubin -inkey  keys/public_key.pem -in email.txt -out public_key_enc_email.txt
```

```bash
openssl pkeyutl -decrypt -inkey keys/private_key.pem -in public_key_enc_email.txt -out dec_email.txt
```

## Aufgabe 6
1. DigiCert, Inc.
2. Google Trust Service LLC
3. Microsoft Corporation
4. D-Trust GmbH
5. Amazon
6. Apple Inc.
7. Sectigo Limited
8. Let's Encrypt
