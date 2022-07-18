---
title: SmtpClient Activity Logging
type: docs
weight: 26
url: /net/smtpclient-activity-logging/
---


## **SMTP Client Activity Logging**
SMTP client activity can be logged by modifying the configSections in the config file. Following are the steps to perform diagnostics logging:

- Add a sectionGroup called "applicationSettings".
- Add a section called "Aspose.Email.Properties.Settings".
- Include the setting with the name SmtpDiagonosticLog where the file name is defined in the applicationSettings/Aspose.Email.Properties.Settings

Here is a sample form based application which uses [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) to send an email. This whole activity is logged by modifying the App.config file. Create a form application with a single button on it. Add the following code for button’s click:



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}



- Add reference to Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
| :- |
- Add the App.Config file and modify it in such a way that file contents are as follows



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}



- For C# .NET use the following option

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
| :- |
- For VB .NET use the following option

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
| :- | :- | :- |


|![todo:image_alt_text](utility-features-smtp-client_5.png)|
| :- |
- Run the code and then observe the debug folder. The following file will be generated.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
| :- |
