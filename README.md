# SIGNED COMMIT

## Requirements

- [GnuPG](https://gnupg.org/)
- [Git](https://git-scm.com/)

## Commands

1. Create a key
```shell
$ gpg --full-generate-key
```
Choose the kind of key RSA

Choose key size 4096

Define how long the key should be valid

Define name and email of your git account


2. List keys
```shell
gpg --list-secret-key --keyid-form LONG
```

3. Export a key to add in github.
```shell
#To get key id
#sec   rsa4096/${id-here} YYYY-MM-DD [SC] [expires: YYYY-MM-DD]
$ gpg --armor --export ${key-id}
```

4. Copy and past your key in github. Check out [how add GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-new-gpg-key-to-your-github-account)

5. Config git to use signed commit
```shell
$ git config --global user.signingkey ${key-id}
$ export GPG_TTY=$(tty)
```
Tip: add `GPG_TTY` as environment in your system (~/.bash_profile or ~/.zshenv).

6. Config sign commit (global or per repository)

```shell
#global 
$ git config --global commit.gpgsign true
$ git config --global tag.gpgSign true

#per repository
$ git config commit.gpgsign true
$ git config tag.gpgSign true
```