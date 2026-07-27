---
tags:
  - Virtualization/VMware
---
## Migrate VM(s) to a new Datastore

1. Right click the VM and click *Migrate*
2. Select *Change storage only*
3. Select the Destination Datastore
4. Click Finish, progress can be monitored in the Task View

## Create a new Datastore

1. Provision a new volume on the external SAN or NAS solution.
2. Expose the new volume on the SAN or NAS solution to VMware hosts in the cluster.
3. In VMware, right click the desired cluster and select: Storage > Rescan Storage.
4. Check *Scan for new VMFS Volumes* and click OK.
5. After the scan, right click the cluster and select Storage > New Datastore.
6. Select the Datastore Type.
7. Name the Datastore and select a host to view the available disks/vols.
	- Even if 1 host is selected, the datastore will be provisioned to all in the cluster assuming they are:
		1. Clustered in VMware.
		2. SAN/NAS exposes the underlying volume/disk to all hosts in the cluster.
8. Set the desired partitions etc... and complete.

## Delete a Datastore

1. Right click the datastore and unmount.
2. Right click the datastore and delete the datastore. (assuming are certain data recovery is not needed)
3. In the external SAN/NAS solution, un-expose and delete the volume/disk.
4. In VMware, right click the cluster and click Storage > Rescan Storage.
5. The old Datastore will now disappear if it was only unmounted.

	If the Datastore is only unmounted, and the underlying SAN/NAS has recovery options... and recovery is needed. Restore in the SAN/NAS, expose to the VMware cluster, rescan storage, and the Datastore should reappear as long as it was not deleted in step 2. At this stage, it can be re-mounted to hosts in the cluster.