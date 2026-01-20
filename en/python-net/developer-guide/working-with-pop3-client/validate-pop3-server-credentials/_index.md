---
title: Validate POP3 Server Credentials in Python
ArticleTitle: Validate POP3 Server Credentials
type: docs
weight: 30
url: /python-net/validate-pop3-server-credentials-python/
---


Aspose.Email provides the `validate_credentials()` method of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class to verify the user's login credentials (username and password) for a POP3 email server. This method ensures that the credentials are valid, allowing successful authentication and access to the mailbox using the POP3 protocol. If the credentials are incorrect, the method returns 'False' or raises an exception, indicating authentication failure.

The code snippet below demonstrates how to validate POP3 server credentials using the Aspose.Email API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```
