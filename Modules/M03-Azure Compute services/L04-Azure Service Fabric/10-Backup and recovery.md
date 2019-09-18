

Creating backups requires development effort, and a method to be called within a Reliable Service. This causes the data to be copied to a local backup folder. 

After that, it's possible to copy that data to a central storage location. This location should be in a different fault domain, for example, in a different cloud. Because data is shared between partitions, every primary replica of your Stateful Reliable Services needs to create its own backups. Use the following code to do this:

``` csharp

public async Task BeginCreateBackup()
{
	
	var backupDescription = new BackupDescription(BackupOption.Full, PostBackupCallbackAsync);
	await BackupAsync(backupDescription);
}

private async Task<bool> PostBackupCallbackAsync(BackupInfo backupInfo, CancellationToken cancellationToken)
{
	await _centralBackupStore.UploadBackupFolderAsync(backupInfo.Directory, cancellationToken);
	return true;
}
```

In the code sample above, a backup is created first. After that operation completes, the method **PostBackupCallAsync** will be invoked. In this method, the local backup folder is copied to the central location. The implementation of ```_centralBackupStore``` is omitted.

### Restoring backups
Restoring backups also requires some development effort. The Reliable Service needs to have code that is executed by Service Fabric in a data loss situation such as a node failure or using code. After the data loss is triggered, your Reliable Service can access your central storage location and download the contents to the local backup folder. After that, data can be restored from the local backup folder. Every running primary replica of your Stateful Reliable Services must restore its own backups. The following command demonstrates how to do these steps:

``` csharp
public async Task BeginRestoreBackup()
{
	var partitionSelector = PartitionSelector.PartitionKeyOf(Context.ServiceName,
		((Int64RangePartitionInformation) Partition.PartitionInfo).LowKey);
	var operationId = Guid.NewGuid();

	await new FabricClient(FabricClientRole.Admin).TestManager.StartPartitionDataLossAsync(operationId, partitionSelector, DataLossMode.FullDataLoss);
	//Causes OnDataLossAsync to be called.
}

protected override async Task<bool> OnDataLossAsync(RestoreContext restoreCtx, CancellationToken cancellationToken)
{
	string backupFolder = Context.CodePackageActivationContext.WorkDirectory;
	await _centralBackupStore.DownloadBackupFolderAsync(backupFolder, cancellationToken);

	var restoreDescription = new RestoreDescription(backupFolder, RestorePolicy.Force);
	await restoreCtx.RestoreAsync(restoreDescription, cancellationToken);
	return true;
}
```

In this code sample, backups are retrieved from a central location, and the local folder is used to call `RestoreAsync`. The call to `OnDataLossAsync` can be triggered by executing the following command:

```FabricClient.TestManagementClient.StartPartitionDataLossAsync```

Alternatively, you can use the following PowerShell command:

``` Start-ServiceFabricPartitionDataLoss ```

Again, the implementation of ```_centralBackupStore``` is omitted.

### Fire drills 
Consider your backup strategy carefully. The amount of data loss that is acceptable differs for every service. The size of the central store will grow quickly if you create many full backups.

Make sure to gain hands-on experience with creating and restoring backups by practicing it. This way, you'll know that your solution works, and you won't discover that your backup strategy is insufficient during a real disaster-recovery situation.
