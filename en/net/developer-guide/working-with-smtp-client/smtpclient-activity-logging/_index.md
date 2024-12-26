---
title: Enable SMTP Activity Logging in .NET Using appsettings.json
ArticleTitle: Set Up SMTP Client Activity Logging in .NET Core
type: docs
weight: 26
url: /net/enable-smtp-activity-logging/
---

Activity logging is used for debugging, as well as for collecting and analyzing working information about the SMTP client.

## **Enable Activity Logging**

### **Use appsettings.json File to Enable Activity Logging**

> **_NOTE:_** This option is preferred for .NET Core applications.

Logging in [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) can be enabled with the following steps and code samples:

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
        "SmtpDiagnosticLog": "smtp.log",
        "SmtpDiagnosticLog_UseDate": true
      }
   ```

The two properties mentioned above are:

- **SmtpDiagnosticLog** - specifies the relative or absolute path to the log file.

- **SmtpDiagnosticLog_UseDate** - specifies whether to add a string representation of the current date to the log file name.

### **Enable Activity Logging in Programm Code**

You can also enable logging immediately in the code. 

> **_NOTE:_** even if you have already enabled logging by using configuration files, this option will be applied.

Logging in [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) can be enabled with the following steps and code samples:

1. Create an [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
2. Set the path to the log file using the [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Set the [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) property if it is necessary.

```cs
   using (var client = new SmtpClient("your smtp server"))
   {
       // Set username, password, port, and security options
       client.Username = "your username";
       client.Password = "your password";
       client.Port = 465;
       client.SecurityOptions = SecurityOptions.SSLImplicit;
   
       // Set the path to the log file using the LogFileName property.
       client.LogFileName = @"C:\Aspose.Email.Smtp.log";
       
       // Set the UseDateInLogFileName property if it is necessary.
       client.UseDateInLogFileName = false;
   
       var eml = new MailMessage("from address", "to address", "this is a test subject", "this is a test body");
   
       client.Send(eml);
   }
```

### **Use App.config File to Enable Activity Logging**

SMTP client activity can be logged by modifying the configSections in the config file. Diagnostics logging can be performed with the following steps:

1. Add a sectionGroup called "applicationSettings".
2. Add a section called "Aspose.Email.Properties.Settings".
3. Include the setting with the name SmtpDiagonosticLog where the file name is defined in the applicationSettings/Aspose.Email.Properties.Settings

Here is a sample form based application which uses [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) to send an email. This whole activity is logged by modifying the App.config file. Create a form application with a single button on it. Add the following code for button’s click:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}

4. Add reference to Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
| :- |

5. Add the App.Config file and modify it in such a way that file contents are as follows

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}

- For C# .NET use the following option

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
| :- |

- For VB .NET use the following option

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
| :- | :- | :- |

|![todo:image_alt_text](utility-features-smtp-client_5.png)|
| :- |

6. Run the code and then observe the debug folder. The following file will be generated.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
| :- |
