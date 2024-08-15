---
title: "Подключение к серверу IMAP"
url: /ru/java/connecting-to-imap-server/
weight: 10
type: docs
---


The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс позволяет приложениям управлять почтовыми ящиками IMAP с помощью протокола IMAP. [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс используется для подключения к почтовым серверам IMAP и управления электронной почтой в папках электронной почты IMAP. Для подключения к серверу IMAP

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Укажите имя хоста, имя пользователя и пароль в поле [Конструктор IMAP-клиентов](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

Как только [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) экземпляр инициирован, следующий вызов любой операции с использованием этого экземпляра подключится к серверу. В следующем фрагменте кода показано, как подключиться к серверу IMAP, используя описанные выше шаги.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
~~~

## **Подключение к серверу IMAP с поддержкой SSL**

[Подключение к серверу IMAP](/email/java/connecting-to-imap-server#connecting-with-imap-server) описал, как подключиться к серверу IMAP за четыре простых шага:

1. Создайте экземпляр [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Укажите имя хоста, имя пользователя и пароль.
1. Укажите порт.
1. Укажите [Опции безопасности](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/).

Процесс подключения к серверу IMAP с поддержкой SSL аналогичен, но требует установки еще нескольких свойств:

- Set [Опции безопасности](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) в SSlimplicit.

В следующем фрагменте кода показано, как

1. Задайте имя пользователя, пароль и порт.
1. Задайте параметр безопасности.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Создайте экземпляр ImapClient class
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");

// Set the security mode to implicit
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~

## **Подключение к серверу через прокси-сервер**

Прокси-серверы обычно используются для связи с внешним миром. В таких случаях почтовые клиенты не могут обмениваться данными через Интернет без указания адреса прокси-сервера. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 протокола прокси-сервера SOCKS. В этой статье представлен рабочий пример доступа к почтовому ящику с помощью прокси-почтового сервера. Чтобы получить доступ к почтовому ящику через прокси-сервер, выполните следующие действия:

1. Initialize [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) с необходимой информацией, то есть адресом прокси-сервера, портом и версией SOCKS.
1. Initialize [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
1. Настройте клиент [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) недвижимость для [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) объект, созданный выше.

В следующем фрагменте кода показано, как получить почтовый ящик через прокси-сервер.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP and set SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);

String proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Set the proxy
client.setProxy(proxy);

try {
    client.selectFolder("Inbox");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Подключение к серверу через HTTP-прокси-сервер**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
final ImapClient client = new ImapClient("imap.domain.com", "username", "password");
try {
    client.setProxy(proxy);
    client.selectFolder("Inbox");
} finally {
    if (client != null)
        client.dispose();
}
~~~

## **Настройка механизма аутентификации**

Получите список механизмов аутентификации, поддерживаемых сервером IMAP, используя [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getSupportedAuthentication--) метод [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс. Этот метод позволяет клиенту определить, какие методы аутентификации доступны для установления безопасного соединения с сервером. Затем, используя [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setAllowedAuthentication-long-) метод, который получает (или задает) перечисление типов аутентификации, разрешенных пользователем, выбирает наиболее подходящий механизм аутентификации для связи между клиентом и сервером. Это позволяет явно установить метод аутентификации для почтового клиента.

В следующем примере кода показано, как настроить аутентификацию почтового клиента:

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.Plain);
```

## **Подключение к серверу в режиме «только для чтения»**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) класс предоставляет [ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) свойство, для которого задано значение **true**, указывает на то, что не следует вносить никаких изменений в постоянное состояние почтового ящика. Следующий пример кода демонстрирует использование [ImapClient.ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) имущество. Оно определяет количество непрочитанных сообщений, затем извлекает одно сообщение, а затем снова получает количество непрочитанных сообщений в режиме «только для чтения». Количество непрочитанных сообщений осталось прежним, что означает, что постоянное состояние почтового ящика не изменилось.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.hasNoFlags(ImapMessageFlags.isRead()); /* get unread messages. */
MailQuery query = imapQueryBuilder.getQuery();

imapClient.setReadOnly(true);
imapClient.selectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.listMessages(query);
System.out.println("Initial Unread Count: " + messageInfoCol.size());
if (messageInfoCol.size() > 0) {
    imapClient.fetchMessage(messageInfoCol.get_Item(0).getSequenceNumber());

    messageInfoCol = imapClient.listMessages(query);
    // This count will be equal to the initial count
    System.out.println("Updated Unread Count: " + messageInfoCol.size());
} else {
    System.out.println("No unread messages found");
}
~~~

## **Использование аутентификации CRAM-MD5 для подключения к серверу**

Чтобы обеспечить безопасную аутентификацию и связь с сервером IMAP, вы можете указать и принудительно использовать CRAM-MD5 в качестве разрешенного метода аутентификации для клиента IMAP. В следующем фрагменте кода показано, как настроить разрешенный тип аутентификации для [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.CramMD5);
```
## **Подтвердите учетные данные почтового сервера без отправки электронной почты**

Иногда необходимо подтвердить учетные данные без отправки электронного письма. Aspose.Email предоставляет [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#validateCredentials--) метод выполнения этой операции. Если проверка прошла успешно, выполняется код, содержащийся в инструкции if, который обычно используется для выполнения дальнейших действий или получения данных с сервера IMAP. Следующий фрагмент кода демонстрирует проверку учетных данных без отправки электронного письма:

```java
try (ImapClient imapClient = new ImapClient(
        server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto)) {
    imapClient.setTimeout(4000);

    if (imapClient.validateCredentials()) {
        // to do something
    }
}
```

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (сетевых задержек, размера данных, производительности сервера и т. д.). Можно установить тайм-аут для всех почтовых операций. В приведенном ниже примере кода показано, как это сделать с помощью [Timeout](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setTimeout-int-) имущество. Примечание: не следует устанавливать большие значения, чтобы избежать длительного ожидания в приложении.

~~~Java
try (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~

## **Как ограничить тайм-аут приветствия**

Клиент IMAP может использовать автоматический режим для установления соединения. В этом режиме клиент IMAP проверяет все возможные параметры соединения до тех пор, пока соединение не будет установлено. Сервер IMAP в случае правильного соединения отправляет клиенту строку приветствия. Серверы могут использовать неявное или явное (START TLS) инициирование соединения SSL/TLS. Если режим соединения не совпадает (например, сервер ожидает неявного SSL-соединения, но клиент пытается установить незащищенное или явное SSL-соединение), сервер не отправит строку приветствия, а пользователь будет долго ждать, пока тайм-аут не достигнет строки приветствия, и клиент перейдет к следующему варианту подключения. Чтобы избежать этой проблемы, был введен режим greetingTimeout. Это свойство позволяет установить время ожидания строки приветствия и сократить время автоматического установления соединения.

```java
ImapClient imapClient = new ImapClient();
imapClient.setGreetingTimeout(4000);
```
