---
title: "Ведение журнала активности Pop3Client"
url: /ru/net/pop3client-activity-logging/
weight: 40
type: docs
---

Ведение журнала активности используется для отладки, а также для сбора и анализа рабочей информации о клиенте POP3.

## **Включение ведения журнала активности с помощью файла appsettings.json**

> **_ПРИМЕЧАНИЕ:_** Этот вариант предпочтителен для приложений .NET Core.

Ведение журнала в [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) можно включить с помощью следующих шагов и образцов кода:

1. Добавьте конфигурационный файл appsettings.json в проект C#, если он не был добавлен ранее.
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

Два вышеупомянутых свойства:

- **Pop3DiagnosticLog** - указывает относительный или абсолютный путь к файлу журнала.

- **Pop3DiagnosticLog_UseDate** - указывает, добавлять ли строковое представление текущей даты к имени файла журнала.

## **Включение ведения журнала активности в коде программы**

Вы также можете включить ведение журнала сразу в коде.

> **_ПРИМЕЧАНИЕ:_** даже если вы уже включили ведение журнала с помощью конфигурационных файлов, этот вариант будет применен.

Ведение журнала в [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) можно включить с помощью следующих шагов и образцов кода:

1. Создайте [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/).
2. Установите путь к файлу журнала с помощью свойства [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Установите свойство [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) при необходимости.

```cs
   using (var client = new Pop3Client("your pop3 server", 995, "your username", "your password"))
{
    // Установите режим безопасности
    client.SecurityOptions = SecurityOptions.Auto;

    // Установите путь к файлу журнала с помощью свойства LogFileName.
    client.LogFileName = @"C:\Aspose.Email.Pop3.log";

    // Установите свойство UseDateInLogFileName при необходимости.
    client.UseDateInLogFileName = false;
}
```

## **Включение ведения журнала активности с помощью файла App.config**

Активность [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) может быть зарегистрирована путем изменения секций config в конфигурационном файле. Следующие шаги необходимо выполнить для ведения диагностического журнала:

1. Добавьте **sectionGroup** под названием "applicationSettings".
1. Добавьте **section** под названием "Aspose.Email.Properties.Settings".
1. Включите настройку ImapDiagonosticLog, где имя файла определяется в **applicationSettings/Aspose.Email.Properties.Settings**.

Вот пример формы приложения, которая использует [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) для обработки почты. Вся эта активность записывается путем изменения файла App.config.

- Создайте приложение на основе формы с одной кнопкой. Добавьте следующий пример кода для обработки нажатия кнопки:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-Pop3ClientActivityLogging-Pop3ClientActivityLogging.cs" >}}

- Добавьте ссылку на Aspose.Email.
- Теперь добавьте файл App.Config и измените его так, чтобы содержимое файла было следующим:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-Pop3ClientActivityLogging.config" >}}

Для C# .NET используйте следующий вариант

|![todo:image_alt_text](pop3client-activity-logging_1.png)|
| :- |
Для VB .NET используйте следующий вариант

|![todo:image_alt_text](pop3client-activity-logging_1.png)| |![todo:image_alt_text](pop3client-activity-logging_3.png)| |
| :- | :- | :- | :- |

|![todo:image_alt_text](pop3client-activity-logging_4.png)| |
| :- | :- |

- Запустите код и затем проверьте папку Log. Будет создан следующий файл.

|![todo:image_alt_text](pop3client-activity-logging_5.png)| |
| :- | :- |