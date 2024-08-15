---
title: "Подключение к серверу IMAP"
url: /ru/python-net/connecting-to-imap-server/
weight: 10
type: docs
---

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс в Aspose.Email для Python служит компонентом для взаимодействия с учетными записями электронной почты по протоколу IMAP. IMAP (Internet Message Access Protocol) — это стандартный протокол для доступа и управления сообщениями электронной почты, хранящимися на почтовом сервере.

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс предоставляет функции для подключения к почтовому серверу через IMAP, аутентификации пользователей, получения электронной почты, управления папками и выполнения различных операций, таких как чтение, перемещение, удаление или обновление сообщений электронной почты. Этот класс, по сути, позволяет разработчикам интегрировать функциональность IMAP в свои приложения на Python, позволяя им взаимодействовать с учетными записями электронной почты стандартизированным образом и в соответствии с протоколами.

Чтобы подключиться к серверу IMAP, выполните три простых шага. В приведенном ниже примере кода показано, как программно подключиться к серверу IMAP.

1. Создайте экземпляр класса IMAPClient.
2. Укажите имя хоста, порт, имя пользователя и пароль.
3. Укажите параметры безопасности.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
```
## **Подключение к серверу IMAP с поддержкой SSL**

Процесс подключения к серверу IMAP с поддержкой SSL аналогичен описанному выше, но требует установки другого свойства:

- Задайте для параметров безопасности значение SSLimplicit.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

# Set the security mode to implicit
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```
## **Подключение к серверу через прокси-сервер**

Прокси-сервер выступает в роли посредника между устройством пользователя и Интернетом. Его можно использовать по разным причинам, таким как повышение производительности сети, повышение безопасности и конфиденциальности, обход географических ограничений и кэширование веб-контента для снижения использования полосы пропускания. Прокси-серверы также можно использовать для фильтрации и мониторинга использования Интернета в организации или для обеспечения анонимности пользователей. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 протокола прокси-сервера SOCKS. В следующем примере кода и шагах показано, как настроить клиент IMAP для подключения к серверу IMAP через прокси-сервер SOCKS для безопасной и конфиденциальной связи с почтовым сервером.

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) и задайте сведения о сервере IMAP.
2. Установите автоматические параметры безопасности для клиента IMAP.
3. Задайте сведения о прокси-сервере, такие как IP-адрес и порт.
4. Создайте объект SocksProxy с заданным прокси-адресом и портом, используя SOCKS версии 5.
5. Настройте созданный прокси-сервер в качестве прокси-сервера для клиента IMAP.
6. Подключитесь к серверу IMAP и выберите папку «Входящие», используя прокси-сервер для связи.

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
## **Подключение к серверу через HTTP-прокси-сервер**

Aspose.Email также предоставляет возможность доступа к почтовому ящику с помощью HTTP-прокси. В приведенном ниже примере кода показано, как настроить клиент IMAP для подключения к серверу IMAP через прокси-сервер HTTP для безопасной и конфиденциальной связи с почтовым сервером.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Inbox")
```
## **Подключение к серверу в режиме «только для чтения»**

Внедрение режима «только для чтения» для почтового ящика предполагает предоставление возможности контролировать и ограничивать изменение постоянного состояния почтового ящика, обеспечивать целостность данных, соответствие требованиям и удобство работы пользователей. Значение True, присвоенное этому свойству, означает, что изменения запрещены. В следующем примере кода показано, как использовать это свойство в проекте:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```
## **Подключение к серверу с использованием аутентификации CRAM-MD5**

Использование аутентификации CRAM-MD5 обеспечивает безопасный способ аутентификации на почтовом сервере. С помощью Aspose.Email вы можете легко реализовать эту возможность в своем проекте на Python.

В следующем примере кода показано, как настроить клиент на прием CRAM-MD5 в качестве одного из поддерживаемых методов аутентификации при подключении к серверу IMAP:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```
## **Как установить тайм-аут для почтовых операций**

Свойство «тайм-аут» [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс не позволяет клиенту бесконечно ждать ответа при взаимодействии с почтовым сервером и позволяет обрабатывать потенциальные задержки соединения, сетевые проблемы или задержки. Время ожидания рассчитывается в миллисекундах. В следующем фрагменте кода показано, как установить для клиента период ожидания ответа сервера в 60 000 миллисекунд (60 секунд):

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 seconds
client.timeout = 60000
```
## **Как ограничить тайм-аут приветствия**

Установка тайм-аута для операции приветствия между клиентом и сервером позволяет клиенту ограничить время ожидания ответа от сервера во время первоначального процесса рукопожатия. Это важно, потому что если сервер не отвечает или возникают проблемы с сетью, клиенту не следует бесконечно ждать ответа.

API предоставляет свойство greeting_timeout, принадлежащее [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) класс для установки тайм-аута операции приветствия. В следующем фрагменте кода показано, как ограничить время ожидания приветствия: 

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```
## **Использование криптографических протоколов с клиентом IMAP**

Aspose.Email поддерживает криптографические протоколы SSL (устаревшие) и TLS для обеспечения безопасности связи. Свойство 'supported_encryption' [EmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients/emailclient/#emailclient-class) класс определяет версии используемых протоколов шифрования SSL/TLS.

> **_NOTE:_** вы можете установить только те версии протокола, которые поддерживаются фреймворком.net. Если некоторые версии протокола не поддерживаются вашей текущей версией.NET framework, они будут проигнорированы и пропущены. Это может привести к снижению уровня безопасности TLS. В этом случае исключения не будут созданы. Используйте метод set_supported_encryption_unsafe (value), если вы хотите настроить протоколы без каких-либо проверок совместимости.

В приведенном ниже примере кода показано, как установить TLS 1.3 для [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) экземпляр класса.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
Если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении метода set_supported_encryption_unsafe (value) и свойства supported_encryption заключается в следующем:

Если используется свойство supported_encryption, почтовый клиент понижает протокол шифрования до поддерживаемого уровня.
Если используется метод set_supported_encryption_unsafe (value), почтовый клиент генерирует исключения.