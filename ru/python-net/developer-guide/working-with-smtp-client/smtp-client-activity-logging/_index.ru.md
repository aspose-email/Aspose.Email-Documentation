---
title: "Ведение журнала активности SmtpClient"
url: /ru/python-net/smtpclient-activity-logging/
weight: 30
type: docs
---


## **Включение ведения журнала активности в программном коде**

Aspose.Email позволяет систематически записывать или документировать действия, события или транзакции на протяжении времени. Также известное как ведение журнала активности, это можно осуществить с помощью следующих свойств класса [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class):

- Свойство 'log_file_name' получает или устанавливает имя файла журнала.
- Свойство 'use_date_in_log_file_name' получает или устанавливает значение, указывающее, следует ли использовать дату в имени файла журнала.

Приведенный ниже пример кода демонстрирует, как включить ведение журнала активности в программном коде:

```py
import aspose.email as ae

# Установите имя пользователя, пароль, порт и параметры безопасности
client = ae.clients.smtp.SmtpClient
client.host = "<HOST>"
client.username = "<USERNAME>"
client.password = "<PASSWORD>"
client.port = 587
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT

# Установите путь к файлу журнала с помощью свойства LogFileName
client.log_file_name = "C:\Aspose.Email.Smtp.log"

# Установите свойство UseDateInLogFileName, если это необходимо.
client.use_date_in_log_file_name = False

eml = ae.MailMessage("from address", "to address", "this is a test subject", "this is a test body")
client.send(eml)
```