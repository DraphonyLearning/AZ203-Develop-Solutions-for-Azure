# Azure Storage Account

Create a console "Blob Storage Explorer".

## Features
Your solution should support the following features.

### Containers and (Virtual) Directories
1. User can list all the BlobItems in the current container or directory.
2. User can switch into a container or directory. When switching the container, show for the new container:
    1. Show the public access level and stored access policies
    2. Lists all the meta data
    3. List all Blobs with AccessTier, BlobType, LastModified
3. User can create directories in the current context (current container and current directories).

### Blobs
1. Acquiring the Lease for the current BlobItem
    * Delete the BlobItem on the [Azure Portal](https://portal.azure.com) when you have acquired the Lease. Does it work?
2. Create a Shared Access Signature from a given Shared Access Policy
    * Delete the SAP after you have acquired the SAS. Use your SAS again. Does it still work?
3. Enable user to upload files as BlockBlob, AppendBlob.
    *  PageBlob is optional 
4. Decrease the access tier of a blob. (**Do not increase the access tier, this will cause extra charges!**).
    * Can you do this all blob types?

### Bonus Task
1. Use a [Blob Batch](https://docs.microsoft.com/en-us/rest/api/storageservices/blob-batch) to perform multiple operations.

## Hints
1. If you prefer, you can use the [REST-API]( https://docs.microsoft.com/en-us/rest/api/storageservices/blob-service-rest-api).
2. Or use the Azure SDK for .NET.
    * `dotnet add package Azure.Storage.Blobs`
    * `dotnet add package Azure.Storage.Blobs.Batch`
    * Please be aware, that packages starting `Microsoft.Azure` are deprecated.
3. You may need the following classes:
    * [BlobContainer](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.blobcontainerclient?view=azure-dotnet)
    * [BlobClient](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.blobclient?view=azure-dotnet)
    * [BlobUriBuilder](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.bloburibuilder?view=azure-dotnet)
    * [PageBlobClient](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.specialized.pageblobclient?view=azure-dotnet)
    * [BlockBlobClient](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.specialized.blockblobclient?view=azure-dotnet)
    * [BlobLeaseClient](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.specialized.blobleaseclient?view=azure-dotnet)
    * [AppendBlobClient](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.blobs.specialized.appendblobclient?view=azure-dotnet)
    * [BlobSASBuilder](https://docs.microsoft.com/en-us/dotnet/api/azure.storage.sas.blobsasbuilder?view=azure-dotnet)