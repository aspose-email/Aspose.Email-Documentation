---
title: Логирование активности ImapClient
type: docs
weight: 90
url: /net/imapclient-activity-logging/
---

Логирование активности используется для отладки, а также для сбора и анализа рабочей информации о клиенте IMAP.

## **Включение логирования активности с использованием файла appsettings.json**

> **_ПРИМЕЧАНИЕ:_** Этот вариант предпочтителен для приложений .NET Core.

Логирование в [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) можно включить, выполнив следующие шаги и примеры кода:

1. Добавьте файл конфигурации appsettings.json в проект C#, если он ранее не был добавлен.
2. Убедитесь, что файл проекта содержит следующие строки в секции ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Затем добавьте следующее содержимое в файл appsettings.json.

   ```json
      {
        "ImapDiagnosticLog": "imap.log",
        "ImapDiagnosticLog_UseDate": true
      }
   ```

Два упомянутых свойства:

- **ImapDiagnosticLog** - указывает относительный или абсолютный путь к файлу журнала.

- **ImapDiagnosticLog_UseDate** - указывает, нужно ли добавлять строковое представление текущей даты в имя файла журнала.

## **Включение логирования активности в коде программы**

Вы также можете включить логирование сразу в коде.

> **_ПРИМЕЧАНИЕ:_** даже если вы уже включили логирование с помощью файлов конфигурации, этот вариант будет применен.

Логирование в [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) можно включить, выполнив следующие шаги и примеры кода:

1. Создайте [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Установите путь к файлу журнала, используя свойство [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Установите свойство [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/), если это необходимо.

```cs
   using (var client = new ImapClient("your imap server", 993, "your username", "your password"))
{
    // Установите режим безопасности
    client.SecurityOptions = SecurityOptions.Auto;

    // Установите путь к файлу журнала, используя свойство LogFileName.
    client.LogFileName = @"C:\Aspose.Email.IMAP.log";

    // Установите свойство UseDateInLogFileName, если это необходимо.
    client.UseDateInLogFileName = false;
}
```

## **Включение логирования активности с использованием файла App.config**

Активность [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) может быть зарегистрирована, изменив секции configSections в файле конфигурации. Следующие шаги помогут выполнить диагностику логирования:

1. Добавьте **sectionGroup** с именем "applicationSettings".
1. Добавьте **section** с именем "Aspose.Email.Properties.Settings".
1. Включите настройку ImapDiagonosticLog, где имя файла определяется в **applicationSettings/Aspose.Email.Properties.Settings**.

Вот пример формы приложения, которая использует [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) для обработки почты. Вся эта активность регистрируется путем изменения файла App.config.

- Создайте приложение на основе формы с одной кнопкой. Добавьте следующий пример кода для обработки нажатия кнопки:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ImapClientActivityLogging-ImapClientActivityLogging.cs" >}}

- Добавьте ссылку на Aspose.Email.

|![todo:image_alt_text](imapclient-activity-logging_1.png)| |
| :- | :- |

- Теперь добавьте файл App.Config и измените его, чтобы содержимое файла было следующим:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ImapClientActivityLogging-ImapClientActivityLogging.xml" >}}

Для C# .NET используйте следующий вариант

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |
| :- | :- |
Для VB .NET используйте следующий вариант

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |![todo:image_alt_text](imapclient-activity-logging_4.png)| |
| :- | :- | :- | :- |

|![todo:image_alt_text](imapclient-activity-logging_5.png)| |
| :- | :- |

- Запустите код, а затем проверьте папку Журнала. Будет сгенерирован следующий файл.

|![todo:image_alt_text](imapclient-activity-logging_6.png)| |
| :- | :- |