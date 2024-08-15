---
title: SmtpClient Activity Logging
type: docs
weight: 30
url: /python-net/smtpclient-activity-logging/
---


## **Enable Activity Logging in Programm Code**

Aspose.Email makes it possible to systematically record or document activities, events, or transactions over a period of time. Also known as activity logging, it can be achieved with the following properties of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class:

- 'log_file_name' property gets or sets log file name.
- 'use_date_in_log_file_name'	gets or sets value which indicates if date has to be used in log file name.

The code sample below demonstrates how to enable activity logging in the programm code:

```py
import aspose.email as ae

# Set username, password, port, and security options
client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

# Set the path to the log file using the LogFileName property
client.log_file_name = "C:\Aspose.Email.Smtp.log"

# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False

eml = ae.MailMessage("from address", "to address", "this is a test subject", "this is a test body")
client.send(eml)
```