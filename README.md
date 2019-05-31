# AzCopy v10

AzCopy v10 is the next-generation command-line utility designed to help you copy data to and from containers and file shares in Azure Storage accounts. AzCopy V10 provides you with simpler commands that are optimized for performance.

For complete guidance, see [Get started with AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy-v10?toc=%2fazure%2fstorage%2fblobs%2ftoc.json).

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
