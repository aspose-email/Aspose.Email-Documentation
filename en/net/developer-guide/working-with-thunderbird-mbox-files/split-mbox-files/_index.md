---
title: Split MBOX Files with Aspose.Email in C#
ArticleTitle: Splitting MBOX Files
type: docs
weight: 50
url: /net/split-mbox-files-csharp/
---


## **Split MBOX Storage/Cancel Splitting Operation**

Aspose.Email provides methods for dividing large mailbox files into manageable chunks. This helps improve performance and memory efficiency, especially when working with extensive email archives. The available splitting options vary depending on the .NET version you're using.

### **Supported APIs by .NET Version**


**For .NET Framework 4.5 and .NET Core**

You can segment MBOX data using the `SplitInto` method of the [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/) class, with the option to include a cancellation token or customize the output file naming:

- [SplitInto(long chunkSize, string outputPath, CancellationToken token)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/splitinto/#splitinto_1) 

- [SplitInto(long chunkSize, string outputPath, string partFileNamePrefix, CancellationToken token)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/splitinto/#splitinto)

**Parameters:**

- chunkSize: The approximate size of each chunk in bytes.
- outputPath: The folder path where the chunks will be created.
- partFileNamePrefix: The prefix to be added to the filename of each part.
- token: A CancellationToken that allows for the possible cancellation of the operation.
    

**For .NET Versions Below 4.5**

Earlier versions support the same `SplitInto` method but without cancellation tokens:

- [SplitInto(long chunkSize, string outputPath)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/splitinto/#splitinto_2) 

- [SplitInto(long chunkSize, string outputPath, string partFileNamePrefix)](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/splitinto/#splitinto_3) 

- Cancel() - Used to interrupt the splitting process mid-way.

### **Code Samples for Controlled Splitting with Cancellation**

The following code samples demonstrate how to split an archive into up to 5 parts, automatically cancelling the operation afterward:

**.NET 4.5 / .NET Core**

```cs
int partCount = 0;

var tokenSource = new CancellationTokenSource();

var mbox = new MboxrdStorageReader(fileName, new MboxLoadOptions { LeaveOpen = false });

// Subscribe to events
mbox.MboxFileCreated += (sender, e) =>
{
    partCount++;
    if (partCount >= 5)
        tokenSource.Cancel();
};

System.Threading.Tasks.Task task = mbox.SplitInto(10000000, outputPath, tokenSource.Token);
task.Wait();
```

**Below .NET 4.5**

```cs
int partCount = 0;
var mbox = new MboxrdStorageReader(fileName, new MboxLoadOptions { LeaveOpen = false });
mbox.SplitInto(10000000, outputPath);

mbox.MboxFileCreated += (sender, e) =>
{
    partCount++;
    if (partCount >= 5)
        mbox.Cancel();
};
```

## **Split Large MBOX Files Asynchronously**

Working with large email archives can be inefficient and memory-intensive. To improve performance and manageability, Aspose.Email for .NET provides the asynchronous [SplitIntoAsync](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#methods) method, which allows you to split large files into smaller chunks - without blocking the main thread. The code sample below shows how to use [MboxStorageReader.CreateReaderAsync](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#methods) to open a large MBOX file asynchronously and then call [SplitIntoAsync](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/#methods) to divide it into smaller files, each with a maximum size of 10 MB. The resulting chunks are saved to the specified output directory using the prefix "chunk_".

```cs
using (var reader = await MboxStorageReader.CreateReaderAsync("input.mbox", new MboxLoadOptions()))
{
    await reader.SplitIntoAsync(10 * 1024 * 1024, "outputDirectory", "chunk_", CancellationToken.None);
}
```