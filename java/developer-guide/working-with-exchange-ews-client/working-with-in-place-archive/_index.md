---
title: Working with In-Place Archive
type: docs
weight: 150
url: /java/working-with-in-place-archive/
---


## **In-Place Archives in Office 365**
In-Place Archives in Office 365 provides users with additional storage space. After the archive mailboxes are turned on, users can access and store messages in their Archive Mailbox by using Microsoft Outlook and Outlook on the Web. When the mailbox with In-Place archiving enabled is opened with Outlook, the archive mailbox is shown as a separate mailbox.
## **Move Items to In-Place Archive**
Aspose.Email API can be used to move items into users archive mailbox by using the [IEWSClient.archiveItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) method. [IEWSClient.archiveItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) method provides four overloads which are listed below.

- archiveItem(String sourceFolderUri, Appointment appointment)
- archiveItem(String sourceFolderUri, ExchangeTask task)
- archiveItem(String sourceFolderUri, MapiMessageItemBase item)]
- archiveItem(String sourceFolderUri, String uniqueId)

The code example given below demonstrates the use of [IEWSClient.archiveItem](https://reference.aspose.com/email/java/com.aspose.email/IEWSClient#archiveItem\(java.lang.String,%20java.lang.String\)) method to move an email to the Archive Mailbox by using the UniqueUri.



~~~Java
NetworkCredential credentials = new NetworkCredential(username, password, domain);
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credentials);

ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

for (ExchangeMessageInfo msgInfo : (Iterable<ExchangeMessageInfo>) msgCollection) {
    System.out.println("Subject:" + msgInfo.getSubject());
    client.archiveItem(client.getMailboxInfo().getInboxUri(), msgInfo.getUniqueUri());
}
client.dispose();
~~~