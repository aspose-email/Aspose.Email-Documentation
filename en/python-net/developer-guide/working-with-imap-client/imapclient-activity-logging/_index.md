---
title: ImapClient Activity Logging in Python
ArticleTitle: ImapClient Activity Logging in Python
type: docs
weight: 40
url: /python-net/imapclient-activity-logging/
---


## **Enable Activity Logging**

Activity logging involves recording server connections, transmission details of messages sent and received, error messages during email processing, and any other actions performed by the client or server. To track IMAP client activity and interactions with the server, use the following code sample which uses the 'log_file_name' property of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class to log the information to the specified log file:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```
