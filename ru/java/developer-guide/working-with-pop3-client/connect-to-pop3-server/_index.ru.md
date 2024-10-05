---
title: "Подключение к POP3 серверу"
url: /ru/java/connect-to-pop3-server/
weight: 10
type: docs
---


Класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) позволяет приложениям управлять почтовыми ящиками с использованием Протокола Почтового Офиса, версия 3 (POP3). Для подключения к серверу используйте класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). Класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) является основным средством для разработчиков, которые хотят добавить управление POP3 в свои приложения .NET. В этой статье объясняется, как его использовать. Чтобы подключиться к POP3 серверу:

1. Создайте экземпляр класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Укажите хост, имя пользователя и пароль в экземпляре [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).

Следующий фрагмент кода показывает, как подключиться к POP3 серверу.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client();

// Укажите хост, имя пользователя, пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Подключено к POP3 серверу.");
~~~

## **Подключение к SSL серверу**

[Подключение к POP3 серверу](#connecting-to-pop3-server) описывает, как подключиться к POP3 серверу в три простых шага:

1. Создайте экземпляр класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Укажите хост, имя пользователя и пароль.

Процесс подключения к POP3 серверу с поддержкой SSL аналогичен, но требует, чтобы вы задали несколько дополнительных свойств:

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Порт

Чтобы подключиться к POP3 серверу с поддержкой SSL, используйте класс [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) и установите свойства [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) и Порт. Следующий фрагмент кода показывает, как подключиться к POP3 серверу с поддержкой SSL.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client();

// Укажите хост, имя пользователя и пароль, порт и параметры безопасности для вашего клиента
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Подключение к POP3 серверу с использованием SSL.");
~~~

## **Подключение к APOP серверу**

POP означает Протокол Почтового Офиса. APOP означает Аутентифицированный Протокол Почтового Офиса. APOP является расширенной версией настройки сервера POP3, которая шифрует ваше имя пользователя и пароль и использует механизм аутентификации, разработанный для защиты пароля вашей учетной записи POP3 при проверке электронной почты. Аутентификация APOP не требует отправки пароля учетной записи в виде открытого текста на почтовый сервер POP3.

## **Подключение к серверу через прокси**

Прокси-серверы очень распространены для связи с внешним миром. В таких случаях адреса прокси используются почтовыми клиентами для доступа к почтовым ящикам через Интернет. Aspose.Email предоставляет поддержку версий 4, 4a и 5 протокола прокси SOCKS. Эта статья предоставляет рабочий пример получения электронной почты с использованием прокси-сервера. Чтобы получить электронную почту через прокси-сервер:

1. Инициализируйте [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) с необходимой информацией, а именно адресом прокси, портом и версией SOCKS.
1. Инициализируйте [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) с адресом хоста, именем пользователя, паролем и любыми другими настройками.
2. Установите свойство клиента Proxy в объект [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/), созданный выше.

Следующий фрагмент кода показывает, как получить электронные письма через прокси-сервер.

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java

// Создайте экземпляр класса Pop3Client
Pop3Client client = new Pop3Client("pop.domain.com", "username", "password");

// Установите адрес прокси, порт и прокси
String proxyAddress = "192.168.203.142";
int proxyPort = 1080;
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
~~~

## **Подключение к серверу через HTTP-прокси**

~~~Java
// Для полных примеров и файлов данных, пожалуйста, перейдите по адресу https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (Pop3Client client = new Pop3Client("imap.domain.com", "username", "password")) {
    client.setProxy(proxy);
    Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
}
~~~

## **Настройка механизма аутентификации**

Получите список механизмов аутентификации, поддерживаемых сервером POP3, с помощью метода [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getSupportedAuthentication--) класса [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/). Этот метод позволяет клиенту определить, какие методы аутентификации доступны для установки безопасного соединения с сервером. Затем, используя метод [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setAllowedAuthentication-long-), который получает (или устанавливает) перечисление типов аутентификации, разрешенных пользователем, выберите наиболее подходящий механизм аутентификации для общения клиент-сервер. Это позволяет вам явно установить метод аутентификации для почтового клиента.

Следующий пример кода показывает, как настроить аутентификацию почтового клиента:

```java
pop3Client.setAllowedAuthentication(Pop3KnownAuthenticationType.Plain);
```

## **Поддержка протокола OAuth 2.0 для авторизации**

OAuth 2.0 предоставляет авторизацию 

Pop3Client поддерживает OAuth 2.0, предоставляя специфические способы авторизации для приложений. Следующие конструкторы используются для инициализации POP3Client с использованием OAuth:

```java
public Pop3Client(

            String host, /*Имя хоста*/

            int port, /*Номер порта*/ 

            String username, /*Имя пользователя*/

            ITokenProvider tokenProvider, /*Поставщик токенов, позволяющий получить токен доступа*/

            /*SecurityOptions*/int securityOptions) /*Режим безопасности для почтового клиента*/



public Pop3Client(

            String host, /*Имя хоста*/

            int port, /*Номер порта*/

            String username, /*Имя пользователя*/

            String authInfo, /*Пароль пользователя или токен доступа XOAUTH2*/

            boolean useOAuth, /*Определяет, используется ли механизм SASL XOAUTH2 для входа на сервер*/

            /*SecurityOptions*/int securityOptions) /*Режим безопасности для почтового клиента*/
```

## **Подтверждение учетных данных почтового сервера без отправки электронной почты**

Иногда необходимо проверить учетные данные без отправки электронной почты. Aspose.Email предоставляет метод [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#validateCredentials--) для выполнения этой операции. Если проверка прошла успешно, код внутри оператора if выполняется, обычно используется для выполнения дополнительных действий или получения данных с IMAP сервера. Следующий фрагмент кода демонстрирует проверку учетных данных без отправки электронной почты:

```java
try (Pop3Client pop3Client = new Pop3Client(
        server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto)) {
    pop3Client.setTimeout(4000);

    if (pop3Client.validateCredentials()) {
        // выполнить какое-либо действие
    }
}
```

## **Использование аутентификации CRAM-MD5 для подключения к серверу**

Чтобы обеспечить безопасную аутентификацию и связь с сервером POP3, вы можете указать и настоять на использовании CRAM-MD5 в качестве разрешенного метода аутентификации для клиента POP3. Следующий фрагмент кода показывает, как настроить разрешенный тип аутентификации для [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/):

```java
popClient.setAllowedAuthentication(Pop3KnownAuthenticationType.CramMD5);
```
## **Как установить таймаут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (задержки сети, размер данных, производительность сервера и т. д.). Вы можете установить таймаут для всех почтовых операций. Пример кода ниже показывает, как это сделать с помощью свойства [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setTimeout-int-). Примечание: не следует устанавливать большие значения, чтобы избежать долгого ожидания в вашем приложении.

~~~Java
try (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.setTimeout(60000); // 60 секунд

    // какой-то код...
}
~~~