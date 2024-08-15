---
title: Connect to POP3 Server
type: docs
weight: 10
url: /java/connect-to-pop3-server/
---


The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class allows applications to manage email boxes using the Post Office Protocol, Version 3 (POP3). To connect to a server, use the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class. The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class is the major entry for developers who want to add POP3 management to their .NET applications. This article explains how to use it. To connect to a POP3 server:

1. Create an instance of the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.
1. Specify the host, username, and password in the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) instance.

The following code snippet shows you how to connect with the POP3 server.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Connected to POP3 server.");
~~~

## **Connecting to SSL Server**

[Connecting to a POP3 Server](#connecting-to-pop3-server) described how to connect to a POP3 server in three simple steps:

1. Create an instance of the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.
1. Specify the host, username, and password.

The process for connecting to an SSL enabled POP3 server is similar but requires that you set another few properties:

- [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/)
- Port

To connect to an SSL enabled POP3 server, use the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class and set the [SecurityOptions](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) and Port properties. The following code snippet shows you how to connect to an SSL enabled POP3 server.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username and password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
System.out.println("Connecting to POP3 server using SSL.");
~~~

## **Connecting with an APOP Server**

POP stands for Post Office Protocol. APOP stands for Authenticated Post Office Protocol. APOP is an extended version of the POP3 server setting that encrypts your username and password and uses an authentication mechanism designed to protect your POP3 account password when checking email. APOP authentication does not require the account password to be sent as plain text to the POP3 mail server.

## **Connecting to Server via Proxy**

Proxy servers are very common for communicating with the outside world. In such cases, proxy addresses are used for email clients to access mailboxes over the Internet. Aspose.Email provides support for versions 4, 4a and 5 of the SOCKS proxy protocol. This article provides a working sample of retrieving email using a proxy mail server. To retrieve email via a proxy server:

1. Initialize [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) with the required information, that is, proxy address, port, and SOCKS version.
1. Initialize [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) with the host address, user name, password, and any other settings.
2. Set the client Proxy property to the [Proxy](https://reference.aspose.com/email/java/com.aspose.email/proxy/) object created above.

The following code snippet shows you how to retrieve emails via proxy server.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client("pop.domain.com", "username", "password");

// Set proxy address, Port and Proxy
String proxyAddress = "192.168.203.142";
int proxyPort = 1080;
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);
client.setProxy(proxy);
Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
~~~

## **Connecting to a Server via HTTP Proxy**

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
try (Pop3Client client = new Pop3Client("imap.domain.com", "username", "password")) {
    client.setProxy(proxy);
    Pop3MailboxInfo mailboxInfo = client.getMailboxInfo();
}
~~~

## **Customize Authentication Mechanism**

Retrieve the list of authentication mechanisms that are supported by the POP3 server using the [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getSupportedAuthentication--) method of the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class. This method allows the client to determine which authentication methods are available for establishing a secure connection with the server. Then, using the [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setAllowedAuthentication-long-) method which gets (or sets) enumeration of the authentication types allowed by user, choose the most appropriate authentication mechanism for the client-server communication. This allows you to set the authentication method for the mail client explicitly.

The following code sample shows how to customize email client authentication:

```java
pop3Client.setAllowedAuthentication(Pop3KnownAuthenticationType.Plain);
```

## **OAuth 2.0 protocol support for authorization**

OAuth 2.0 provides  authorization 

Pop3Client supports OAuth 2.0 providing specific authorization ways for applications. The following constructors are used to initialize POP3Client using OAuth: 

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

## **Validate Mail Server Credentials Without Sending Email**

Sometimes it is necessary to verify credentials without sending an email. Aspose.Email provides the [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#validateCredentials--) method to perform this operation. If the validation is successful, the code inside the if statement is executed, typically used to perform further actions or retrieve data from the IMAP server. The following code snippet demonstrates the validation of credentials without sending an email:

```java
try (Pop3Client pop3Client = new Pop3Client(
        server.Pop3Url, server.Pop3Port, "userName", "password", SecurityOptions.Auto)) {
    pop3Client.setTimeout(4000);

    if (pop3Client.validateCredentials()) {
        // to do something
    }
}
```

## **Using CRAM-MD5 authentication to Connect to a Server**

To ensure secure authentication and communication with the POP3 server, you can specify and enforce the use of CRAM-MD5 as the allowed authentication method for the POP3 client. The following code snippet shows how to configure the allowed authentication type for the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/):

```java
popClient.setAllowedAuthentication(Pop3KnownAuthenticationType.CramMD5);
```
## **How to Set Timeout for Mail Operations**

Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/java/com.aspose.email/emailclient/#setTimeout-int-) property. Note: you should not set large values to avoid long waits in your application.

~~~Java
try (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.setTimeout(60000); // 60 seconds

    // some code...
}
~~~