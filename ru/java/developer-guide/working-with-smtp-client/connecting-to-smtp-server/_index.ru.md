---
title: "Подключение к SMTP-серверу"
url: /ru/java/connecting-to-smtp-server/
weight: 10
type: docs
---


При подключении к SMTP-серверу с поддержкой SSL необходимо задать следующие свойства.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Port

В приведенных ниже примерах мы покажем, как:

1. Задайте имя пользователя.
1. Установите пароль.
1. Настройте порт.
1. Задайте параметр безопасности.

В следующем фрагменте кода показано, как подключить SMTP-сервер с поддержкой SSL.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com");

// Set username, password, port, and security options
client.setUsername("your.email@gmail.com");
client.setPassword("your.password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~

## **Подключение к серверу через прокси-сервер Socks**

Иногда мы используем прокси-серверы для связи с внешним миром. В таких случаях почтовые клиенты не могут общаться через Интернет без указания адреса прокси-сервера. Aspose.Email обеспечивает поддержку версий 4, 4a и 5 прокси-протокола SOCKS. В этой статье представлен рабочий пример отправки электронной почты с помощью прокси-почтового сервера. Чтобы отправить электронное письмо через прокси-сервер, выполните следующие действия:

1. Инициализируйте прокси-сервер, указав необходимую информацию, например адрес прокси-сервера, порт и версию SOCKS.
1. Initialize [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) с адресом хоста, именем пользователя и паролем и любыми другими настройками.
1. Присвойте свойству клиента Proxy значение [Proxy](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getProxy--) объект, созданный ранее.

В следующем фрагменте кода показано, как подключиться к серверу через прокси-сервер.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.domain.com", "username", "password");
client.setSecurityOptions(SecurityOptions.SSLImplicit);
String proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy",
        "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"));
~~~

## **Подключение к серверу через прокси-сервер HTTP**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (SmtpClient client = new SmtpClient("host", 587, "username", "password")) {
    client.setProxy(proxy);
    client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy",
            "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"));
}
~~~

## **Настройка механизма аутентификации**

Получите список механизмов аутентификации, поддерживаемых SMTP-сервером, используя [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getSupportedAuthentication--) метод [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) класс. Этот метод позволяет клиенту определить, какие методы аутентификации доступны для установления безопасного соединения с сервером. Затем, используя [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setAllowedAuthentication-long-) метод, который получает (или задает) перечисление типов аутентификации, разрешенных пользователем, выбирает наиболее подходящий механизм аутентификации для связи между клиентом и сервером. Это позволяет явно установить метод аутентификации для почтового клиента.

В следующем примере кода показано, как настроить аутентификацию почтового клиента:

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.Login);
```
## **Использование аутентификации CRAM-MD5 для подключения к серверу**

Чтобы обеспечить безопасную аутентификацию и связь с SMTP-сервером, можно указать и принудительно использовать CRAM-MD5 в качестве разрешенного метода аутентификации для SMTP-клиента. В следующем фрагменте кода показано, как настроить разрешенный тип аутентификации для [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/):

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.CramMD5);
```

## **Привязать SMTP-клиент к определенному IP-адресу на хосте**

Нельзя исключать возможность наличия на хосте нескольких портов для отправки электронной почты. В таких случаях может возникнуть необходимость привязать клиент, отправляющий электронную почту, к определенному порту на хосте для отправки электронных писем. Это может быть достигнуто также с помощью API Aspose.Email, а также с помощью [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#bindIPEndPoint-com.aspose.email.BindIPEndPointHandler-) имущество. API [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) можно настроить использование определенного IP-адреса на хосте, указав конкретную конечную точку IP. В следующем фрагменте кода показано, как привязать SMTP-клиент к определенному IP-адресу на хосте.


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

## **Подтвердите учетные данные почтового сервера без отправки электронной почты**

Иногда необходимо подтвердить учетные данные без отправки электронного письма. Aspose.Email предоставляет [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#validateCredentials--) метод выполнения этой операции. Если проверка прошла успешно, выполняется код, содержащийся в инструкции if, который обычно используется для выполнения дальнейших действий или получения данных с сервера IMAP. Следующий фрагмент кода демонстрирует проверку учетных данных без отправки электронного письма:

```java
try (SmtpClient smtpClient = new SmtpClient(
        server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto)) {
    smtpClient.setTimeout(4000);

    if (smtpClient.validateCredentials()) {
        // to do something
    }
}
```

## **Как установить тайм-аут для почтовых операций**

Каждая почтовая операция занимает некоторое время в зависимости от многих факторов (сетевых задержек, размера данных, производительности сервера и т. д.). Можно установить тайм-аут для всех почтовых операций. В приведенном ниже примере кода показано, как это сделать с помощью [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getTimeout--) имущество. Примечание: не следует устанавливать большие значения, чтобы избежать длительного ожидания в приложении.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~