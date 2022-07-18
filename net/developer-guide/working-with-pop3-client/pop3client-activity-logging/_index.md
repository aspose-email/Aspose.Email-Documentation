---
title: Pop3Client Activity Logging
type: docs
weight: 40
url: /net/pop3client-activity-logging/
---


[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) activity can be logged by modifying the configSections in the config file. Following are the steps to perform diagnostics logging:

1. Add a **sectionGroup** called "applicationSettings".
1. Add a **section** called "Aspose.Email.Properties.Settings".
1. Include the setting ImapDiagonosticLog where the file name is defined in the **applicationSettings/Aspose.Email.Properties.Settings**.

Here is a sample form application which uses [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client) to process mail. This whole activity is logged by modifying the App.config file.

- Create a form based application with a single button on it. Add the following sample code for button's click:



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-Pop3ClientActivityLogging-Pop3ClientActivityLogging.cs" >}}



- Add a reference to Aspose.Email.
- Now add the App.Config file and modify it in so that the file contents are as follows:



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-Pop3ClientActivityLogging.config" >}}



For C# .NET use the following option

|![todo:image_alt_text](pop3client-activity-logging_1.png)|
| :- |
For VB .NET use the following option

|![todo:image_alt_text](pop3client-activity-logging_1.png)| |![todo:image_alt_text](pop3client-activity-logging_3.png)| |
| :- | :- | :- | :- |


|![todo:image_alt_text](pop3client-activity-logging_4.png)| |
| :- | :- |
- Run the code and then observe the Log folder. The following file will be generated.

|![todo:image_alt_text](pop3client-activity-logging_5.png)| |
| :- | :- |

