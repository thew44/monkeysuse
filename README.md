# monkeysuse
A custom port of Monkeysphere key translation utility to openSUSE 15.x and SLE-15

This tool allows converting gpg private keys to SSH private keys.

**Usage:**

{{openpgp2ssh < mykey.gpg}}

or 

{{gpg --export $KEYID | openpgp2ssh $KEYID}}

**And then...**
To convert a gpg key to an ssh key (will replace the user SSH key, if any):
{{openpgp2ssh < mykey.gpg >> ~/.ssh/id_rsa}}
{{chmod 600 ~/.ssh/id_rsa}}
Do not forget to create the corresponding public key:
{{ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub}}

