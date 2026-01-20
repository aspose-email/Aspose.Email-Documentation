---
title: Enable SMTP Client Activity Logging
ArticleTitle: Enable SMTP Client Activity Logging
type: docs
weight: 30
url: /python-net/smtp-client-activity-logging/
---


Aspose.Email for Python via .NET provides built-in support for logging SMTP activity. This feature — commonly known as activity logging — allows developers to systematically track email transactions, events, or errors during the send process. It can be especially useful for debugging, auditing, or maintaining operational transparency in server-side applications.

The [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class offers the following properties to enable and configure activity logging:

- `log_file_name`: Specifies the full path and name of the log file.

- `use_date_in_log_file_name`: Determines whether the current date should be appended to the log file name, which is useful for creating daily logs.

The code sample below demonstrates how to enable SMTP activity logging in the programm code:

```py
import aspose.email as ae

# Initialize and configure the SMTP client
client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

# Set the log file name and enable/disable date in file name
client.log_file_name = "C:\Aspose.Email.Smtp.log"

# Set to True to append current date
client.use_date_in_log_file_name = False

# Prepare and send the email
eml = ae.MailMessage("from address", "to address", "this is a test subject", "this is a test body")
client.send(eml)
```
