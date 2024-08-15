---
title: "Подключение к серверу POP3"
url: /ru/java/connect-to-pop3-server/
weight: 10
type: docs
---


The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс позволяет приложениям управлять почтовыми ящиками с использованием протокола Post Office Protocol версии 3 (POP3). Чтобы подключиться к серверу, используйте [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс. [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class — основная статья для разработчиков, которые хотят добавить управление POP3 в свои приложения.NET. В этой статье объясняется, как его использовать. Чтобы подключиться к серверу POP3, выполните следующие действия:

1. Создайте экземпляр [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.
1. Укажите хост, имя пользователя и пароль в поле [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) instance.

В следующем фрагменте кода показано, как подключиться к серверу POP3.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Connected to POP3 server.");
~~~

## **Подключение к серверу SSL**

[Подключение к серверу POP3](#connecting-to-pop3-server) описал, как подключиться к серверу POP3 за три простых шага:

1. Создайте экземпляр [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.
1. Укажите хост, имя пользователя и пароль.

Процесс подключения к серверу POP3 с поддержкой SSL аналогичен, но требует установки еще нескольких свойств:

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Port

Чтобы подключиться к серверу POP3 с поддержкой SSL, используйте [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс и установите [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) и портовая недвижимость. В следующем фрагменте кода показано, как подключиться к серверу POP3 с поддержкой SSL.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username and password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Connecting to POP3 server using SSL.");
~~~

## **Подключение к серверу APOP**

POP означает Почтовый протокол. APOP означает аутентифицированный почтовый протокол. APOP — это расширенная версия настройки сервера POP3, которая шифрует ваше имя пользователя и пароль и использует механизм аутентификации, предназначенный для защиты пароля учетной записи POP3 при проверке электронной почты. Аутентификация APOP не требует отправки пароля учетной записи в виде обычного текста на почтовый сервер POP3.

## **Подключение к серверу через прокси-сервер**

Прокси-серверы очень распространены для связи с внешним миром. В таких случаях прокси-адреса используются почтовыми клиентами для доступа к почтовым ящикам через Интернет. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 протокола прокси-сервера SOCKS. В этой статье представлен рабочий пример получения электронной почты с помощью прокси-почтового сервера. Чтобы получить электронную почту через прокси-сервер, выполните следующие действия:

1. Initialize [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) с необходимой информацией, то есть адресом прокси-сервера, портом и версией SOCKS.
1. Initialize [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
2. Присвойте свойству клиента Proxy значение [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) объект, созданный выше.

В следующем фрагменте кода показано, как получать электронные письма через прокси-сервер.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр Pop3Client class
Pop3Client client = new Pop3Client("pop.domain.com", "username", "password");

// Set proxy address, Port and Proxy
String proxyAddress = "192.168.203.142";
int proxyPort = 1080;
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
~~~

## **Подключение к серверу через HTTP-прокси-сервер**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (Pop3Client client = new Pop3Client("imap.domain.com", "username", "password")) {
    client.setProxy(proxy);
    Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
}
~~~

## **Настройка механизма аутентификации**

Получите список механизмов аутентификации, поддерживаемых сервером POP3, используя [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getSupportedAuthentication--) метод [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) класс. Этот метод позволяет клиенту определить, какие методы аутентификации доступны для установления безопасного соединения с сервером. Затем, используя [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setAllowedAuthentication-long-) метод, который получает (или задает) перечисление типов аутентификации, разрешенных пользователем, выбирает наиболее подходящий механизм аутентификации для связи между клиентом и сервером. Это позволяет явно установить метод аутентификации для почтового клиента.

В следующем примере кода показано, как настроить аутентификацию почтового клиента:

```java
pop3Client.setAllowedAuthentication(Pop3KnownAuthenticationType.Plain);
```

## **Поддержка протокола OAuth 2.0 для авторизации**

OAuth 2.0 обеспечивает авторизацию

Pop3Client поддерживает OAuth 2.0, предоставляя специальные способы авторизации для приложений. Для инициализации Pop3Client с помощью OAuth используются следующие конструкторы:

```java
public Pop3Client(

            String host, /*The host name*/

            int port, /*The port number*/

            String username, /*The user name*/

            ITokenProvider tokenProvider, /*TokenProvider allowing to retrieve access token*/

            /*SecurityOptions*/int securityOptions) /*Security mode for a mail client*/



public Pop3Client(

            String host, /*The host name*/

            int port, /*The port number*/

            String username, /*The user name*/

            String authInfo, /*The user password or XOAUTH2 access token*/

            boolean useOAuth, /*Defines whether SASL XOAUTH2 mechanism is used to login to the server*/

            /*SecurityOptions*/int securityOptions) /*Security mode for a mail client*/
```

## **Подтвердите учетные данные почтового сервера без отправки электронной почты**

Иногда необходимо подтвердить учетные данные без отправки электронного письма. Aspose.Email предоставляет [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#validateCredentials--) метод выполнения этой операции. Если проверка прошла успешно, выполняется код, содержащийся в инструкции if, который обычно используется для выполнения дальнейших действий или получения данных с сервера IMAP. Следующий фрагмент кода демонстрирует проверку учетных данных без отправки электронного письма:

```java
try (Pop3Client pop3Client = new Pop3Client(
        server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto)) {
    pop3Client.setTimeout(4000);

    if (pop3Client.validateCredentials()) {
        // to do something
    }
}
```

## **Использование аутентификации CRAM-MD5 для подключения к серверу**

Чтобы обеспечить безопасную аутентификацию и связь с сервером POP3, можно указать и принудительно использовать CRAM-MD5 в качестве разрешенного метода аутентификации для клиента POP3. В следующем фрагменте кода показано, как настроить разрешенный тип аутентификации для [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/):

```java
popClient.setAllowedAuthentication(Pop3KnownAuthenticationType.CramMD5);
```
## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (сетевых задержек, размера данных, производительности сервера и т. д.). Можно установить тайм-аут для всех почтовых операций. В приведенном ниже примере кода показано, как это сделать с помощью [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setTimeout-int-) имущество. Примечание: не следует устанавливать большие значения, чтобы избежать длительного ожидания в приложении.

~~~Java
try (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.setTimeout(60000); // 60 seconds

    // some code...
}
~~~