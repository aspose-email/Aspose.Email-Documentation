---
title: "Ведение журнала активности Pop3Client"
url: /ru/net/pop3client-activity-logging/
weight: 40
type: docs
---

Ведение журнала активности используется для отладки, а также для сбора и анализа рабочей информации о клиенте POP3.

## **Включите ведение журнала активности с помощью файла appsettings.json**

> **_NOTE:_** Этот вариант предпочтителен для приложений.NET Core.

Вход в систему [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) можно включить с помощью следующих шагов и примеров кода:

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
        "Pop3DiagnosticLog": "Pop3.log",
        "Pop3DiagnosticLog_UseDate": true
      }
   ```

Вышеупомянутые два свойства:

- **Pop3DiagnosticLog** - указывает относительный или абсолютный путь к файлу журнала.

- **Pop3DiagnosticLog_UseDate** - указывает, следует ли добавить строковое представление текущей даты к имени файла журнала.

## **Включить ведение журнала активности в программном коде**

Вы также можете сразу включить логирование в коде.

> **_NOTE:_** даже если вы уже включили ведение журнала с помощью файлов конфигурации, эта опция будет применена.

Вход в систему [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) можно включить с помощью следующих шагов и примеров кода:

1. Создайте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Задайте путь к файлу журнала, используя [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Установите [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) имущество, если это необходимо.

```cs
   using (var client = new Pop3Client("your pop3 server", 995, "your username", "your password"))
{
    // Set security mode
    client.SecurityOptions = SecurityOptions.Auto;

    // Задайте путь к файлу журнала, используя LogFileName property.
    client.LogFileName = @"C:\Aspose.Email.Pop3.log";

    // Установите UseDateInLogFileName имущество, если это необходимо.
    client.UseDateInLogFileName = false;
}
```

## **Включите ведение журнала активности с помощью файла App.config**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) активность можно зарегистрировать, изменив ConfigSections в файле конфигурации. Ниже приведены шаги по ведению журнала диагностики:

1. Добавьте **sectionGroup** называется «Настройки приложения».
1. Добавьте **section** называется «Aspose.Email.Properties.Settings».
1. Включите настройку IMAPDiagonosticLog, где имя файла определено в поле **applicationSettings/Aspose.Email.Properties.Settings**.

Вот образец заявки, в котором используется [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) для обработки почты. Вся эта операция регистрируется путем изменения файла App.config.

- Создайте приложение на основе формы, нажав на него всего одну кнопку. Добавьте следующий пример кода для нажатия кнопки:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-Pop3ClientActivityLogging-Pop3ClientActivityLogging.cs" >}}

- Добавьте ссылку на Aspose.Email.
- Теперь добавьте файл App.Config и измените его так, чтобы содержимое файла выглядело следующим образом:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-Pop3ClientActivityLogging.config" >}}

Для C#.NET используйте следующую опцию

|![todo:image_alt_text](pop3client-activity-logging_1.png)|
|: - |
Для VB.NET используйте следующую опцию

|![todo:image_alt_text](pop3client-activity-logging_1.png)| |![todo:image_alt_text](pop3client-activity-logging_3.png)| |
|: - |: - |: - |: - |

|![todo:image_alt_text](pop3client-activity-logging_4.png)| |
|: - |: - |

- Запустите код и просмотрите папку Log. Будет создан следующий файл.

|![todo:image_alt_text](pop3client-activity-logging_5.png)| |
|: - |: - |
