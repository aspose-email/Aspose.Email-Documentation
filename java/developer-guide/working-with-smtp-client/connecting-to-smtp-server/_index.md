---
title: Connecting to SMTP Server
type: docs
weight: 10
url: /java/connecting-to-smtp-server/
---


The following properties need to be set when connecting with an SMTP server with SSL support.

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/SecurityOptions)
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
1. Initialize [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient) with the host address, user name and password, and any other settings.
1. Set the client's Proxy property to the [Proxy](https://reference.aspose.com/email/java/com.aspose.email/EmailClient#setProxy\(com.aspose.email.Proxy\)) object created earlier.

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
## **Bind SMTP Client to Specific IP Address on Host**
The possibility of a host having multiple ports available for sending out emails cannot be ruled out. In such cases, the requirement may arise to bind the email sending client to a specific port on the host for sending out emails. This can be achieved with Aspose.Email API as well using the [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient) [bindIPEndPoint](https://reference.aspose.com/email/java/com.aspose.email/EmailClient#bindIPEndPoint\(com.aspose.email.BindIPEndPointHandler\)) property. The API's [SmtpClient](https://reference.aspose.com/email/java/com.aspose.email/SmtpClient) can be set to use a specific IP address on the host by specifying the specific IP Endpoint. The following code snippet shows you how to bind SMTP Client to Specific IP Address on Host.


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

## **How to Set Timeout for Mail Operations**
Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/java/com.aspose.email/EmailClient#setTimeout\(int\)) property. Note: you should not set large values to avoid long waits in your application.

~~~Java
try (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~