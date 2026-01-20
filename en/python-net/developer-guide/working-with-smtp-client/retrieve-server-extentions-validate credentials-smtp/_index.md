---
title: Retrieve SMTP Server Extensions | Validate SMTP Credentials
ArticleTitle: Retrieve SMTP Server Extensions & Validate Mail Server Credentials
type: docs
weight: 30
url: /python-net/retrieve-smtp-server-extensions-validate-mail-server-credentials/
---

Aspose.Email [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/) class provides advanced features beyond sending emails. It enables developers to:

- **Retrieve supported server extensions** such as IDLE, UNSELECT, QUOTA, etc., to ensure compatibility before using certain features.

- **Validate SMTP credentials** without actually sending an email, which is useful for login verification and connection testing.

## **Retrieve SMTP Server Extensions**

Before using specific SMTP features, it’s helpful to check which extensions the mail server supports. The `get_capabilities()` method retrieves these as a list of strings.

The following code snippet shows you how to retrieve server extensions:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-RetrieveSMTPServerExtensions-RetrieveSMTPServerExtensions.py" >}}

## **Validate SMTP Credentials Without Sending an Email**

To check if the provided credentials are valid — without sending a test message — you can use the `validate_credentials()` method of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class. This is useful for authentication checks and system diagnostics.

The following code sample can be used to verify login credentials provided for authentication with the SMTP server without sending an email:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("Url", port, "username", "password", ae.clients.SecurityOptions.AUTO)
client.timeout = 4000   # Set timeout in milliseconds

# Validate login
if client.validate_credentials():
    print("Credentials are valid.")
else:
    print("Invalid credentials or unable to connect.")
```
