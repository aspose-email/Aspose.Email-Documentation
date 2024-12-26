---
title: Connect to POP3 Server
ArticleTitle: Connect to POP3 Server
type: docs
weight: 10
url: /net/connect-to-pop3-server/
---

## **Connect to POP3 Server**

The [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class allows applications to manage email boxes using the Post Office Protocol, Version 3 (POP3). This class is the major entry for developers who want to add POP3 management to their .NET applications. 

To connect to a POP3 server:

1. Create an instance of the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class.
2. Specify the host, username, and password in the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) instance.

The following code snippet shows you how to connect with the POP3 server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-ConnectingToPOP3-ConnectingToPOP3.cs" >}}

### **Connect to SSL server**

The process for connecting to an SSL enabled POP3 server is similar but requires that you set another few properties:

- [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/)
- Port

To connect to an SSL enabled POP3 server, set the [SecurityOptions](https://reference.aspose.com/email/net/aspose.email.clients/securityoptions/) and Port properties. The following code snippet shows you how to connect to an SSL enables POP3 server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.cs" >}}

### **Connect to APOP Server**

POP stands for Post Office Protocol. APOP stands for Authenticated Post Office Protocol. APOP is an extended version of the POP3 server setting that encrypts your username and password and uses an authentication mechanism designed to protect your POP3 account password when checking email. APOP authentication does not require the account password to be sent as plain text to the POP3 mail server.

### **Connect to Server via Proxy**

Proxy addresses are used for email clients to access mailboxes over the Internet. Aspose.Email provides support for versions 4, 4a and 5 of the SOCKS proxy protocol.

To retrieve email via a proxy server:

1. Initialize [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) with the required information, that is, proxy address, port, and SOCKS version.
1. Initialize [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) with the host address, user name, password, and any other settings.
1. Set the Proxy property of a client to the [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) object created above.

The following code snippet shows you how to retrieve email via proxy server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-RetrieveEmailViaProxyServer-RetrieveEmailViaProxyServer.cs" >}}

### **Connect to Server via HTTP Proxy**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-AccessMailboxViaHttpProxy-AccessPOP3MailboxViaHttpProxy.cs" >}}

### **Connect with CRAM-MD5 Authentication**

Using CRAM-MD5 authentication, Aspose.Email for .NET allows users to securely authenticate and access email servers supporting this authentication method. The code sample below shows how to use the mechanism in your project:

```cs
popClient.AllowedAuthentication = Pop3KnownAuthenticationType.CramMD5;
```

## **List Server Extensions**

[Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [GetCapabilities()](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/getcapabilities/#getcapabilities) method returns the supported extension types in the form of a string array.

### **Retrieve Server Extensions**

The following code sample demonstrates retrieving server extensions using POP3Client for Gmail server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-POP3-GetServerExtensionsUsingPop3Client-GetServerExtensionsUsingPop3Client.cs" >}}

## **Set Timeout for Mail Operations**

Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) property. Note: you should not set large values to avoid long waits in your application.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Use Cryptographic Protocols with POP3 Client**

Aspose.Email supports SSL (obsolete) and TLS cryptographic protocols to provide communications security. You can enable cryptographic encryption to protect data exchange between your application and mail servers.

> **_NOTE:_**  You should set only those versions of the protocol, which are supported by .NET Framework. If some versions of the cryptographic protocol are not supported by your current version of .NET Framework, they will be ignored and skipped. In this case, exceptions won't be generated. Please use [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method if you want to set the protocols without any compatibility checks.

The code example below shows you how to set TLS 1.3 for [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class instance.

```csharp
using (Pop3Client pop3Client = new Pop3Client("host", 995, "username", "password", SecurityOptions.Auto))
{
    pop3Client.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

In case of a specified encryption protocol is not supported in the current version of .NET Framework, the difference in behavior between [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method and [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property is the following:

- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property is used, the email client downgrades the encryption protocol to a supported level.
  
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method is used, the email client throws exceptions.
