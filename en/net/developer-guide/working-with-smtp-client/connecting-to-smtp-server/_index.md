---
title: Connecting to SMTP Server
type: docs
weight: 10
url: /net/connecting-to-smtp-server/
---

When working with email clients, certain operations may take a considerable amount of time to execute. To prevent these operations from running indefinitely, users can make use of the [EmailClient.Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) property. It's important to note that the values assigned to this property should have long enough intervals to accommodate lengthy operations.

However, relying solely on the Timeout property may cause connection establishment to take longer than expected. This can occur when the email client uses the automatic mode for connection establishment. In this mode, the client cycles through various connection parameters until a connection is established.

When connecting to SMTP, IMAP, and POP3 servers, a greeting string is sent to the client upon successful connection establishment. Servers may use implicit or explicit (START TLS) SSL/TLS connection initiation. In cases where the connection mode is mismatched (for example, the server is expecting an implicit SSL connection while the client tries to establish a non-secured or explicit SSL connection), the server will not send a greeting string.

As a result, the user may wait for an extended period until the timeout is reached, and the client moves on to the next connection option.

To address this issue, the [GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) property has been introduced. This property allows users to set a timeout for the greeting string, reducing the time it takes to establish an automatic connection. By implementing the **GreetingTimeout property**, users can optimize their email client's performance and avoid lengthy wait times during connection establishment.

The following code sample shows how to set the [EmailClient.GreetingTimeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/greetingtimeout/) property:

```cs
using (SmtpClient client = new SmtpClient("localhost", 25, "username", "password"))
{
    client.GreetingTimeout = 4000;
}
```

## **Connecting to Server via Socks Proxy Sever**

Sometimes we use proxy servers for communicating with the outside world. In such cases, mail clients are not able to communicate over the Internet without specifying the proxy address. Aspose.Email provides support for versions 4, 4a and 5 of SOCKS proxy protocol. This article provides a working sample of sending email using a proxy mail server. To send an email via a proxy server:

1. Initialize Proxy with the required information, that is proxy address, port, and SOCKS version.
1. Initialize [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) with the host address, user name and password, and any other settings.
1. Set the client's Proxy property to the [Proxy](https://reference.aspose.com/email/net/aspose.email.clients/proxy/) object created earlier.

The following code snippet shows you how to connect to a server via proxy server.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaProxyServer-SendEmailViaProxyServer.cs" >}}

## **Connecting to Server via HTTP Proxy Server**

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SendEmailViaHttpProxy-SendEmailViaHttpProxy.cs" >}}

## **Connecting to Server using Supported Authentication Method**

Aspose.Email for .NET offers properties allowing to check which authentication methods can be used for establishing a secure connection with the SMTP server before sending an email:
- the [SmtpClient.SupportedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/supportedauthentication/) property returns a list of authentication methods supported by the SMTP server. 
- the [SmtpClient.AllowedAuthentication](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/allowedauthentication/) property returns a list of authentication methods defined by the user.

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.Login;
```

## **Loading SMTP Authentication Information from CONFIG File**

The [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class allows applications to read authentication information like username and password and the host address and port number directly from a configuration file. Using the .NET native configuration tag, as shown below, enables the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class to read this information through the Configuration Manager also available in .NET framework. For Aspose.Email to be able to read a configuration file, it needs to be in the correct format. Below, we show an example XML configuration file followed by the code that reads it. The following code snippet shows you how to load SMTP authentication information from CONFIG File.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "LoadingAuthenticationInformationFromAFile.xml" >}}

Once the configuration settings are defined, load these settings directly into an instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class using one of its overloaded constructors. The following code snippet demonstrates reading configuration settings from the configuration file and loading them directly into the instance of the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/).

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-LoadSmtpConfigFile-LoadSmtpConfigFile.cs" >}}

## **Bind SMTP Client to Specific IP Address on Host**

The possibility of a host having multiple ports available for sending out emails cannot be ruled out. In such cases, the requirement may arise to bind the email sending client to a specific port on the host for sending out emails. This can be achieved with Aspose.Email API as well using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) [BindIPEndPoint](https://apireference.aspose.com/email/net/aspose.email.clients/emailclient/events/bindipendpoint) property. The API's [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) can be set to use a specific IP address on the host by specifying the specific IP Endpoint. The following code snippet shows you how to bind SMTP Client to Specific IP Address on Host.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-SMTP-SetSpecificIpAddress-SetSpecificIpAddress.cs" >}}

## **How to Set Timeout for Mail Operations**

Each mail operation takes some time depending on many factors (network delays, data size, server performance, etc.). You can set a timeout for all mail operations. The code example below shows you how to do that using the [Timeout](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/timeout/) property. Note: you should not set large values to avoid long waits in your application.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.Timeout = 60000; // 60 seconds

    // some code...
}
```

## **Using Cryptographic Protocols with SMTP Client**

Aspose.Email supports SSL (obsolete) and TLS cryptographic protocols to provide communications security. You can enable cryptographic encryption to protect data exchange between your application and mail servers.

> **_NOTE:_**  You should set only those versions of the protocol, which are supported by .NET Framework. If some versions of the cryptographic protocol are not supported by your current version of .NET Framework, they will be ignored and skipped. In this case, exceptions won't be generated. Please use [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method if you want to set the protocols without any compatibility checks.

The code example below shows you how to set TLS 1.3 for [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class instance.

```csharp
using (SmtpClient smtpClient = new SmtpClient("host", 587, "username", "password", SecurityOptions.SSLExplicit))
{
    smtpClient.SupportedEncryption = EncryptionProtocols.Tls13;

    // some code...
}
```

In case of a specified encryption protocol is not supported in the current version of .NET Framework, the difference in behavior between [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method and [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property is the following:
- If [SupportedEncryption](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/supportedencryption/) property is used, the email client downgrades the encryption protocol to a supported level.
- If [SetSupportedEncryptionUnsafe](https://reference.aspose.com/email/net/aspose.email.clients/emailclient/setsupportedencryptionunsafe/#setsupportedencryptionunsafe) method is used, the email client throws exceptions.

##  **Using the CRAM-MD5 Mechanism for Authentication**

The CRAM-MD5 authentication mechanism of Aspose.Email for .NET provides an additional layer of security when accessing the server. The following code snippet shows how to implement this feature into your project:

```cs
smtpClient.AllowedAuthentication = SmtpKnownAuthenticationType.CramMD5;
```