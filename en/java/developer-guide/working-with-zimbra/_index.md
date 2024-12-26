---
title: Working with Zimbra
ArticleTitle: Working with Zimbra
type: docs
weight: 110
url: /java/working-with-zimbra/
---

## **About Zimbra**
Zimbra is an email, calendar and collaboration suite built for the cloud. Zimbra includes complete email, contacts, calendar, file sharing, tasks and messaging/videoconferencing, all accessed from the Zimbra Web Client from any device.
## **Read all messages from Zimbra TGZ storage**
Aspose.Email provides the [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) class to read Zimbra TGZ storage files. The following sample code demonstrates the use of the [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) class to read all messages from the file. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadAllMessagesFromZimbraTgzStorage-1.java" >}}
## **Save Messages and Directory Structure**
You may also save all the message with directory structure from the Zimbra TGZ storage file. For this, the [TgzReader](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader) class provides a method [ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) which takes the output path as a parameter.

The following code snippet demonstrates the use of the [TgzReader.ExportTo](https://apireference.aspose.com/email/java/com.aspose.email/TgzReader#exportTo\(java.lang.String\)) method to save all messages from the Zimbra TGZ storage file.



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-SaveMessagesFromZimbraTgzStorage-1.java" >}}

## **Export calendar and contact items from Zimbra backup files**

Aspose.Email makes it possible to export Zimbra’s calendar and contacts to iCalendar and VCard formats. The code sample below shows how to implement this feature into our project:

```java
try (TgzReader reader = new TgzReader("test2.tgz")) {
    //contacts files can be found in Contacts and Emailed Contacts subfolders
    //calendar files can be found in Calendar subfolder
    reader.exportTo("out");
}
```
