---
title: Pop3Client Activity Logging
type: docs
weight: 40
url: /net/pop3client-activity-logging/
---

Activity logging is used for debugging, as well as for collecting and analyzing working information about the POP3 client.

## **Enable Activity Logging using appsettings.json File**

> **_NOTE:_** This option is preferred for .NET Core applications.

Logging in [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) can be enabled with the following steps and code samples:

1. Add an appsettings.json configuration file to a C# project, if it has not been added before. 
2. Make sure that the project file contains the following lines in the ItemGroup section.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Then, add the following content to the appsettings.json file.

   ```json
      {
        "Pop3DiagnosticLog": "Pop3.log",
        "Pop3DiagnosticLog_UseDate": true
      }
   ```

The two properties mentioned above are:

- **Pop3DiagnosticLog** - specifies the relative or absolute path to the log file.

- **Pop3DiagnosticLog_UseDate** - specifies whether to add a string representation of the current date to the log file name.

## **Enable Activity Logging in Programm Code**

You can also enable logging immediately in the code. 

> **_NOTE:_** even if you have already enabled logging by using configuration files, this option will be applied.

Logging in [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) can be enabled with the following steps and code samples:

1. Create an [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Set the path to the log file using the [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Set the [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) property if it is necessary.

```cs
   using (var client = new Pop3Client("your pop3 server", 995, "your username", "your password"))
{
    // Set security mode
    client.SecurityOptions = SecurityOptions.Auto;

    // Set the path to the log file using the LogFileName property.
    client.LogFileName = @"C:\Aspose.Email.Pop3.log";

    // Set the UseDateInLogFileName property if it is necessary.
    client.UseDateInLogFileName = false;
}
```

## **Enable Activity Logging using App.config File**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) activity can be logged by modifying the configSections in the config file. Following are the steps to perform diagnostics logging:

1. Add a **sectionGroup** called "applicationSettings".
1. Add a **section** called "Aspose.Email.Properties.Settings".
1. Include the setting ImapDiagonosticLog where the file name is defined in the **applicationSettings/Aspose.Email.Properties.Settings**.

Here is a sample form application which uses [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) to process mail. This whole activity is logged by modifying the App.config file.

- Create a form based application with a single button on it. Add the following sample code for the button click:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-Pop3ClientActivityLogging-Pop3ClientActivityLogging.cs" >}}

- Add a reference to Aspose.Email.
- Now add the App.Config file and modify it so that the file contents are as follows:

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
