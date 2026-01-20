---
title: List IMAP Server Extensions in Python
ArticleTitle: List IMAP Server Extensions
type: docs
weight: 40
url: /python-net/list-imap-server-extensions/
---


Aspose.Email [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) allows you to retrieve the server extensions supported by the mail server such as IDLE, UNSELECT, QUOTA, and others. This helps ensure the availability of specific features before performing operations that rely on them. The `get_capabilities()` method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class returns a list of supported IMAP extension types as strings. The following code snippet shows you how to retrieve the list of IMAP extensions:



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-IMAP-RetrievingServerExtensions-RetrievingServerExtensions.py" >}}
