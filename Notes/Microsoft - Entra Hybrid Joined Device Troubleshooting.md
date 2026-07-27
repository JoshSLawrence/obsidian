---
tags:
  - Microsoft/Intune
  - Microsoft/Entra
---
# Hybrid Joined Device Troubleshooting

## Evaluate Join Status

To get the current join status of the computer:

```cmd
dsregcmd /status
```

If `AzureAdJoined` and `DomainJoined` both return `YES`, then the device is successfully hybrid joined.

![[entra-hybrid-join-trbl-p1.png]]

If the device is not joined, utilize the [following tool](https://github.com/Azure-Samples/DSRegTool/) to run initial checks.

## Reinitiate the registration/join to Intune

If the device is not hybrid-joined, there may be directory objects that exist in Entra already. To avoid any potential issues they should be removed before a re-join is attempted.

If this is the case, use the following command to clean-up objects when prepping to attempt a re-join:

```cmd
dsregcmd /debug /leave
```

After successfully executing this command and confirming the debug output, the computer should be rebooted. 

When the computer is later re-joined, it is also recommended to reboot the computer a final time.

Use this command to re-join: (ensure there is line of sight to a domain controller)

```cmd
dsregcmd /debug /join
```

## Going Deeper

This solution is applicable if the device is domain joined and hybrid joined in Entra, but the MDM flag is set to `None` instead of `Microsoft Intune`.

I have not confirmed if line-of-sight is required for the next series of steps. I would ensure the device is connected via VPN or directly on network to avoid any potential headache.

Additionally, confirm there are ***no*** objects in Intune already, if so delete it as its likely orphaned.

1. Ensure the following registry path exists:
	- `SYSTEM\CurrentControlSet\Control\CloudDomainJoin\TenantInfo\`

2. If this path exists, there should be a sub-directory as well with a name matching your Entra tenant ID.

3. The following keys should exist in this sub-directory:
	- `MdmEnrollmentUrl`
	- `MdmTermsOfUseUrl`
	- `MdmComplianceUrl`

4. If any of the above string- type keys are missing, create them.  If the keys do exist, validate that the key-values are correct. You can confirm the correct key-values in the Intune Admin Center:
	`Devices > Enroll Devices > Windows Enrollment > Automatic Enrollment`

5. Download the [PSEXEC](https://learn.microsoft.com/en-us/sysinternals/downloads/psexec) utility. This is required to execute the enrollment binary as **SYSTEM**.
	`You cannot run this binary as a user or an elevated user.`

6. With PSEXEC on your system, execute the binary with the following flags in PowerShell or CMD: 

```powershell
psexec -i -s powershell
```

*this will launch an interactive PowerShell session in the SYSTEM context*

7. Finally, execute the following command in the PSEXEC session: 

```powershell
C:\Windows\system32\deviceenroller.exe /c /AutoEnrollMDM
```

Review the device listing in the Entra Admin Portal. After a few minutes you should see the MDM column update from `NONE` to `Microsoft Intune`.

It may take longer still for the device to appear in the Intune Admin Portal as well, be sure to reboot the device. 

You may need line of sight to a DC and `gpupdate /force` after this final reboot.