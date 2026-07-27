---
tags:
  - Linux
---
> SSH Keys should be required and Password-based Authentication should be disabled when connecting via SSH

# Setup Remote Linux SSH Authentication

## 1. Generate a Public/Private Key Pair

For your reference, [the following guide by Red Hat](https://www.redhat.com/sysadmin/configure-ssh-keygen) provides an example using `ssh-keygen` to generate a public and private key pair.

While this example uses `ssh-keygen`, common alternatives include `OpenSSL` and `PuTTYgen`.

```bash
ssh-keygen -t rsa -b 4096 -C <hostname-accountname> -f <outputdirectory>
```

## 2. Import the Public for use by a given user

Manual public key import:

```bash
mkdir -p ~/.ssh
echo '<public_key_string>' >> ~/.ssh/authorized_keys
chmod -R go= ~/.ssh
chown -R <username>:<username> ~/.ssh
```

1-liner import from a remote host:

```bash
cat ~/.ssh/id_rsa.pub | ssh <username>@<hostname> "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

## 3. Disable Password Authentication

Ensure you can connect to the Linux host using the SSH Key before disabling Password Authentication.

Run the following command:

```bash
sudo vi /etc/ssh/sshd_config
```

With the text editor open, set `PasswordAuthentication` to `false`.

_Note: if the variable is missing, add it, but often you will find it commented out within the config file._

## 4. Restart the SSH Daemon

Setting `PasswordAuthentication` to `false` will not take effect until  the sshd service is restarted or the system is rebooted.

To restart the service, run the following command:

```bash
sudo systemctl restart sshd
```
