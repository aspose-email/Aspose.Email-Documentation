---
title: Utility Features - IMAP Client
type: docs
weight: 100
url: /net/utility-features-imap-client/
---

## **Validate Mail Server Credentials**

Aspose.Email API enables the validation of mail server credentials without sending an email. [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentials) method is responsible for verifying the authenticity and validity of the provided email credentials, which are normally used to authenticate when connecting to the server.

It verifies that the email credentials provided, such as username and password, are valid and that it is possible for the client to establish a successful connection to the server. This credential verification helps ensure that the client can securely access the email account and perform various operations, such as receiving email.

```cs
using (ImapClient client = new ImapClient(server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

For an asynchronous operation, there is also a version of the method [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/validatecredentialsasync).
