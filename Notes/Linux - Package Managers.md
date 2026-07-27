---
tags:
  - Linux
---
# Linux Package Managers

Updating any given Linux distribution is done via a package manager. Syntax to carry out a given update varies between package manger.

For those coming from windows:

- Updating packages is akin to pushing Windows updates.
- Updating the distribution release is akin to Upgrade the OS itself.

_Note: you can install a different package manager if you do not prefer what is shipped with a given Linux distribution._

### Disclaimer

The commands in this section focus on updating all system packages. Each package manager has various flags available to manage updates with great flexibility.

It is recommended to review documentation for each package manager to learn the various controls.

Some helpful links:

- [apt](https://ubuntu.com/server/docs/package-management)
- [yum](https://man7.org/linux/man-pages/man8/yum.8.html)
- [dnf](https://docs.fedoraproject.org/en-US/quick-docs/dnf/)
- [pacman](https://wiki.archlinux.org/title/pacman)

### Updating with apt

The apt package manager is often found on Debian based distributions, such as Ubuntu.

To check for updates:

```bash
sudo apt update
# or
sudo apt-get update
```

To deploy the updates:

```bash
sudo apt upgrade
# or
sudo apt-get upgrade
```

### Updating with yum and dnf

The yum package manager is commonly found on Red Hat based distributions.

Dandified YUM, or **_dnf_**, is esentially an improved version of the yum package manager.

To check for updates:

```bash
sudo yum check-update
# or
sudo dnf check-update
```

To deploy the updates:

```bash
sudo yum update
# or
sudo dnf update
```

### Updating with pacman

The package manager pacman is found most commonly on Arch Linux based distributions.

It is possible to check for package updates and push those updates with a single command:

```bash
sudo pacman -Syu
```

