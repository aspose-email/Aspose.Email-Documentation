---
title: Utility Features - POP3 Client
ArticleTitle: Utility Features - POP3 Client
type: docs
weight: 30
url: /python-net/utility-features-pop3-client/
---

## **Validate Mail Server Credentials**

Aspose.Email provides the 'validate_credentials()' method of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class to verify the credentials (username and password) provided by the user for accessing a POP3 email server. This method ensures that the user's login credentials are accurate and valid, allowing them to successfully authenticate and access their email account using the POP3 protocol. If the credentials provided are incorrect, the method may return an error or throw an exception, indicating that the login process has failed.

The code snippet below demonstrates the verification method provided by the API:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 40000
if client.validate_credentials():
# to do something
```
