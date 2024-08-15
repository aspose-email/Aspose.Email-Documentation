---
title: "Ведение журнала активности SMTP-клиента"
url: /ru/net/smtpclient-activity-logging/
weight: 26
type: docs
---

Ведение журнала активности используется для отладки, а также для сбора и анализа рабочей информации о SMTP-клиенте.

## **Включите ведение журнала активности с помощью файла appsettings.json**

> **_NOTE:_** Этот вариант предпочтителен для приложений.NET Core.

Вход в систему [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) можно включить с помощью следующих шагов и примеров кода:

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
        "SmtpDiagnosticLog": "smtp.log",
        "SmtpDiagnosticLog_UseDate": true
      }
   ```

Вышеупомянутые два свойства:

- **SmtpDiagnosticLog** - указывает относительный или абсолютный путь к файлу журнала.

- **SmtpDiagnosticLog_UseDate** - указывает, следует ли добавить строковое представление текущей даты к имени файла журнала.

## **Включить ведение журнала активности в программном коде**

Вы также можете сразу включить логирование в коде.

> **_NOTE:_** даже если вы уже включили ведение журнала с помощью файлов конфигурации, эта опция будет применена.

Вход в систему [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) можно включить с помощью следующих шагов и примеров кода:

1. Создайте [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).
2. Задайте путь к файлу журнала, используя [LogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/logfilename/) property.
3. Установите [UseDateInLogFileName](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/usedateinlogfilename/) имущество, если это необходимо.

```cs
   using (var client = new SmtpClient("your smtp server"))
   {
       // Set username, password, port, and security options
       client.Username = "your username";
       client.Password = "your password";
       client.Port = 465;
       client.SecurityOptions = SecurityOptions.SSLImplicit;
  
       // Задайте путь к файлу журнала, используя LogFileName property.
       client.LogFileName = @"C:\Aspose.Email.Smtp.log";
      
       // Установите UseDateInLogFileName имущество, если это необходимо.
       client.UseDateInLogFileName = false;
  
       var eml = new MailMessage("from address", "to address", "this is a test subject", "this is a test body");
  
       client.Send(eml);
   }
```

## **Включите ведение журнала активности с помощью файла App.config**

Активность SMTP-клиента можно зарегистрировать, изменив ConfigSections в файле конфигурации. Ведение журнала диагностики можно выполнить следующим образом:

1. Добавьте группу секций под названием «Настройки приложения».
2. Добавьте раздел под названием «Aspose.Email.Properties.Settings».
3. Включите настройку под названием SMTPDiagonosticLog, где имя файла определено в файле ApplicationSettings/Aspose.email.properties.settings

Вот образец приложения на основе формы, в котором используются [SmtpClient](https://apireference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient) чтобы отправить электронное письмо. Все это действие регистрируется путем изменения файла App.config. Создайте приложение-форму, нажав на нее всего одну кнопку. Добавьте следующий код для нажатия кнопки:

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SMTPClientActivityLogging-SMTPClientActivityLogging.cs" >}}

4. Добавьте ссылку на Aspose.Email.

|![todo:image_alt_text](utility-features-smtp-client_1.png)|
|: - |

5. Добавьте файл App.Config и измените его таким образом, чтобы содержимое файла выглядело следующим образом

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-App-SMTPClientActivityLogging.config" >}}

- Для C#.NET используйте следующую опцию

|![todo:image_alt_text](utility-features-smtp-client_2.png)|
|: - |

- Для VB.NET используйте следующую опцию

|![todo:image_alt_text](utility-features-smtp-client_2.png)| |![todo:image_alt_text](utility-features-smtp-client_4.png)|
|: - |: - |: - |

|![todo:image_alt_text](utility-features-smtp-client_5.png)|
|: - |

6. Запустите код и просмотрите папку debug. Будет создан следующий файл.

|![todo:image_alt_text](utility-features-smtp-client_6.png)|
|: - |
