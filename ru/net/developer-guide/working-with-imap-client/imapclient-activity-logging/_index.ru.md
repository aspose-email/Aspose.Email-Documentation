---
title: "Ведение журнала активности IMapClient"
url: /ru/net/imapclient-activity-logging/
weight: 90
type: docs
---

Ведение журнала активности используется для отладки, а также для сбора и анализа рабочей информации о клиенте IMAP.

## **Включите ведение журнала активности с помощью файла appsettings.json**

> **_NOTE:_** Этот вариант предпочтителен для приложений.NET Core.

Вход в систему [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) можно включить с помощью следующих шагов и примеров кода:

1. Добавьте файл конфигурации appsettings.json в проект C#, если он не был добавлен ранее.
2. Убедитесь, что файл проекта содержит следующие строки в разделе ItemGroup.

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

Вышеупомянутые два свойства:

- **ImapDiagnosticLog** - указывает относительный или абсолютный путь к файлу журнала.

- **ImapDiagnosticLog_UseDate** - указывает, следует ли добавить строковое представление текущей даты к имени файла журнала.

## **Включить ведение журнала активности в программном коде**

Вы также можете сразу включить логирование в коде.

> **_NOTE:_** даже если вы уже включили ведение журнала с помощью файлов конфигурации, эта опция будет применена.

Вход в систему [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) можно включить с помощью следующих шагов и примеров кода:

1. Создайте [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/).
2. Задайте путь к файлу журнала, используя [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Установите [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) имущество, если это необходимо.

```cs
   using (var client = new ImapClient("your imap server", 993, "your username", "your password"))
{
    // Set security mode
    client.SecurityOptions = SecurityOptions.Auto;

    // Задайте путь к файлу журнала, используя LogFileName property.
    client.LogFileName = @"C:\Aspose.Email.IMAP.log";

    // Установите UseDateInLogFileName имущество, если это необходимо.
    client.UseDateInLogFileName = false;
}
```

## **Включите ведение журнала активности с помощью файла App.config**

[ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) активность можно зарегистрировать, изменив ConfigSections в файле конфигурации. Ниже приведены шаги по ведению журнала диагностики:

1. Добавьте **sectionGroup** называется «Настройки приложения».
1. Добавьте **section** называется «Aspose.Email.Properties.Settings».
1. Включите настройку IMAPDiagonosticLog, где имя файла определено в поле **applicationSettings/Aspose.Email.Properties.Settings**.

Вот образец заявки, в котором используется [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) для обработки почты. Вся эта операция регистрируется путем изменения файла App.config.

- Создайте приложение на основе формы, нажав на него всего одну кнопку. Добавьте следующий пример кода для нажатия кнопки:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-IMAP-ImapClientActivityLogging-ImapClientActivityLogging.cs" >}}

- Добавьте ссылку на Aspose.Email.

|![todo:image_alt_text](imapclient-activity-logging_1.png)| |
|: - |: - |

- Теперь добавьте файл App.Config и измените его так, чтобы содержимое файла выглядело следующим образом:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ImapClientActivityLogging-ImapClientActivityLogging.xml" >}}

Для C#.NET используйте следующую опцию

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |
|: - |: - |
Для VB.NET используйте следующую опцию

|![todo:image_alt_text](imapclient-activity-logging_2.png)| |![todo:image_alt_text](imapclient-activity-logging_4.png)| |
|: - |: - |: - |: - |

|![todo:image_alt_text](imapclient-activity-logging_5.png)| |
|: - |: - |

- Запустите код и просмотрите папку Log. Будет создан следующий файл.

|![todo:image_alt_text](imapclient-activity-logging_6.png)| |
|: - |: - |
