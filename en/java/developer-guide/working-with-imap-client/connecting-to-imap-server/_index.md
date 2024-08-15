---
title: Connecting to IMAP Server
type: docs
weight: 10
url: /java/connecting-to-imap-server/
---


The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class allows applications to manage IMAP mailboxes using the IMAP protocol. The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class is used to connect to IMAP mail servers and manage emails in the IMAP email folders. To connect to an IMAP server

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Specify the hostname, username, and password in the [ImapClient constructor](https://reference.aspose.com/email/java/com.aspose.email/imapclient/).

Once the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) instance is initiated, the next call to any operation using this instance will connect to the server. The following code snippet shows you how to connect to an IMAP server using the steps above.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
~~~

## **Connecting with SSL Enabled IMAP Server**

[Connecting with IMAP Server](/email/java/connecting-to-imap-server#connecting-with-imap-server) described how to connect to an IMAP server in four simple steps:

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class.
1. Specify the hostname, username, and password.
1. Specify the port.
1. Specify the [Security Options](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/).

The process for connecting to an SSL enabled IMAP server is similar but requires that you set another few properties:

- Set [Security Options](https://reference.aspose.com/email/java/com.aspose.email/securityoptions/) to SSLImplicit.

The following code snippet shows how to

1. Set a username, password, and port.
1. Set security option.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of the ImapClient class
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");

// Set the security mode to implicit
client.setSecurityOptions(SecurityOptions.SSLImplicit);
~~~

## **Connecting to Server via Proxy**

Proxy servers are commonly used to communicate with the outside world. In such cases, mail clients are not able to communicate over the Internet without specifying the proxy address. Aspose.Email provides support for versions 4, 4a and 5 of the SOCKS proxy protocol. This article provides a working sample of accessing the mailbox using a proxy mail server. To access the mailbox via a proxy server:

1. Initialize [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) with the required information, that is proxy address, port, and SOCKS version.
1. Initialize [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) with host address, user name, password, and any other settings.
1. Set the client [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) property to the [SocksProxy](https://reference.aspose.com/email/java/com.aspose.email/socksproxy/) object created above.

The following code snippet shows you how to retrieve mailbox via a proxy server.

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

## **Connecting to Server via HTTP Proxy**

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

## **Customize Authentication Mechanism**

Retrieve the list of authentication mechanisms that are supported by the IMAP server using the [getSupportedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#getSupportedAuthentication--) method of the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class. This method allows the client to determine which authentication methods are available for establishing a secure connection with the server. Then, using the [setAllowedAuthentication](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setAllowedAuthentication-long-) method which gets (or sets) enumeration of the authentication types allowed by user, choose the most appropriate authentication mechanism for the client-server communication. This allows you to set the authentication method for the mail client explicitly.

The following code sample shows how to customize email client authentication:

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.Plain);
```

## **Connecting to Server in Read-Only mode**

The [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/) class provides a [ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) property which when set to **true**, indicates that no changes should be made to the permanent state of the mailbox. The following code sample demonstrates the use of [ImapClient.ReadOnly](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setReadOnly-boolean-) property. It gets the count of unread messages, then fetches one message and then gets the count of unread messages again in read-only mode. The count of the unread messages remains the same indicating that the permanent state of the mailbox was not changed.

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

## **Using CRAM-MD5 authentication to Connect to a Server**

To ensure secure authentication and communication with the IMAP server, you can specify and enforce the use of CRAM-MD5 as the allowed authentication method for the IMAP client. The following code snippet shows how to configure the allowed authentication type for the [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/imapclient/):

```java
imapClient.setAllowedAuthentication(ImapKnownAuthenticationType.CramMD5);
```
## **Validate Mail Server Credentials Without Sending Email**

Sometimes it is necessary to verify credentials without sending an email. Aspose.Email provides the [validateCredentials()](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#validateCredentials--) method to perform this operation. If the validation is successful, the code inside the if statement is executed, typically used to perform further actions or retrieve data from the IMAP server. The following code snippet demonstrates the validation of credentials without sending an email:

```java
try (ImapClient imapClient = new ImapClient(
        server.ImapUrl, server.ImapPort, "username", "password", SecurityOptions.Auto)) {
    imapClient.setTimeout(4000);

    if (imapClient.validateCredentials()) {
        // to do something
    }
}
```

## **How to Set Timeout for Mail Operations**

Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/java/com.aspose.email/imapclient/#setTimeout-int-) property. Note: you should not set large values to avoid long waits in your application.

~~~Java
try (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.setTimeout(60000); // 60 seconds

    // some code...
}
~~~

## **How to Restrict Greeting Timeout**

The IMAP client may use the automatic mode to establish a connection. In this mode, the IMAP client goes through all possible connection parameters until the connection is established. An IMAP server in case of the correct connection sends a greeting string to the client. Servers may use implicit or explicit (START TLS) SSL/TLS connection initiation. If connection mode is mismatched (for instance, the server waits for an implicit SSL connection but the client tries to establish a non-secured or explicit SSL connection), the server won't send a greeting string and the user will wait a long time until the timeout reaches a greeting string, and the client goes to the next connection option. To avoid this problem, the GreetingTimeout has been introduced. This property allows you to set the timeout for the greeting string, and reduce the time of automatic connection establishment.

```java
ImapClient imapClient = new ImapClient();
imapClient.setGreetingTimeout(4000);
```
