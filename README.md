# monkeysuse
A custom port of Monkeysphere key translation utility to openSUSE 15.x and SLE-15.

Monkeysphere sources were copied from the following commit:
https://github.com/dkg/monkeysphere/commit/97ade311fc287985972bb73a47dd75450260c389

This tool allows converting gpg private keys to SSH private keys.

**Prerequisites:**

Install the following packages using zypper:

```perl-Crypt-OpenSSL-RSA```

```perl-Crypt-OpenSSL-Bignum```

**Usage:**

```openpgp2ssh < mykey.gpg```

or (when the key has several subkeys)

```gpg --export $KEYID | openpgp2ssh $KEYID```

**And then...**

To convert a gpg key to an ssh key (beware, this will remove and replace the user's current SSH key, if any):
```
openpgp2ssh < mykey.gpg > ~/.ssh/id_rsa
chmod 600 ~/.ssh/id_rsa
```
Do not forget to create the corresponding public key out of the private key:
```
ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

