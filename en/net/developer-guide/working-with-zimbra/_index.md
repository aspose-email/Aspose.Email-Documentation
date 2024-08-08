---
title: Working with Zimbra
type: docs
weight: 120
url: /net/working-with-zimbra/
---


## **About Zimbra**

Zimbra is an email, calendar and collaboration suite built for the cloud. Zimbra includes complete email, contacts, calendar, file sharing, tasks and messaging/videoconferencing, all accessed from the Zimbra Web Client from any device.

## **Read all messages from Zimbra TGZ storage**

Aspose.Email provides the TgzReader class to read Zimbra TGZ storage files. The following sample code demonstrates the use of the TgzReader class to read all messages from the file. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadAllMessagesFromZimbraTgzStorage-1.cs" >}}

## **Get Total Items Count from a Tgz File**

The [GetTotalItemsCount()](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/gettotalitemscount/#tgzreadergettotalitemscount-method) method of the [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) class will return the total number of message items contained in the storage.

The following code sample will show you how to implement this method in your project:

```cs
using (TgzReader reader = new TgzReader(fileName))
{
    int count = reader.GetTotalItemsCount();
}
```

## **Save Messages and Directory Structure**

You may also save all the message with directory structure from the Zimbra TGZ storage file. For this, the TgzReader class provides a method ExportTo which takes the output path as a parameter.

The following code snippet demonstrates the use of the TgzReader.ExportTo method to save all messages from the Zimbra TGZ storage file.

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-SaveMessagesFromZimbraTgzStorage-1.cs" >}}

## **Export Calendar and Contact Items from Zimbra Backup Files**

To export Zimbra’s calendar and contacts and save them in iCalendar and VCard formats, you can use the following code snippet:

```cs
using (var reader = new TgzReader(@"test2.tgz"))
{
    //contacts files can be found in Contacts and Emailed Contacts subfolders
    //calendar files can be found in Calendar subfolder
    reader.ExportTo(@"out");
}
```