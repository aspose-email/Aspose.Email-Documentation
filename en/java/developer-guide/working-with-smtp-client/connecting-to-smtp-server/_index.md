---
title: Connecting to SMTP Server
type: docs
weight: 10
url: /java/connecting-to-smtp-server/
---


The following properties need to be set when connecting with an SMTP server with SSL support.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Port

In the examples below we show how to:

1. Set a username.
1. Set a password.
1. Set the port.
1. Set security option.

The following code snippet shows you how to connect SSL enabled SMTP server.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

SmtpClient client = new SmtpClient("smtp.gmail.com");

// Set username, password, port, and security options
client.setUsername("your.email@gmail.com");
client.setPassword("your.password");
client.setPort(587);
client.setSecurityOptions(SecurityOptions.SSLExplicit);
~~~

## **Connecting to Server via Socks Proxy Sever**

Sometimes we use proxy servers for communicating with the outside world. In such cases, mail clients are not able to communicate over the Internet without specifying the proxy address. Aspose.Email provides support for versions 4, 4a and 5 of SOCKS proxy protocol. This article provides a working sample of sending email using a proxy mail server. To send an email via a proxy server:

1. Initialize Proxy with the required information, that is proxy address, port, and SOCKS version.
1. Initialize [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) with the host address, user name and password, and any other settings.
1. Set the client Proxy property to the [Proxy](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getProxy--) object created earlier.

The following code snippet shows you how to connect to a server via proxy server.

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

## **Connecting to Server via HTTP Proxy Server**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (SmtpClient client = new SmtpClient("host", 587, "username", "password")) {
    client.setProxy(proxy);
    client.send(new MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy",
            "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"));
}
~~~

## **Customize Authentication Mechanism**

Retrieve the list of authentication mechanisms that are supported by the SMTP server using the [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#getSupportedAuthentication--) method of the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) class. This method allows the client to determine which authentication methods are available for establishing a secure connection with the server. Then, using the [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#setAllowedAuthentication-long-) method which gets (or sets) enumeration of the authentication types allowed by user, choose the most appropriate authentication mechanism for the client-server communication. This allows you to set the authentication method for the mail client explicitly.

The following code sample shows how to customize email client authentication:

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.Login);
```
## **Using CRAM-MD5 authentication to Connect to a Server**

To ensure secure authentication and communication with the SMTP server, you can specify and enforce the use of CRAM-MD5 as the allowed authentication method for the SMTP client. The following code snippet shows how to configure the allowed authentication type for the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/):

```java
smtpClient.setAllowedAuthentication(SmtpKnownAuthenticationType.CramMD5);
```

## **Bind SMTP Client to Specific IP Address on Host**

The possibility of a host having multiple ports available for sending out emails cannot be ruled out. In such cases, the requirement may arise to bind the email sending client to a specific port on the host for sending out emails. This can be achieved with Aspose.Email API as well using the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#bindIPEndPoint-com.aspose.email.BindIPEndPointHandler-) property. The API [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/) can be set to use a specific IP address on the host by specifying the specific IP Endpoint. The following code snippet shows you how to bind SMTP Client to Specific IP Address on Host.


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

## **Validate Mail Server Credentials Without Sending Email**

Sometimes it is necessary to verify credentials without sending an email. Aspose.Email provides the [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/smtpclient/#validateCredentials--) method to perform this operation. If the validation is successful, the code inside the if statement is executed, typically used to perform further actions or retrieve data from the IMAP server. The following code snippet demonstrates the validation of credentials without sending an email:

```java
try (SmtpClient smtpClient = new SmtpClient(
        server.SmtpUrl, server.SmtpPort, "username", "password", SecurityOptions.Auto)) {
    smtpClient.setTimeout(4000);

    if (smtpClient.validateCredentials()) {
        // to do something
    }
}
```

## **How to Set Timeout for Mail Operations**

Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#getTimeout--) property. Note: you should not set large values to avoid long waits in your application.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~