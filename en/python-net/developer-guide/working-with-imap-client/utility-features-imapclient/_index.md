---
title: Utility Features for IMAP Client in Python
ArticleTitle: Utility Features for IMAP Client in Python
type: docs
weight: 40
url: /python-net/utility-features-imap-client/
---


## **Validate Mail Server Credentials**

To establish a secure connection to an IMAP server before undertaking further actions, the user credentials are checked and validated. The 'validate_credentials' method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class helps to check if the provided username and password are correct. If the credentials are indeed valid, the client can successfully authenticate with the IMAP server. The following code sample shows how to implement this method into your project:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # To do something
```
