---
title: "Настроить ведение журнала активности"
url: /ru/net/set-up-activity-logging/
weight: 41
type: docs
---

Ведение журнала используется для отладки, а также для сбора и анализа рабочей информации о приложении. Файлы журнала содержат системную информацию о работе клиентского приложения.

## **Включите ведение журнала активности с помощью файла appsettings.json**

> **_NOTE:_** Этот вариант предпочтителен для приложений.NET Core.

Ниже приведены шаги, чтобы включить вход в систему [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Добавьте файл конфигурации appsettings.json в проект C#, если он не был добавлен ранее. Убедитесь, что файл проекта содержит следующие строки в разделе ItemGroup:

  ```xml
  <Content Include="appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
  </Content>
  ```

- Затем добавьте следующее содержимое в файл appsettings.json.

  ```json
  {
    "EWSDiagnosticLog": "ews.log",
    "EWSDiagnosticLog_UseDate": true
  }
  ```

Есть два свойства:

- `EWSDiagnosticLog` - Указывает относительный или абсолютный путь к файлу журнала.
- `EWSDiagnosticLog_UseDate` - указывает, следует ли добавить строковое представление текущей даты к имени файла журнала.

## **Включить ведение журнала активности в программном коде**

Вы также можете сразу включить логирование в коде.

> **_NOTE:_** даже если вы уже включили ведение журнала с помощью файлов конфигурации, эта опция будет применена.

Ниже приведены шаги, чтобы включить логирование в EWSClient.

- Создайте [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
- Задайте путь к файлу журнала, используя [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/logfilename/) property.
- Установите [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/usedateinlogfilename/) имущество, если это необходимо.

```csharp
using (var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials))
{
  client.LogFileName = @"Aspose.Email.EWS.log";
  client.UseDateInLogFileName = false;
}
```

## **Включите ведение журнала активности с помощью файла App.config**

Этот вариант подходит для приложений, где `app.config` является предпочтительным способом сохранения конфигурации приложения.

Ниже приведены шаги, чтобы включить вход в систему [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Добавьте файл конфигурации приложения в проект C#, если он не был добавлен ранее.
- Добавьте следующее содержимое в файл конфигурации.

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

Есть два раздела настроек:

- `EWSDiagnosticLog` - Указывает относительный или абсолютный путь к файлу журнала.
- `EWSDiagnosticLog_UseDate` - указывает, следует ли добавить строковое представление текущей даты к имени файла журнала.
