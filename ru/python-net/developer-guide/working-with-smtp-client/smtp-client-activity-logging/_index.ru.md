---
title: "Ведение журнала активности SMTP-клиента"
url: /ru/python-net/smtpclient-activity-logging/
weight: 30
type: docs
---


## **Включить ведение журнала активности в программном коде**

Aspose.Email позволяет систематически записывать или документировать действия, события или транзакции в течение определенного периода времени. Это явление, также известное как ведение журнала активности, может быть достигнуто с помощью следующих свойств [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class:

- Свойство log_file_name получает или задает имя файла журнала.
- 'use_date_in_log_file_name' получает или задает значение, указывающее, нужно ли использовать дату в имени файла журнала.

В приведенном ниже примере кода показано, как включить ведение журнала активности в программном коде:

```py
import aspose.email as ae

# Set username, password, port, and security options
client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

# Set the path to the log file using the LogFileName property
client.log_file_name = "C:\Aspose.Email.Smtp.log"

# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False

eml = ae.MailMessage("from address", "to address", "this is a test subject", "this is a test body")
client.send(eml)
```