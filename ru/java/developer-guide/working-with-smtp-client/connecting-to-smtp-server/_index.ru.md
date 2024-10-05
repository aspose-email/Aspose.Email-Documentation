---
title: "Подключение к SMTP серверу"
url: /ru/java/connecting-to-smtp-server/
weight: 10
type: docs
---

При подключении к SMTP серверу с поддержкой SSL необходимо установить следующие параметры.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Порт

В приведенных ниже примерах мы показываем, как:

1. Установить имя пользователя.
2. Установить пароль.
3. Установить порт.
4. Установить параметр безопасности.

Следующий фрагмент кода показывает, как подключиться к SMTP серверу с поддержкой SSL.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com");

// Set username, password, port, and security options
client.setUsername("your.email@gmail.com");
client.setPassword("your.password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~

## **Подключение к серверу через SOCKS прокси-сервер**

Иногда мы используем прокси-серверы для связи с внешним миром. В таких случаях почтовые клиенты не могут осуществлять связь через Интернет без указания адреса прокси. Aspose.Email предоставляет поддержку версий 4, 4a и 5 протокола прокси SOCKS. В этой статье приведен работающий пример отправки электронной почты с помощью прокси почтового сервера. Для отправки электронной почты через прокси-сервер:

1. Инициализируйте прокси с необходимой информацией, то есть адресом прокси, портом и версией SOCKS.
2. Инициализируйте [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) с адресом хоста, именем пользователя и паролем, а также любыми другими настройками.
3. Установите свойство Proxy клиента на объект [Proxy](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getProxy--) , созданный ранее.

Следующий фрагмент кода показывает, как подключиться к серверу через прокси-сервер.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.SSLImplicit);
String proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Отправка электронной почты через прокси",
        "Реализуйте протокол SOCKS proxy для версий 4, 4a, 5 (только аутентификация через имя пользователя/пароль)"));
~~~

## **Подключение к серверу через HTTP прокси-сервер**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (SmtpClient client = new SmtpClient("host", 587, "username", "password")) {
    client.setProxy(proxy);
    client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Отправка электронной почты через прокси",
            "Реализуйте протокол SOCKS proxy для версий 4, 4a, 5 (только аутентификация через имя пользователя/пароль)"));
}
~~~

## **Настройка механизма аутентификации**

Получите список механизмов аутентификации, поддерживаемых SMTP сервером, используя метод [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getSupportedAuthentication--) класса [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/). Этот метод позволяет клиенту определить, какие методы аутентификации доступны для установки безопасного соединения с сервером. Затем, используя метод [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setAllowedAuthentication-long-), который получает (или устанавливает) перечисление допустимых пользователем типов аутентификации, выберите наиболее подходящий механизм аутентификации для связи клиент-сервер. Это позволяет вам явно установить метод аутентификации для почтового клиента.

Следующий пример кода показывает, как настроить аутентификацию почтового клиента:

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.Login);
```
## **Использование аутентификации CRAM-MD5 для подключения к серверу**

Для обеспечения безопасной аутентификации и связи с SMTP сервером вы можете указать и обеспечить использование CRAM-MD5 в качестве разрешенного метода аутентификации для почтового клиента SMTP. Следующий фрагмент кода показывает, как настроить разрешенный тип аутентификации для [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/):

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.CramMD5);
```

## **Привязка SMTP клиента к конкретному IP-адресу на хосте**

Невозможно исключить возможность наличия у хоста нескольких портов для отправки электронных писем. В таких случаях может возникнуть необходимость привязать клиента для отправки электронной почты к конкретному порту на хосте. Это также можно осуществить с помощью API Aspose.Email, используя свойство [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#bindIPEndPoint-com.aspose.email.BindIPEndPointHandler-). API [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) может быть настроен для использования конкретного IP-адреса на хосте, указав конкретную конечную точку IP. Следующий фрагмент кода показывает, как привязать SMTP клиент к конкретному IP-адресу на хосте.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", // host
        587, // port
        "username", // username
        "password", // password
        SecurityOptions.Auto // Security Options
);
try {
    client.bindIPEndPoint(new BindIPEndPointHandler() {
        public InetSocketAddress invoke(InetSocketAddress remoteEndPoint) {
            return new InetSocketAddress(0);
        }
    });
    client.noop();
} finally {
    client.dispose();
}
~~~ 

## **Проверка учетных данных почтового сервера без отправки электронной почты**

Иногда необходимо проверить учетные данные без отправки электронной почты. Aspose.Email предоставляет метод [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#validateCredentials--) для выполнения этой операции. Если проверка прошла успешно, код внутри инструкции if выполняется, обычно используется для выполнения дальнейших действий или получения данных с IMAP сервера. Следующий фрагмент кода демонстрирует проверку учетных данных без отправки электронной почты:

```java
try (SmtpClient smtpClient = new SmtpClient(
        server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto)) {
    smtpClient.setTimeout(4000);

    if (smtpClient.validateCredentials()) {
        // to do something
    }
}
```

## **Как установить тайм-аут для операций с электронной почтой**

Каждая операция с электронной почтой занимает определенное время в зависимости от многих факторов (сетевая задержка, размер данных, производительность сервера и т.д.). Вы можете установить тайм-аут для всех операций с электронной почтой. Пример кода ниже показывает, как это сделать, используя свойство [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getTimeout--). Примечание: не следует устанавливать большие значения, чтобы избежать длительных ожиданий в вашем приложении.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~