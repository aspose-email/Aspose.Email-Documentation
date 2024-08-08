---
title: Listing Server Extensions using Pop3Client
type: docs
weight: 30
url: /python-net/listing-server-extensions-using-pop3client/
---

## **Listing Server Extensions using Pop3Client**
Aspose.Email's Pop3Client lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT,QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The GetCapabilities() method returns the supported extension types in the form of a string array.
### **Retrieving Server Extensions**
The following code sample demonstrates retrieving server extensions using ImapClient for Gmail server.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}
