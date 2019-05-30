# AzCopy v10

AzCopy (v10) is the next-generation command-line utility designed for copying data to and from Microsoft Azure Blob and File, using simple commands designed for optimal performance. You can copy data between a file system and a storage account, or between storage accounts.

## What's new in AzCopy v10

:heavy_check_mark: Synchronize a file system up to Azure Blob or vice versa. Use `azcopy sync <source> <destination>`

:heavy_check_mark: Supports Azure Data Lake Storage Gen2. Use `myaccount.dfs.core.windows.net` for the URI to use ADLS Gen2 APIs.

:heavy_check_mark: Supports copying an entire account (Blob service only) to another account.

    Use `azcopy cp https://myaccount.blob.core.windows.net https://myotheraccount.blob.core.windows.net` which will enumerate all Blob containers and copy to the destination account

:heavy_check_mark: Supports [copying data from AWS S3](https://github.com/Azure/azure-storage-azcopy/wiki/Copy-from-AWS-S3)

:heavy_check_mark: Account to account copy is now using the new Put from URL APIs that will copy the data directly from one storage account to another. 

    No data transfer is needed down to the client where AzCopy runs. Therefore it is significantly faster!

:heavy_check_mark: List/Remove files and blobs in a given path

:heavy_check_mark: Supports glob patterns in path, and --exclude flags

:heavy_check_mark: Every AzCopy run will create a job order, and a related log file. You can view and restart previous jobs using `azcopy jobs` command.

:heavy_check_mark: Improved performance all around!

## Get started

For complete guidance about how to install and use AzCopy V10, see [Get started with AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy-v10?toc=%2fazure%2fstorage%2fblobs%2ftoc.json).

## Frequently asked questions

### What is the difference between `sync` and `copy`?

The `copy` command is a simple transferring operation, it scans the source and attempts to transfer every single file/blob. The supported source/destination pairs are listed in the help message of the tool. On the other hand, `sync` makes sure that whatever is present in the source will be replicated to the destination, and also whatever is not at the source will be deleted from the destination. If your goal is to simply move some files, then `copy` is definitely the right command, since it offers much better performance.

For `sync`, last modified times are used to determine whether to transfer the same file present at both the source and the destination. If the use case is to incrementally transfer data
then `sync` is the better choice, since only the modified/missing files are transferred.

### Will `copy` overwrite my files?

By default, AzCopy will overwrite the files at the destination if they already exist. To avoid this behavior, please use the flag `--overwrite=false`. 

## How to contribute to AzCopy v10

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
