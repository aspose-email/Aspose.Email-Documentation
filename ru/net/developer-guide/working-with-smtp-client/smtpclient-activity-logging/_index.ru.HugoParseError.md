---
title: Логирование активности SmtpClient
type: docs
weight: 26
url: /net/smtpclient-activity-logging/
---

Логирование активности используется для отладки, а также для сбора и анализа рабочей информации о клиенте SMTP.

## **Включение логирования активности с использованием файла appsettings.json**

> **_ПРИМЕЧАНИЕ:_** Этот вариант предпочтителен для приложений .NET Core.

Логирование в [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) можно включить с помощью следующих шагов и примеров кода:

1. Добавьте файл конфигурации appsettings.json в проект C#, если он ранее не был добавлен.
2. Убедитесь, что в файле проекта содержатся следующие строки в разделе ItemGroup.

   ```xml
      <Content Include="appsettings.json">
          <CopyToOutputDirectory>Always</CopyToOutputDirectory>
      </Content>
   ```

3. Затем добавьте следующее содержимое в файл appsettings.json.

   ```json
      {
        "SmtpDiagnosticLog": "smtp.log",
        "SmtpDiagnosticLog_UseDate": true
      }
   ```

Два вышеупомянутых свойства:

- **SmtpDiagnosticLog** - указывает относительный или абсолютный путь к файлу журнала.

- **SmtpDiagnosticLog_UseDate** - указывает, следует ли добавлять строковое представление текущей даты в имя файла журнала.

## **Включение логирования активности в коде программы**

Вы также можете включить логирование сразу в коде.

> **_ПРИМЕЧАНИЕ:_** даже если вы уже включили логирование, используя конфигурационные файлы, этот вариант будет применен.

Логирование в [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) можно включить с помощью следующих шагов и примеров кода:

1. Создайте [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
2. Установите путь к файлу журнала с помощью свойства [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/).
3. Установите свойство [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/), если это необходимо.

```cs
   using (var client = new SmtpClient("your smtp server"))
   {
       // Установите имя пользователя, пароль, порт и параметры безопасности
       client.Username = "your username";
       client.Password = "your password";
       client.Port = 465;
       client.SecurityOptions = SecurityOptions.SSLImplicit;
   
       // Установите путь к файлу журнала с помощью свойства LogFileName.
       client.LogFileName = @"C:\Aspose.Email.Smtp.log";
       
       // Установите свойство UseDateInLogFileName, если это необходимо.
       client.UseDateInLogFileName = false;
   
       var eml = new MailMessage("from address", "to address", "this is a test subject", "this is a test body");
   
       client.Send(eml);
   }
```

## **Включение логирования активности с использованием файла App.config**

Активность клиента SMTP может быть зарегистрирована путем изменения configSections в конфигурационном файле. Логирование диагностики можно выполнить с помощью следующих шагов:

1. Добавьте группу секций с названием "applicationSettings".
2. Добавьте секцию с названием "Aspose.Email.Properties.Settings".
3. Включите настройку с именем SmtpDiagonosticLog, где имя файла определяется в applicationSettings/Aspose.Email.Properties.Settings.

Вот пример приложения на основе форм, которое использует [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) для отправки электронной почты. Вся эта активность фиксируется путем изменения файла App.config. Создайте форму приложения с одной кнопкой. Добавьте следующий код для клика по кнопке:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}

4. Добавьте ссылку на Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
| :- |

5. Добавьте файл App.Config и измените его так, чтобы содержимое файла выглядело следующим образом:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}

- Для C# .NET используйте следующий вариант:

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
| :- |

- Для VB .NET используйте следующий вариант:

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
| :- | :- | :- |

|![todo:image_alt_text](utility-features-smtp-client_5.png)|
| :- |

6. Запустите код и затем проверьте папку отладки. Будет сгенерирован следующий файл.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
| :- |