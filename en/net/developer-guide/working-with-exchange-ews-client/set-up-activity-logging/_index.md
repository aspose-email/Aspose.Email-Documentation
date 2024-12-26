---
title: Enable Activity Logging for EWS Client in .NET Applications
ArticleTitle: Enabling Activity Logging in EWS Client for .NET
type: docs
weight: 160
url: /net/enable-activity-logging-in-ews-client-csharp/
---

Logging is used for debugging, as well as for collecting and analyzing working information about the application. Log files contain system information about the operation of the client application.

## **Set Up Logging Using appsettings.json File**

> **_NOTE:_** This option is preferred for .NET Core applications.

The following are the steps to enable logging in [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Add an appsettings.json configuration file to a C# project, if it has not been added before. Make sure that the project file contains the following lines in the ItemGroup section:

  ```xml
  <Content Include="appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
  </Content>
  ```

- Then, add the following content to the appsettings.json file.

  ```json
  {
    "EWSDiagnosticLog": "ews.log",
    "EWSDiagnosticLog_UseDate": true
  }
  ```

There are two properties:

- `EWSDiagnosticLog` - Specifies the relative or absolute path to the log file.
- `EWSDiagnosticLog_UseDate` - specifies whether to add a string representation of the current date to the log file name.

## **Set Up Logging in Programm Code**

You can also enable logging immediately in the code.

> **_NOTE:_** even if you have already enabled logging by using configuration files, this option will be applied.

The following are the steps to enable logging in EWSClient.

- Create an [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
- Set the path to the log file using the [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/logfilename/) property.
- Set the [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/usedateinlogfilename/) property if it is necessary.

```csharp
using (var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials))
{
  client.LogFileName = @"Aspose.Email.EWS.log";
  client.UseDateInLogFileName = false;
}
```

## **Set Up Logging using App.config File**

This option is suitable for applications where `app.config` is the preferred way for keeping the app configuration.

The following are the steps to enable logging in [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Add an application configuration file to a C# project, if it has not been added before.
- Add the following content to the configuration file.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
      <section name="Aspose.Email.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
    </sectionGroup>
  </configSections>
    <applicationSettings>
        <Aspose.Email.Properties.Settings>
            <setting name="EWSDiagnosticLog" serializeAs="String">
                <value>..\..\..\Log\Aspose.Email.EWS.log</value>
            </setting>
            <setting name="EWSDiagnosticLog_UseDate" serializeAs="String">
                <value>False</value>
            </setting>
        </Aspose.Email.Properties.Settings>
    </applicationSettings>
</configuration>
```

There are two setting sections:

- `EWSDiagnosticLog` - Specifies the relative or absolute path to the log file.
- `EWSDiagnosticLog_UseDate` - specifies whether to add a string representation of the current date to the log file name.
