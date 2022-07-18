---
title: ImapClient Activity Logging
type: docs
weight: 90
url: /net/imapclient-activity-logging/
---


[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient) activity can be logged by modifying the configSections in the config file. Following are the steps to perform diagnostics logging:

1. Add a **sectionGroup** called "applicationSettings".
1. Add a **section** called "Aspose.Email.Properties.Settings".
1. Include the setting ImapDiagonosticLog where the file name is defined in the **applicationSettings/Aspose.Email.Properties.Settings**.

Here is a sample form application which uses [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient) to process mail. This whole activity is logged by modifying the App.config file.

- Create a form based application with a single button on it. Add the following sample code for button's click:



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ImapClientActivityLogging-ImapClientActivityLogging.cs" >}}



- Add a reference to Aspose.Email.

|![todo:image_alt_text](imapclient-activity-logging_1.png)| |
| :- | :- |
- Now add the App.Config file and modify it so that the file contents are as follows:



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ImapClientActivityLogging-ImapClientActivityLogging.xml" >}}



For C# .NET use the following option

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |
| :- | :- |
For VB .NET use the following option

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |![todo:image_alt_text](imapclient-activity-logging_4.png)| |
| :- | :- | :- | :- |


|![todo:image_alt_text](imapclient-activity-logging_5.png)| |
| :- | :- |
- Run the code and then observe Log folder. The following file will be generated.

|![todo:image_alt_text](imapclient-activity-logging_6.png)| |
| :- | :- |

