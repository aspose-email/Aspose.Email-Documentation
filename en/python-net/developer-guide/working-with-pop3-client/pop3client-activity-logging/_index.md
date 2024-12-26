---
title: Pop3Client Activity Logging
ArticleTitle: Pop3Client Activity Logging
type: docs
weight: 40
url: /python-net/pop3client-activity-logging/
---

## **Enable Activity Logging in Programm Code**

Activity logging involves monitoring and recording the interactions and operations performed by users and mail clients when accessing and managing emails from a POP3 server. The enabled activity logging allows you to troubleshoot email-related issues, maintain security, and ensure compliance with data retention and privacy regulations. 

The following code sample demonstrates how to enable activity logging with Python API: 

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.Pop3.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```
