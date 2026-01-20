---
title: List Supported POP3 Server Extensions
ArticleTitle: List Supported POP3 Server Extensions
type: docs
weight: 30
url: /python-net/list-pop3-server-extensions-python/
---


Aspose.Email provides a [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/) class that allows you to retrieve the supported extensions of a POP3 server, such as IDLE, UNSELECT, QUOTA, and more. Knowing which extensions are available is crucial for determining if specific functionalities can be utilized. The `get_capabilities()` method returns the types of supported extensions as a string array.

The following code sample demonstrates how to retrieve server extensions using Pop3Client for the Gmail server:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ListingServerExtensions-ListingServerExtensions.py" >}}
