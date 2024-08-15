---
title: "Подключение к серверу POP3"
url: /ru/python-net/connect-to-pop3-server/
weight: 10
type: docs
---

## **Подключение к серверу POP3**
Класс Pop3Client позволяет приложениям управлять почтовыми ящиками с использованием протокола Post Office Protocol версии 3 (POP3). Для подключения к серверу используйте класс Pop3Client. Класс Pop3Client является основным компонентом для разработчиков, которые хотят добавить управление POP3 в свои приложения.NET. В этой статье объясняется, как его использовать. Чтобы подключиться к серверу POP3, выполните следующие действия:

1. Создайте экземпляр класса Pop3Client в качестве клиента.
1. Укажите хост, имя пользователя и пароль в экземпляре Pop3Client.

В следующем фрагменте кода показано, как подключиться к серверу POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ConnectingToPOP3-ConnectingToPOP3.py" >}}
## **Подключение к серверу SSL**
При подключении к серверу POP3 описано, как подключиться к серверу POP3 за три простых шага:

1. Создайте экземпляр класса Pop3Client.
1. Укажите хост, имя пользователя и пароль.

Процесс подключения к серверу POP3 с поддержкой SSL аналогичен, но требует установки еще нескольких свойств:

- SecurityOptions
- Port

Чтобы подключиться к серверу POP3 с поддержкой SSL, используйте класс Aspose.Email.Pop3.Pop3Client и задайте свойства SecurityOptions и Port. В следующем фрагменте кода показано, как подключиться к серверу с поддержкой SSL POP3.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.py" >}}

## **Подключение к серверу APOP**

APOP или Authenticated Post Office Protocol является расширением традиционного почтового протокола (POP) и обеспечивает безопасный метод аутентификации клиентов в процессе получения электронной почты. Ключевое преимущество APOP заключается в том, что фактический пароль никогда не передается по сети. Доступ к почтовому ящику пользователя предоставляется в результате успешного обмена хеш-значениями между сервером и клиентом.

### **Подключение к серверу через прокси-сервер**

Прокси-серверы очень распространены для связи с внешним миром. В таких случаях прокси-адреса используются почтовыми клиентами для доступа к почтовым ящикам через Интернет. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 протокола прокси-сервера SOCKS. Это [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) класс позволяет приложениям получать доступ к сообщениям и управлять ими с помощью протокола почтового отделения версии 3 (POP3). Метод get_mailbox_info () класса извлекает информацию о почтовом ящике, такую как количество сообщений, общий размер и т. д. В следующем примере кода показан процесс получения электронной почты с помощью почтового прокси-сервера:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
# Set proxy address, Port and Proxy
proxy_address = "192.168.203.142"
proxy_port = 1080
proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Подключение к серверу через HTTP-прокси-сервер**

Существуют различные типы прокси, в том числе HTTP-прокси, SOCKS-прокси и другие, каждый из которых предназначен для разных целей и обеспечивает разные уровни функциональности. Конкретные шаги и конфигурации могут отличаться в зависимости от типа используемого прокси-сервера. В приведенном ниже примере кода показано, как настроить POP3Client с дополнительной конфигурацией HTTP-прокси-сервера и получить информацию о почтовом ящике:

```py
import aspose.email as ae

proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Подключение к серверу через механизм аутентификации CRAM-MD5**

CRAM-MD5 (механизм аутентификации «запрос-ответ» с MD5) обычно используется в протоколах электронной почты, таких как POP3 и IMAP, где важна безопасная аутентификация. Он обеспечивает более высокий уровень безопасности по сравнению с передачей паролей в виде простого текста. Aspose.Email for .NET позволяет пользователям безопасно аутентифицироваться и получать доступ к серверам электронной почты, поддерживающим этот метод аутентификации.

```py
client.allowed_authentication = ae.clients.pop3.Pop3KnownAuthenticationType.CRAM_MD5
```
## **Как установить тайм-аут для почтовых операций**

Aspose.Email предоставляет свойство «тайм-аут» [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) класс для получения или установки тайм-аута для почтовых операций с целью предотвращения зависания или блокировки, решения проблем с сетью или сервером, повышения скорости реагирования и обеспечения эффективного управления ресурсами. В следующем примере кода показано, как внедрить свойство в проект:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
#  60 seconds
client.timeout = 60000
```
## **Использование криптографических протоколов с клиентом POP3**

Aspose.Email поддерживает криптографические протоколы SSL (устаревшие) и TLS для обеспечения безопасности связи. Для защиты обмена данными между приложением и почтовыми серверами можно включить криптографическое шифрование.

```
NOTE: It's important to know that you can only configure protocol versions supported by the .NET Framework. If your current .NET Framework version does not support certain protocol versions, those unsupported versions will be disregarded and skipped. This could result in a potential downgrade in TLS security level, and it's crucial to be aware that no exceptions will be raised in this situation. Developers should exercise caution to ensure the desired TLS security level is maintained based on the supported protocols in their .NET Framework environment.
```
В следующем примере кода показано, как настроить клиент POP3 с конфигурациями протокола шифрования TLS 1.3 для безопасной связи:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
Если указанный протокол шифрования не поддерживается в текущей версии .NET Framework, разница в поведении метода setSupportedEncryptionUnsafe и свойства SupportedEncryption заключается в следующем:

Если используется свойство supportedEncryption, почтовый клиент понижает протокол шифрования до поддерживаемого уровня.

Если используется метод setSupportedEncryptionUnsafe, почтовый клиент генерирует исключения.