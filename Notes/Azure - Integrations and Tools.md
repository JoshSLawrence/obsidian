---
tags:
  - Linux
  - Microsoft/Azure
---
# Azure and Microsoft Services

A reference for setting up a Linux guest with Microsoft/Azure identity and tools.

## Connecting a Linux host to Azure via Arc

The `az_connect_linux.sh` bash script can be ran directly on a Linux guest to connect it to Azure via Arc.

For the latest version of the bash script and more detailed instructions, follow these official links:

- [GitHub: az_connect_linux.sh](https://github.com/microsoft/azure_arc/blob/main/azure_arc_servers_jumpstart/scripts/az_connect_linux.sh)
- [Microsoft Learn: Connect an existing Linux server to Azure Arc](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/manage/hybrid/server/best-practices/onboard-server-linux)

If you choose to use the `az_connect_linux.sh` bash script, you will need to install wget:

```bash
sudo dnf install wget -y
```

*Note: all install examples use dnf, you may need to lookup specifics for your package manager*

## Installing the azure cli

This tool is not required, but is useful to have installed to the host if you intend on doing any automation or management of Azure resources from the Linux host.

- The _Azure Command Line Interface_, `azcli`, is built on top of python.

- Python is required for `azcli` to function and `Python 3.8` is the latest version of python supported by the tool.

_Note: the provided command uses the dnf package manager, depending on the Linux distribution, you may need to lookup and use yum/apt/etc to accomplish this task_

### 1. Install Python and verify the version

```bash
sudo dnf install python38 -y
python3 -V
```

### 2. Installing azcli using the Microsoft install script

The script should highlight any additional dependencies required - install dependencies as needed.

Pull and run the latest install script:

```bash
curl -L https://aka.ms/InstallAzureCli | bash
```

## Installing the Azure Monitor Agent

*The Linux guest must be connected to Azure via Arc before any extensions can be installed.*

Update values and run this command from any computer with azcli installed:

```bash
az connectedmachine extension create \
    --name AzureMonitorLinuxAgent \
    --publisher Microsoft.Azure.Monitor \
    --type AzureMonitorLinuxAgent \
    --machine-name <hostname> \
    --resource-group <resourcegroup> \
    --location <region> \
    --enable-auto-upgrade true
/
```


## Installing Microsoft Defender for Endpoint

The Microsoft Defender for Endpoint (MDE) installation should be automated via Azure Policy. Policy takes effect once the host is connected via Arc.

Should you need to install MDE manually, or confirm if the given distribution of Linux is supported, reference the following:

- [Microsoft Learn: Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-linux?view=o365-worldwide)

