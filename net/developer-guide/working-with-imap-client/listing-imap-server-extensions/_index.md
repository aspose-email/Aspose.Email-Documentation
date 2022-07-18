---
title: Listing IMAP Server Extensions
type: docs
weight: 80
url: /net/listing-imap-server-extensions/
---


Aspose.Email's [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/methods/getcapabilities) method returns the supported extension types in the form of a string array. The following code snippet shows you how to retrieve extensions.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-RetreivingServerExtensions-RetreivingServerExtensions.cs" >}}
