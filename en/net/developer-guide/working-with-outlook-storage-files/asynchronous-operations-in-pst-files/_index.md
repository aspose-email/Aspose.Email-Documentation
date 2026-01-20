---
title: Asynchronous Operations with PST Files
ArticleTitle: Asynchronous Operations with PST Files
type: docs
weight: 15
url: /net/asynchronous-operations-pst-files/
---

To enhance scalability and responsiveness in modern applications, Aspose.Email for .NET provides asynchronous methods for working with PST files. These new APIs allow developers to create, open, merge, and split PST files without blocking the main thread, making them ideal for UI applications and high-load services.

## **Create PST Files Asynchronously**

The [PersonalStorage.CreateAsync](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#methods) method allows you to create a new PST file asynchronously, enabling non-blocking execution in applications that work with large data or require responsive UIs. The following code sample demonstrates how to implement this feature into a C# project:

```cs
string pstFilePath = "newMailbox.pst";
var format = FileFormatVersion.Unicode;

// Create a new PST file asynchronously
using (var pst = await PersonalStorage.CreateAsync(pstFilePath, format, CancellationToken.None))
{
     Console.WriteLine($"PST file created at: {pstFilePath}");
}
```


## **Open PST Files Asynchronously**

To open an existing PST file asynchronously, use the [PersonalStorage.FromFileAsync](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#methods) method of the Aspose.Email API. The following code sample demonstrates how to implement this feature into a C# project:


```cs
string pstFilePath = "newMailbox.pst";
var format = FileFormatVersion.Unicode;

// Open the PST file asynchronously
        using (var pst = await PersonalStorage.FromFileAsync(pstFilePath, CancellationToken.None))
        {
            Console.WriteLine("PST file opened successfully.");

            // Access folders or messages here
            Console.WriteLine($"Root folder name: {pst.RootFolder.DisplayName}");
}
```

## **Merge PST Files Asynchronously**

The [MergeWithAsync](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#methods) method of the Aspose.Email [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#personalstorage-class) class allows you to merge the contents of one PST file into another asynchronously. This is useful in scenarios such as consolidating mail archives, combining backups, or processing email data in bulk - without blocking your application's main thread. The code sample below demonstrates how to use this method in your C# project:


```cs
string targetPstPath = "mainMailbox.pst";
string sourcePstPath = "archiveToMerge.pst";

// Open both PST files asynchronously
using (var targetPst = await PersonalStorage.FromFileAsync(targetPstPath, CancellationToken.None))
using (var sourcePst = await PersonalStorage.FromFileAsync(sourcePstPath, CancellationToken.None))
{
    // Merge the source PST into the target PST
    await targetPst.MergeWithAsync(sourcePst, CancellationToken.None);

    Console.WriteLine("Merge operation completed successfully.");
}
```


## **Split PST Files Asynchronously**

The code sample below demonstrates how to asynchronously open an existing PST file using [FromFileAsync](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#methods), and then split it into multiple parts using [SplitIntoAsync](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/#methods). Each part will be no larger than 50 MB and saved to the specified output directory. Asynchronous execution ensures that the operation doesn't block the main thread, making it suitable for applications that process large PST archives.

```cs
using (var pst = await PersonalStorage.FromFileAsync("input.pst"))
{
    await pst.SplitIntoAsync(50 * 1024 * 1024, "part_", "outputDirectory", CancellationToken.None);
}
```