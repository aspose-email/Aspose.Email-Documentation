---
title: Convert OLM to PST
type: docs
weight: 120
url: /net/convert-olm-to-pst/
---

[OLM](https://docs.fileformat.com/email/olm/) is a database file format used by Microsoft Outlook for Mac systems. OLM files store email messages, calendar data, contact data, and application settings. An OLM file isn’t supported by Outlook for Windows. Thus, it is not possible to open an Outlook for Mac (OLM) file in Outlook for Windows. If you want to migrate your mailbox from Outlook for Mac to Outlook for Windows, it's necessary to convert the Outlook for Mac OLM file to Outlook PST file format.

## **Steps to convert an OLM file to PST**

To convert an OLM file to PST follow the steps given below:

1. Create an instance of [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class to open source OLM.
2. Open a source OLM file.
3. Create a new PST file using [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Create a GetContainerClass method to map the message class to a folder class.
5. Create an AddToPst method that recursively reads each folder and its messages from OLM using EnumerateMapiMessages method and adds them to the PST in the same order using AddSubFolder and AddMessage methods.

## **Code sample**

The following code sample shows how to convert an OLM to a PST.

**Main** method:

```cs
// create an instance of OlmStorage class to open source OLM
using (var olm = new OlmStorage("my.olm"))
// create a new PST file
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    // recursively reads each folder and its messages 
    // and adds them to the PST in the same order
    foreach (var olmFolder in olm.FolderHierarchy)
    {
        AddToPst(pst.RootFolder, olmFolder);
    }
} 
```

**GetContainerClass** method implementation:

```cs
public string GetContainerClass(string messageClass)
{
    if (messageClass.StartsWith("IPM.Contact") || messageClass.StartsWith("IPM.DistList"))
    {
        return "IPF.Contact";
    }

    if (messageClass.StartsWith("IPM.StickyNote"))
    {
        return "IPF.StickyNote";
    }

    if (messageClass.StartsWith("IPM.Activity"))
    {
        return "IPF.Journal";
    }

    if (messageClass.StartsWith("IPM.Task"))
    {
        return "IPF.Task";
    }

    if (messageClass.StartsWith("IPM.Appointment") || messageClass.StartsWith("IPM.Schedule.meeting"))
    {
        return "IPF.Appointment";
    }

    return "IPF.Note";
}
```

**AddToPst** method implementation:

```cs
public void AddToPst(FolderInfo pstFolder, OlmFolder olmFolder)
{
    FolderInfo pstSubFolder = pstFolder.GetSubFolder(olmFolder.Name);

    foreach (var msg in olmFolder.EnumerateMapiMessages())
    {
        if (pstSubFolder == null)
        {
            pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name, GetContainerClass(msg.MessageClass));
        }

        pstSubFolder.AddMessage(msg);
    }

    if (pstSubFolder == null)
    {

        pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name);
    }

    foreach (var olmSubFolder in olmFolder.SubFolders)
    {
        AddToPst(pstSubFolder, olmSubFolder);
    }
}
```
