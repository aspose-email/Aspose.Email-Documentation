---
title: Connecting to IMAP Server
type: docs
weight: 10
url: /net/connecting-to-imap-server/
---


The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class allows applications to manage IMAP mailboxes using the IMAP protocol. The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class is used to connect to IMAP mail servers and manage emails in the IMAP email folders. To connect to an IMAP server

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Specify the hostname, username, and password in the [ImapClient constructor](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/imapclient/#constructor_8).

**Note, password restrictions must meet the requirements of the server. The email client doesn't add password restrictions.**

Once the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) instance is initiated, the next call to any operation using this instance will connect to the server. The following code snippet shows you how to connect to an IMAP server using the steps above.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
```

## **Connecting with SSL Enabled IMAP Server**

[Connecting with IMAP Server](/email/net/connecting-to-imap-server#connecting-with-imap-server) described how to connect to an IMAP server in four simple steps:

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class.
1. Specify the hostname, username, and password.
1. Specify the port.
1. Specify the Security Options.

The process for connecting to an SSL enabled IMAP server is similar but requires that you set another few properties:

- Set Security Options to SSLImplicit.

The following code snippet shows how to

1. Set a username, password, and port.
1. Set security option.


```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Create an instance of the ImapClient class
ImapClient client = new ImapClient("imap.domain.com", 993, "user@domain.com", "pwd");
            
// Set the security mode to implicit
client.SecurityOptions = SecurityOptions.SSLImplicit;
```

## **Connecting to Server via Proxy**

Proxy servers are commonly used to communicate with the outside world. In such cases, mail clients are not able to communicate over the Internet without specifying the proxy address. Aspose.Email provides support for versions 4, 4a and 5 of the SOCKS proxy protocol. This article provides a working sample of accessing the mailbox using a proxy mail server. To access the mailbox via a proxy server:

1. Initialize [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) with the required information, that is proxy address, port, and SOCKS version.
1. Initialize [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) with host address, user name, password, and any other settings.
1. Set the client's [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) property of the client to the [SocksProxy](https://reference.aspose.com/email/net/aspose.email.clients/socksproxy/) object created above.

The following code snippet shows you how to retrieve mailbox via a proxy server.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
// Connect and log in to IMAP and set SecurityOptions
ImapClient client = new ImapClient("imap.domain.com", "username", "password");
client.SecurityOptions = SecurityOptions.Auto;
            
string proxyAddress = "192.168.203.142"; // proxy address
int proxyPort = 1080; // proxy port
SocksProxy proxy = new SocksProxy(proxyAddress, proxyPort, SocksVersion.SocksV5);

// Set the proxy
client.Proxy = proxy;
           
try
{
    client.SelectFolder("Inbox");
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

## **Connecting to Server via HTTP Proxy**

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
HttpProxy proxy = new HttpProxy("18.222.124.59", 8080);
using (ImapClient client = new ImapClient("imap.domain.com", "username", "password"))
{
    client.Proxy = proxy;
    client.SelectFolder("Inbox");
}
```

## **Connecting to Server in Read-Only mode**

The [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class provides a [ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) property which when set to **true**, indicates that no changes should be made to the permanent state of the mailbox. The following code sample demonstrates the use of [ImapClient.ReadOnly](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/readonly/) property. It gets the count of unread messages, then fetches one message and then gets the count of unread messages again in read-only mode. The count of the unread messages remains the same indicating that the permanent state of the mailbox was not changed.

```csharp
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-.NET
ImapClient imapClient = new ImapClient();
imapClient.Host = "<HOST>";
imapClient.Port = 993;
imapClient.Username = "<USERNAME>";
imapClient.Password = "<PASSWORD>";
imapClient.SupportedEncryption = EncryptionProtocols.Tls;
imapClient.SecurityOptions = SecurityOptions.SSLImplicit;

ImapQueryBuilder imapQueryBuilder = new ImapQueryBuilder();
imapQueryBuilder.HasNoFlags(ImapMessageFlags.IsRead); /* get unread messages. */
MailQuery query = imapQueryBuilder.GetQuery();

imapClient.ReadOnly = true;
imapClient.SelectFolder("Inbox");
ImapMessageInfoCollection messageInfoCol = imapClient.ListMessages(query);
Console.WriteLine("Initial Unread Count: " + messageInfoCol.Count());
if (messageInfoCol.Count() > 0)
{
    imapClient.FetchMessage(messageInfoCol[0].SequenceNumber);

    messageInfoCol = imapClient.ListMessages(query);
    // This count will be equal to the initial count
    Console.WriteLine("Updated Unread Count: " + messageInfoCol.Count());
}
else
{
    Console.WriteLine("No unread messages found");
}
```
## **Connecting to Server using CRAM-MD5 authentication**

For secure authentication and access to the email server, Aspose.Email for .NET offers a CRAM-MD5 authentication method.
The following code snippet will show you how it works with the ImapClient:

```cs
imapClient.AllowedAuthentication = ImapKnownAuthenticationType.CramMD5;
```

## **How to Set Timeout for Mail Operations**

Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) property. Note: you should not set large values to avoid long waits in your application.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **How to Restrict Greeting Timeout**

The IMAP client may use the automatic mode to establish a connection. In this mode, the IMAP client goes through all possible connection parameters until the connection is established. An IMAP server in case of the correct connection sends a greeting string to the client. Servers may use implicit or explicit (START TLS) SSL/TLS connection initiation. If connection mode is mismatched (for instance, the server waits for an implicit SSL connection but the client tries to establish a non-secured or explicit SSL connection), the server won't send a greeting string and the user will wait a long time until the timeout reaches a greeting string, and the client goes to the next connection option. To avoid this problem, the GreetingTimeout property has been introduced. This property allows you to set the timeout for the greeting string, and reduce the time of automatic connection establishment.

```cs
using (ImapClient client = new ImapClient("localhost", 993, "username", "password"))
{
    client.GreetingTimeout = 4000;
    client.SelectFolder(ImapFolderInfo.InBox);
}
```

## **Using Cryptographic Protocols with IMAP Client**

Aspose.Email supports SSL (obsolete) and TLS cryptographic protocols to provide communications security. You can enable cryptographic encryption to protect data exchange between your application and mail servers.

> **_NOTE:_**  You should set only those versions of the protocol, which are supported by .NET Framework. If some versions of the cryptographic protocol are not supported by your current version of .NET Framework, they will be ignored and skipped. In this case, exceptions won't be generated. Please use [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method if you want to set the protocols without any compatibility checks.

The code example below shows you how to set TLS 1.3 for [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class instance.

```csharp
using (ImapClient imapClient = new ImapClient("host", 993, "username", "password", SecurityOptions.SSLImplicit))
{
    imapClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

In case of a specified encryption protocol is not supported in the current version of .NET Framework, the difference in behavior between [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method and [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property is the following:
- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property is used, the email client downgrades the encryption protocol to a supported level.
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method is used, the email client throws exceptions.
