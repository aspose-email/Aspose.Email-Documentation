---
title: Listing IMAP Server Extensions
type: docs
weight: 40
url: /python-net/listing-imap-server-extensions/
---


## **Listing Server Extensions**
Aspose.Email's ImapClient lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT,QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The GetCapabilities() method returns the supported extension types in the form of a string array. The following code snippet shows you how to retrieve extensions.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}
