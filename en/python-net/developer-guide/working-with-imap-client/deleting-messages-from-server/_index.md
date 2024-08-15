---
title: Deleting Messages from Server
type: docs
weight: 20
url: /python-net/deleting-messages-from-server/
---


## **Deleting Messages**
The ImapClient class can delete messages from an IMAP server. The ImapClient class DeleteMessage() function is used to delete messages. It takes the message sequence number or unique ID as a parameter. The ImapClient provides DeleteMessage and DeleteMessages methods for deleting messages one by one or multiple. The following code snippet shows you how to delete an email message with the message ID 1 from an IMAP server.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteSingleMessage-DeleteSingleMessage.py" >}}
## **Deleting Multiple Messages**
Multiple emails can be deleted from mailbox using the ImapClient of Aspose.Email API. The DeleteMessages method provides a number of options to delete multiple messages from the server using unique ids, sequence numbers or ImapMessageInfoCollection elements. The following code snippet shows you how to delete multiple messages.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-DeleteMultipleMessages-DeleteMultipleMessages.py" >}}
