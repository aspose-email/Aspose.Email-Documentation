---
title: Utility Features - SMTP Client
ArticleTitle: Utility Features - SMTP Client
type: docs
weight: 30
url: /python-net/utility-features-smtp-client/
---


## **Listing Extension Servers using Smtp Client**
Aspose.Email's Pop3Client lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT,QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The GetCapabilities() method returns the supported extension types in the form of a string array.
### **Retrieving Server Extensions**
The following code snippet shows you how to retrieve server extensions.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Validate Mail Server Credentials Without Sending Email**

The 'validate_credentials()' method of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class is used to check the validity of the provided credentials by establishing a connection to the SMTP server. If the credentials are valid and the connection is successful, further actions could be performed. The following code sample can be used to verify the credentials provided for authentication with the SMTP server without sending an email:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000

if client.validate_credentials():
  # to do something
```
