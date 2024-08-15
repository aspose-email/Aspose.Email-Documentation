---
title: Utility Features - POP3 Client
type: docs
weight: 10
url: /net/utility-features-pop3-client/
---

## **Validate Mail Server Credentials**

The [ValidateCredentials](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentials) method of Aspose.Email API makes the validation of mail server credentials possible without sending an email. This method is responsible for verifying the authenticity and validity of the provided email credentials, being used for authentication when connecting to the server.

It verifies that the email credentials, such as username and password, are valid and that it is possible for the client to establish a successful connection to the server. This verification of credentials helps ensure that the client can securely access the email account and perform various operations, such as receiving email.

```cs
using (Pop3Client client = new Pop3Client(server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto))
{
    client.Timeout = 4000;
   
    if (client.ValidateCredentials())
    {
        //to do something
    }
}
```

To perform an asynchronous operation, there is also a version of the method [ValidateCredentialsAsync](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/validatecredentialsasync/).
