---
title: Listing Server Extensions using Pop3Client
type: docs
weight: 30
url: /net/listing-server-extensions-using-pop3client/
---


Aspose.Email's [Pop3Client](https://reference.aspose.com/net/email/aspose.email.clients.pop3/pop3client) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [GetCapabilities()](https://reference.aspose.com/net/email/aspose.email.clients/emailclient/methods/getcapabilities) method returns the supported extension types in the form of a string array.
## **Retrieving Server Extensions**
The following code sample demonstrates retrieving server extensions using ImapClient for Gmail server.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}
