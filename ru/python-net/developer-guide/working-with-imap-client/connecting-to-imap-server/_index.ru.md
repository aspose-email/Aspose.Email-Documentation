---
title: "Подключение к IMAP-серверу"
url: /ru/python-net/connecting-to-imap-server/
weight: 10
type: docs
---

Класс [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) в Aspose.Email для Python служит компонентом для взаимодействия с учетными записями электронной почты с использованием протокола IMAP. IMAP (Internet Message Access Protocol) — это стандартный протокол для доступа к электронным сообщениям и управления ими, хранящимися на почтовом сервере.

Класс [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) предоставляет функциональность для подключения к почтовому серверу через IMAP, аутентификации пользователей, извлечения электронных писем, управления папками и выполнения различных операций, таких как чтение, перемещение, удаление или обновление электронных сообщений. Этот класс позволяет разработчикам интегрировать функциональность IMAP в свои Python-приложения, позволяя им взаимодействовать с учетными записями электронной почты стандартизированным и совместимым с протоколом образом.

Чтобы подключиться к IMAP-серверу, выполните три простых шага. Пример кода ниже демонстрирует, как программно подключиться к IMAP-серверу.

1. Создайте экземпляр класса ImapClient.
2. Укажите имя хоста, порт, имя пользователя и пароль.
3. Укажите параметры безопасности.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
```
## **Подключение к IMAP-серверу с поддержкой SSL**

Процесс подключения к IMAP-серверу с поддержкой SSL аналогичен описанному выше, но требует установки другого свойства:

- Установите параметры безопасности на SSLImplicit.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

# Установите режим безопасности на явный
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```
## **Подключение к серверу через прокси**

Прокси-сервер выступает посредником между устройством пользователя и интернетом. Его можно использовать по различным причинам, таким как улучшение сетевой производительности, увеличение безопасности и конфиденциальности, обход географических ограничений и кэширование веб-контента для уменьшения использования пропускной способности. Прокси-серверы также могут использоваться для фильтрации и мониторинга интернет-использования в организации или для обеспечения анонимности пользователей. Aspose.Email поддерживает версии 4, 4a и 5 протокола SOCKS. Пример кода и шаги ниже демонстрируют, как настроить IMAP-клиент для подключения к IMAP-серверу через SOCKS-прокси-сервер для безопасной и конфиденциальной связи с почтовым сервером.

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) и задайте параметры IMAP-сервера.
2. Установите параметры безопасности на автоматические для IMAP-клиента.
3. Определите параметры прокси-сервера, такие как IP-адрес и порт.
4. Создайте объект SocksProxy с заданным адресом и портом прокси, используя SOCKS версии 5.
5. Установите созданный прокси как прокси для IMAP-клиента.
6. Подключитесь к IMAP-серверу и выберите папку "Входящие" с помощью прокси для связи.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.AUTO
proxy_address = "192.168.203.142"
proxy_port = 1080

proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = proxy
client.select_folder("Inbox")
```
## **Подключение к серверу через HTTP-прокси**

Aspose.Email также предоставляет функциональность доступа к почтовому ящику с использованием HTTP-прокси. Пример кода ниже демонстрирует, как настроить IMAP-клиента для подключения к IMAP-серверу через HTTP-прокси-сервер для безопасной и конфиденциальной связи с почтовым сервером.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Inbox")
```
## **Подключение к серверу в режиме только для чтения**

Реализация функциональности режима только для чтения для почтового ящика включает в себя предоставление возможности контролировать и ограничивать изменения постоянного состояния почтового ящика, обеспечивая целостность данных, соблюдение норм и удобство для пользователя. Установка значения True для этого свойства указывает, что изменения не допускаются. Пример кода ниже показывает, как использовать это свойство в проекте:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```
## **Подключение к серверу с использованием аутентификации CRAM-MD5**

Использование аутентификации CRAM-MD5 предоставляет безопасный способ аутентификации на почтовом сервере. С помощью Aspose.Email вы можете легко реализовать эту функциональность в своем проекте на Python.

Пример кода ниже демонстрирует, как настроить клиент для приема CRAM-MD5 как одного из поддерживаемых методов аутентификации для подключения к IMAP-серверу:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```
## **Как установить таймаут для почтовых операций**

Свойство 'timeout' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) предотвращает бесконечное ожидание клиентом ответа при взаимодействии с почтовым сервером и позволяет обрабатывать возможные задержки соединения, проблемы с сетью или задержки. Таймаут рассчитывается в миллисекундах. Пример кода ниже показывает, как установить период таймаута в 60 000 миллисекунд (60 секунд) для ожидания ответа от сервера:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 секунд
client.timeout = 60000
```
## **Как ограничить таймаут приветствия**

Установка таймаута на операцию приветствия между клиентом и сервером позволяет клиенту ограничить время, которое он ждет ответа от сервера во время начального обмена сообщениями. Это важно, потому что если сервер не отвечает или возникают сетевые проблемы, клиент не должен ждать бесконечно ответа.

API предоставляет свойство 'greeting_timeout' класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) для установки таймаута на операцию приветствия. Пример кода ниже показывает, как ограничить таймаут приветствия:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```
## **Использование криптографических протоколов с IMAP-клиентом**

Aspose.Email поддерживает криптографические протоколы SSL (устаревший) и TLS для обеспечения безопасности коммуникаций. Свойство 'supported_encryption' класса [EmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients/emailclient/#emailclient-class) определяет версии протоколов шифрования SSL/TLS, которые будут использоваться.

> **_ПРИМЕЧАНИЕ:_** вы можете устанавливать только те версии протоколов, которые поддерживаются .NET Framework. Если некоторые версии протокола не поддерживаются вашей текущей версией .NET Framework, они будут игнорироваться и пропускаться. Это может привести к снижению уровня безопасности TLS. В этом случае исключения не будут вызваны. Пожалуйста, используйте метод 'set_supported_encryption_unsafe(value)', если хотите установить протоколы без каких-либо проверок совместимости.

Пример кода ниже показывает, как установить TLS 1.3 для экземпляра класса [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class).

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
В случае, если указанный шифровальный протокол не поддерживается в текущей версии .NET Framework, разница в поведении между методом 'set_supported_encryption_unsafe(value)' и свойством 'supported_encryption' заключается в следующем:

Если используется свойство 'supported_encryption', почтовый клиент снижает уровень шифрования до поддерживаемого.
Если используется метод 'set_supported_encryption_unsafe(value)', почтовый клиент вызывает исключения.