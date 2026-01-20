---
title: Delete Emails from IMAP Server in Python Environment
ArticleTitle: Delete Emails from IMAP Server
type: docs
weight: 20
url: /python-net/delete-emails-from-imap-server-python/
---


## **Delete Single Message from Server**

To delete a message from an IMAP server, the Aspose.Email library provides the **delete_message** method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class. It takes the message sequence number or unique ID as a parameter. The following code snippet shows you how to delete an email message with the message ID 1 from an IMAP server:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}

## **Delete Multiple Messages from Server**

Multiple emails can be deleted from a mailbox using the **delete_messages** method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class provided by the Aspose.Email API. This method provides a number of options to delete multiple messages from the server using unique ids, sequence numbers or ImapMessageInfoCollection elements. The following code snippet shows you how to delete multiple messages:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}
