---
title: "Подключение к SMTP-серверу"
url: /ru/python-net/connecting-to-smtp-server/
weight: 10
type: docs
---


## **Подключение SMTP-сервера с поддержкой SSL**
При подключении к SMTP-серверу с поддержкой SSL необходимо задать следующие свойства.

- SecurityOptions
- Port

В приведенных ниже примерах мы покажем, как:

1. Задайте имя пользователя.
1. Установите пароль.
1. Настройте порт.
1. Задайте параметр безопасности.

В следующем фрагменте кода показано, как подключить SMTP-сервер с поддержкой SSL.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SSLEnabledSMTPServer-SSLEnabledSMTPServer.py" >}}

### **Установите тайм-аут для приветственного ответа от сервера**

Чтобы повысить эффективность работы почтовых клиентов, разработчики часто используют свойство timeout, чтобы ограничить продолжительность длительных процессов. Однако указание слишком больших интервалов для этого свойства может затруднить выполнение операций, требующих длительного времени обработки. Заметным сценарием является установление соединения, когда использование только свойства Timeout может привести к увеличению времени соединения.

В некоторых случаях почтовый клиент может использовать автоматический режим для установления соединения, систематически переключаясь между различными параметрами соединения до тех пор, пока соединение не будет установлено успешно. Серверы SMTP, IMAP и POP3 после успешного инициирования соединения отправляют клиенту строку приветствия. Примечательно, что серверы могут использовать неявные или явные (START TLS) методы инициирования соединения SSL/TLS.

Потенциальная проблема возникает в случае несоответствия режима соединения между сервером и клиентом. Например, если сервер ожидает неявного SSL-соединения, а клиент пытается установить незащищенное или явно SSL-соединение, сервер воздерживается от отправки строки приветствия. В результате пользователи вынуждены долго ждать истечения тайм-аута, что заставляет клиента перейти к следующему варианту подключения.

Для решения этой проблемы разработчики могут использовать свойство greeting_timeout в [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) класс. Это свойство позволяет указать тайм-аут (в миллисекундах) именно для строки приветствия, сводя к минимуму время, необходимое для автоматического установления соединения. Включив свойство greeting_timeout, разработчики могут оптимизировать процессы подключения и обеспечить более отзывчивый и эффективный почтовый клиент.

В следующем примере кода показано, как реализовать свойство в проекте:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("localhost", 25, "username", "password")
client.greeting_timeout = 4000
```
## **Отправка электронного письма через прокси-сервер Socks**

Aspose.Email обеспечивает поддержку версий 4, 4a и 5 прокси-протокола SOCKS. В следующем примере кода показано, как отправить электронное письмо с помощью SMTP с помощью прокси-сервера SOCKS:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("smtp.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.SSL_IMPLICIT
# proxy address
proxy_address = "192.168.203.142"
#proxy port
proxy_port = 1080
socks_proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = socks_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"))
```

## **Подключение к серверу через прокси-сервер HTTP**

В приведенном ниже примере кода показано использование прокси-сервера HTTP для отправки электронной почты через SMTP-сервер:

```py
import aspose.email as ae

http_proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.smtp.SmtpClient("host", 587, "username", "password")
client.proxy = http_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Body"))
```

## **Подключение к серверу с использованием поддерживаемого метода аутентификации**

Чтобы установить безопасное и успешное соединение с сервером для отправки электронной почты, клиент может выбрать поддерживаемый метод аутентификации в зависимости от возможностей сервера. Aspose.Email предоставляет свойства, возвращающие списки поддерживаемых методов аутентификации:

- Свойство supported_authentication получает список типов аутентификации, поддерживаемых сервером
- Свойство allowed_authentication получает или задает список типов аутентификации, разрешенных пользователем

Используя эти свойства, разработчики могут обеспечить совместимость SMTP-клиента и сервера с точки зрения поддерживаемых методов аутентификации и установить соединение с SMTP-сервером. В следующем фрагменте кода приведен пример использования свойства allowed_authentication в проекте:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.LOGIN
```

## **Как установить тайм-аут для почтовых операций**

Настройка тайм-аута может быть важна для эффективной передачи данных по сети. Свойство «тайм-аут» [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) класс используется для указания максимального времени (в миллисекундах) ожидания ответа от SMTP-сервера. Это свойство позволяет пользователю контролировать время, в течение которого клиент будет ждать ответа сервера на определенную операцию, например подключение или отправку команды. Если ответ сервера превышает указанное время, клиент выдаст исключение, указывающее на ошибку тайм-аута. Это помогает управлять поведением клиента при взаимодействии с сервером, гарантируя, что клиент не зависает на неопределенный срок, если сервер не ответит своевременно. Используйте следующий фрагмент кода, чтобы установить время ожидания ответа сервера:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
# 60 seconds
client.timeout = 60000
```

## **Использование криптографических протоколов с SMTP-клиентом**

Aspose.Email поддерживает криптографические протоколы SSL (устаревшие) и TLS для обеспечения безопасности связи. Для защиты обмена данными между приложением и почтовыми серверами можно включить криптографическое шифрование.

```
NOTE: You should set only those versions of the protocol, which are supported by Python Framework. If some versions of the cryptographic protocol are not supported by your current version of Python Framework, they will be ignored and skipped. In this case, exceptions won't be generated. Please use 'set_supported_encryption_unsafe(value)' method of the SmtpClient class if you want to set the protocols without any compatibility checks.
```
В приведенном ниже примере кода показано, как настроить TLS 1.3 для экземпляра класса SmtpClient.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

## **Использование механизма CRAM-MD5 для аутентификации**

Механизм аутентификации CRAM-MD5 в Aspose.Email для Python обеспечивает дополнительный уровень безопасности при доступе к серверу. В следующем фрагменте кода показано, как внедрить эту функцию в свой проект:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.CRAM_MD5
```
