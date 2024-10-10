---
title: "Настройка журналирования активности"
url: /ru/net/set-up-activity-logging/
weight: 41
type: docs
---

Журналирование используется для отладки, а также для сбора и анализа рабочей информации о приложении. Файлы журналов содержат системную информацию о работе клиентского приложения.

## **Включение журналирования активности с использованием файла appsettings.json**

> **_ПРИМЕЧАНИЕ:_** Этот вариант предпочтителен для приложений .NET Core.

Следующие шаги позволяют включить журналирование в [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Добавьте файл конфигурации appsettings.json в проект C#, если он еще не был добавлен. Убедитесь, что файл проекта содержит следующие строки в секции ItemGroup:

  ```xml
  <Content Include="appsettings.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
  </Content>
  ```

- Затем добавьте следующий контент в файл appsettings.json.

  ```json
  {
    "EWSDiagnosticLog": "ews.log",
    "EWSDiagnosticLog_UseDate": true
  }
  ```

Существует два свойства:

- `EWSDiagnosticLog` - Указывает относительный или абсолютный путь к файлу журнала.
- `EWSDiagnosticLog_UseDate` - указывает, следует ли добавлять строковое представление текущей даты к имени файла журнала.

## **Включение журналирования активности в коде программы**

Вы также можете немедленно включить журналирование в коде.

> **_ПРИМЕЧАНИЕ:_** даже если вы уже включили журналирование с использованием файлов конфигурации, этот вариант будет применен.

Следующие шаги позволяют включить журналирование в EWSClient.

- Создайте [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).
- Установите путь к файлу журнала с помощью свойства [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/logfilename/).
- Установите свойство [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients.exchange/exchangeclientbase/usedateinlogfilename/), если это необходимо.

```csharp
using (var client = EWSClient.GetEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", credentials))
{
  client.LogFileName = @"Aspose.Email.EWS.log";
  client.UseDateInLogFileName = false;
}
```

## **Включение журналирования активности с использованием файла App.config**

Этот вариант подходит для приложений, где `app.config` является предпочтительным способом хранения конфигурации приложения.

Следующие шаги позволяют включить журналирование в [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/).

- Добавьте файл конфигурации приложения в проект C#, если он еще не был добавлен.
- Добавьте следующий контент в файл конфигурации.

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

Существует два раздела настроек:

- `EWSDiagnosticLog` - Указывает относительный или абсолютный путь к файлу журнала.
- `EWSDiagnosticLog_UseDate` - указывает, следует ли добавлять строковое представление текущей даты к имени файла журнала.