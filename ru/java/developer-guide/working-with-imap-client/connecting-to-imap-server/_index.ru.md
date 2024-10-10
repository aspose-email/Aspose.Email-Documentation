---
title: "Подключение к IMAP-серверу"
url: /ru/java/connecting-to-imap-server/
weight: 10
type: docs
---


Класс [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) позволяет приложениям управлять IMAP-почтовыми ящиками с использованием протокола IMAP. Класс [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) используется для подключения к IMAP-почтовым серверам и управления электронными письмами в папках IMAP. Чтобы подключиться к IMAP-серверу:

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Укажите имя хоста, имя пользователя и пароль в [конструкторе ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

После инициализации экземпляра [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) следующий вызов любой операции с использованием этого экземпляра подключит к серверу. Следующий фрагмент кода показывает, как подключиться к IMAP-серверу, используя указанные выше шаги.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Создаем imapclient с хостом, пользователем и паролем
ImapClient client = new ImapClient("localhost", "user", "password");
~~~

## **Подключение к IMAP-серверу с включенным SSL**

[Подключение к IMAP-серверу](/email/java/connecting-to-imap-server#connecting-with-imap-server) описывает, как подключиться к IMAP-серверу в четыре простых шага:

1. Создайте экземпляр класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).
1. Укажите имя хоста, имя пользователя и пароль.
1. Укажите порт.
1. Укажите [Параметры безопасности](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/).

Процесс подключения к IMAP-серверу с включенным SSL схож, но требует настройки нескольких дополнительных параметров:

- Установите [Параметры безопасности](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) на SSLImplicit.

Следующий фрагмент кода показывает, как

1. Установить имя пользователя, пароль и порт.
1. Установить параметр безопасности.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Создаем экземпляр класса ImapClient
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");

// Устанавливаем режим безопасности на implicit
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~

## **Подключение к серверу через прокси**

Прокси-серверы обычно используются для связи с внешним миром. В таких случаях почтовые клиенты не могут обмениваться данными через Интернет без указания адреса прокси. Aspose.Email предоставляет поддержку версий 4, 4a и 5 протокола прокси SOCKS. Эта статья предоставляет рабочий пример доступа к почтовому ящику с использованием прокси-почтового сервера. Чтобы получить доступ к почтовому ящику через прокси-сервер:

1. Инициализируйте [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) с необходимой информацией, такой как адрес прокси, порт и версия SOCKS.
1. Инициализируйте [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) с адресом хоста, именем пользователя, паролем и другими настройками.
1. Установите свойство клиента [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) на объект [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/), созданный выше.

Следующий фрагмент кода показывает, как получить почтовый ящик через прокси-сервер.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
// Подключаемся и входим в IMAP и устанавливаем SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);

String proxyAddress = "192.168.203.142"; // адрес прокси
int proxyPort = 1080; // порт прокси
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Устанавливаем прокси
client.setProxy(proxy);

try {
    client.selectFolder("Inbox");
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~

## **Подключение к серверу через HTTP-прокси**

~~~Java
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
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

Получите список механизмов аутентификации, поддерживаемых IMAP-сервером, с помощью метода [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getSupportedAuthentication--) класса [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/). Этот метод позволяет клиенту определить, какие методы аутентификации доступны для установления безопасного соединения с сервером. Затем, используя метод [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setAllowedAuthentication-long-), который получает (или устанавливает) перечисление типов аутентификации, разрешенных пользователем, выберите наиболее подходящий механизм аутентификации для связи клиент-сервер. Это позволяет явно установить метод аутентификации для почтового клиента.

Следующий фрагмент кода показывает, как настроить аутентификацию почтового клиента:

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.Plain);
```

## **Подключение к серверу в режиме "Только чтение"**

Класс [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) предоставляет свойство [ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-), которое при установке в **true** указывает, что никакие изменения не должны быть внесены в постоянное состояние почтового ящика. Следующий фрагмент кода демонстрирует использование свойства [ImapClient.ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-). Он получает количество непрочитанных сообщений, затем извлекает одно сообщение и снова получает количество непрочитанных сообщений в режиме "только чтение". Количество непрочитанных сообщений остается неизменным, что указывает на то, что постоянное состояние почтового ящика не изменилось.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, посетите https://github.com/aspose-email/Aspose.Email-for-Java
ImapClient imapClient = new ImapClient();
imapClient.setHost("<HOST>");
imapClient.setPort(993);
imapClient.setUsername("<USERNAME>");
imapClient.setPassword("<PASSWORD>");
imapClient.setSupportedEncryption(EncryptionProtocols.Tls);
imapClient.setSecurityOptions(SecurityOptions.SSLImplicit);

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.hasNoFlags(ImapMessageFlags.isRead()); /* получить непрочитанные сообщения. */
MailQuery query = imapQueryBuilder.getQuery();

imapClient.setReadOnly(true);
imapClient.selectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.listMessages(query);
System.out.println("Начальное количество непрочитанных: " + messageInfoCol.size());
if (messageInfoCol.size() > 0) {
    imapClient.fetchMessage(messageInfoCol.get_Item(0).getSequenceNumber());

    messageInfoCol = imapClient.listMessages(query);
    // Это количество будет равно начальному
    System.out.println("Обновленное количество непрочитанных: " + messageInfoCol.size());
} else {
    System.out.println("Непрочитанных сообщений не найдено");
}
~~~

## **Использование аутентификации CRAM-MD5 для подключения к серверу**

Чтобы обеспечить безопасную аутентификацию и связь с IMAP-сервером, вы можете указать и принудить использование CRAM-MD5 в качестве разрешенного метода аутентификации для IMAP-клиента. Следующий фрагмент кода показывает, как настроить разрешенный тип аутентификации для [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.CramMD5);
```
## **Проверка учетных данных почтового сервера без отправки электронной почты**

Иногда необходимо проверить учетные данные без отправки электронной почты. Aspose.Email предоставляет метод [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#validateCredentials--) для выполнения этой операции. Если проверка успешна, выполняется код внутри оператора if, который обычно используется для выполнения дополнительных действий или получения данных с IMAP-сервера. Следующий фрагмент кода демонстрирует проверку учетных данных без отправки электронной почты:

```java
try (ImapClient imapClient = new ImapClient(
        server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto)) {
    imapClient.setTimeout(4000);

    if (imapClient.validateCredentials()) {
        // выполнить что-то
    }
}
```

## **Как установить таймаут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от множества факторов (задержек в сети, размера данных, производительности сервера и т. д.). Вы можете установить таймаут для всех почтовых операций. Пример кода ниже показывает, как это сделать с использованием свойства [Timeout](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setTimeout-int-). Примечание: не следует устанавливать большие значения, чтобы избежать долгих ожиданий в вашем приложении.

~~~Java
try (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.setTimeout(60000); // 60 секунд

    // какой-то код...
}
~~~

## **Как ограничить таймаут приветствия**

IMAP-клиент может использовать автоматический режим для установления соединения. В этом режиме IMAP-клиент проходит через все возможные параметры соединения, пока соединение не будет установлено. IMAP-сервер в случае правильного соединения отправляет приветственное сообщение клиенту. Серверы могут использовать неявную или явную (START TLS) инициацию SSL/TLS соединения. Если режим соединения не совпадает (например, сервер ожидает неявное SSL-соединение, но клиент пытается установить незащищенное или явное SSL-соединение), сервер не отправит приветственное сообщение, и пользователь будет долго ждать, пока таймаут не достигнет сообщения приветствия, и клиент перейдет к следующему варианту соединения. Чтобы избежать этой проблемы, был введен GreetingTimeout. Это свойство позволяет установить время ожидания для приветственного сообщения и сократить время автоматического установления соединения.

```java
ImapClient imapClient = new ImapClient();
imapClient.setGreetingTimeout(4000);
```