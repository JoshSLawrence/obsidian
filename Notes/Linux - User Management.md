---
tags:
  - Linux
---
## Provisioning new Users

After creating the initial account for main admin use, new accounts should be created for those who are to use the system. Granting `sudo` to these users should be avoided if possible.

Should you run into issues creating a user, reference the documentation for the distribution you are using.

NOTE: After creating a new user, it is recommended to secure the user by enforcing [[Linux - Setup SSH Key Authentication|ssh key authentication]] if applicable.

Create a new user and set the password:

```bash
sudo adduser <username>
sudo passwd <username>
```

Grant a user sudo privilges:

```bash
sudo usermod -aG wheel <username>
```

List users:

```bash
sudo cut -d: -f1 /etc/passwd
```

Delete a user:

```bash
# delete a user and their home directory
sudo userdel -r <username>
# or delete only the user
sudo userdel <username>
```


