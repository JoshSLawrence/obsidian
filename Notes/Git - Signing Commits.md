---
tags:
  - Git
  - GitHub
---
- [GitHub GPG Setup](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
- [Add GPG Key to GitHub Account](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account)
- [Tell Git About the Signing Key](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key)
# Setup a new GPG Key

Generate a GPG key pair

```shell
gpg --full-generate-key
```

| Option     | Setting               |
| ---------- | --------------------- |
| Type       | RSA and RSA           |
| Key Size   | 4096                  |
| Validity   | 0 (does not expire)   |
| Real Name  | Josh Lawrence         |
| Email      | josh@joshlawrence.dev |
| Comment    | Device Idenifer       |
| Passphrase | Grab from Bitwarden   |
Get the key id

```shell
gpg --list-secret-keys --keyid-format=long
```

You get an output like this

```shell
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
/home/josh/.gnupg/pubring.kbx
-----------------------------
sec   rsa4096/105DAB856384BEA1 2026-03-04 [SC]
      87BA20266F83E7483D1E8803105DAB856384BEA1
uid                 [ultimate] Josh Lawrence (PSU WKS) <josh@joshlawrence.dev>
ssb   rsa4096/C4548162F5BE1DE0 2026-03-04 [E]
```

The id in this example is `105DAB856384BEA1`

---
Fetch the public key

```shell
gpg --armor --export <id>
```

## Add to GitHub

1. Login to GitHub
2. Open Account Settings
3. Under `Access`, click `SSH and GPG Keys`
4. Scroll to the GPG Key section and click `New GPG Key`
5. Input a name and paste in the public key

# Tell Git About the Key

Unset the key format

```shell
git config --global --unset gpg.format
```

Get the key id

```shell
gpg --list-secret-keys --keyid-format=long
```

You get an output like this

```shell
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
/home/josh/.gnupg/pubring.kbx
-----------------------------
sec   rsa4096/105DAB856384BEA1 2026-03-04 [SC]
      87BA20266F83E7483D1E8803105DAB856384BEA1
uid                 [ultimate] Josh Lawrence (PSU WKS) <josh@joshlawrence.dev>
ssb   rsa4096/C4548162F5BE1DE0 2026-03-04 [E]
```

The id in this example is `105DAB856384BEA1`

---
Set the git signing key

```shell
git config --global user.signingkey <id>
```

Configure git to sign commits and tags

```shell
git config --global commit.gpgsign true
git config --global tag.gpgSign true
```

> [!TIP]
> Omit `--global` for per-repository signing config. The above will set the global default.