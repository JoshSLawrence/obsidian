---
tags:
  - Microsoft/Azure
  - HADR
---
There are 6 types of redundancy configurations available for Azure Storage. The storage account type dictates the type of redundancy available for the account.

Available redundancy configurations for Azure storage:

| Redundancy Type | Description |
| ---- | ---- |
| LRS | 3 copies of your data are stored within the primary region. |
| GRS | Similar to LRS, but an additional 3 copies are stored in the region pair. |
| RA-GRS | Similar to GRS, but read operations are supported on the replicated data enabling additional workloads. |
| ZRS | 3 copies of your data are stored within the primary region, and each copy is guaranteed to be in a different availability zone. |
| GZRS | Similar to ZRS, but an additional 3 copes are stored in the region pair. The replicated is data is *not* zone redundant in the paired region. |
| RA-GZRS | Similar to GZRS, but read operations are supported on the replicated data enabling additional workloads. |

Redundancy configurations supported for each storage type:

| Storage Type | Supported Redundancy Configurations |
| ---- | ---- |
| Blob Storage | All Configurations |
| Data Lake Storage | All Configurations |
| Azure Files | LRS/GRS and ZRS/GZRS |
| Table Storage | All Configurations |
| Premium Block Blobs | LRS and ZRS |
| Premium File Shares | LRS and ZRS |
| Premium Page Blobs | LRS and ZRS |

