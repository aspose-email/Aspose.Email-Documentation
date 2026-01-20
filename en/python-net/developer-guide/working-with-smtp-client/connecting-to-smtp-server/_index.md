---
title: SMTP Client Connection Setup
ArticleTitle: Connect to SMTP Server
type: docs
weight: 10
url: /python-net/connect-to-smtp-server-python/
---


## **Connect to SMTP Server with SSL**

To establish a secure connection with an SMTP server that supports SSL, you need to configure the following key properties of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/) class:

- **Host:** The address of the SMTP server (e.g., smtp.gmail.com)

- **Port:** The port used for SSL-enabled communication (commonly 465 for implicit SSL or 587 for explicit SSL/TLS)

- **Username:** The account name used for authentication

- **Password:** The password for the SMTP account

- **Security Options:** The type of encryption to be used (SSLEXPLICIT, SSLIMPLICIT, etc.)


The following code sample demonstrates how to configure and connect to an SSL-Enabled SMTP server:

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SSLEnabledSMTPServer-SSLEnabledSMTPServer.py" >}}

### **Set a Timeout for the Greeting Response from the Server**

When establishing a connection with an SMTP server, the server typically sends a greeting string after a successful connection. This response confirms that the server is ready to proceed with the communication.

In some scenarios, email clients operate in automatic connection mode, trying multiple combinations of security protocols and ports (such as implicit SSL or STARTTLS) to establish a successful connection. If the client's configuration doesn't match the server's expected security mode, the server won't send the greeting string. This mismatch causes the client to wait until the general timeout expires before trying the next combination — resulting in slow connection handling.

To improve this behavior, Aspose.Email provides the `greeting_timeout` property in the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class. This property sets a specific timeout (in milliseconds) for waiting on the server greeting string. If the greeting isn’t received within the specified interval, the client immediately attempts the next connection configuration — significantly speeding up automatic connection processes.

The following code sample demonstrates how to implement the property into a project:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("localhost", 25, "username", "password")
client.greeting_timeout = 4000
```

## **Send Emails via SMTP using a SOCKS Proxy**

Aspose.Email provides support for versions 4, 4a and 5 of SOCKS proxy protocol. The following code sample demonstrates how to send an email using SMTP with SOCKS proxy: 

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("smtp.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.SSL_IMPLICIT
# proxy address
proxy_address = "192.168.203.142"
#proxy port
proxy_port = 1080
socks_proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = socks_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Implement socks proxy protocol for versions 4, 4a, 5 (only Username/Password authentication)"))
```

## **Send Emails via SMTP using an HTTP Proxy**

The code sample below demonstrates the use of an HTTP proxy to send an email via an SMTP server: 

```py
import aspose.email as ae

http_proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.smtp.SmtpClient("host", 587, "username", "password")
client.proxy = http_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Body"))
```

## **Select Supported SMTP Authentication Methods in Python**

To ensure a secure and compatible connection to an SMTP server, it's important to use an authentication method supported by both the client and the server. Aspose.Email for Python via .NET provides built-in [properties](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#properties) to manage this:

- `supported_authentication` — retrieves a list of authentication methods supported by the SMTP server.

- `allowed_authentication` — gets or sets the authentication methods that the client is permitted to use.

By using these properties, developers can align the client's capabilities with the server's requirements and avoid authentication failures during the connection process.

The following code snippet demonstrates how to specify the allowed SMTP authentication method using the `allowed_authentication` property:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.LOGIN
```

## **Set SMTP Server Timeout**

When sending emails over a network, setting an appropriate timeout is essential for preventing your application from hanging if the server fails to respond. The `timeout` property of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class in Aspose.Email for Python via .NET allows you to define the maximum wait time (in milliseconds) for server responses.

This property applies to operations such as establishing a connection or sending SMTP commands. If the server does not respond within the specified duration, the client throws a timeout exception, helping you handle unresponsive servers more effectively.  

Use the following code snippet to set the timeout for the server response:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
# 60 seconds
client.timeout = 60000
```

## **Enable TLS Encryption for Secure SMTP Connections**

Aspose.Email supports secure communication with SMTP servers using SSL and TLS cryptographic protocols. These protocols help protect the data exchanged between your application and the mail server, ensuring confidentiality and integrity during transmission.

```
NOTE: Only versions of SSL/TLS supported by your current Python framework can be applied. Unsupported protocol versions will be silently ignored without raising exceptions. If you need to bypass compatibility checks and explicitly set the encryption protocols, use the `set_supported_encryption_unsafe(value)` method of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class.
```

The following code example demonstrates how to set TLS 1.3 for SMTP communication:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

## **Using the CRAM-MD5 Mechanism for Authentication**

Aspose.Email for Python via .NET supports the CRAM-MD5 authentication mechanism, which enhances security by avoiding the transmission of plain-text passwords during SMTP authentication. This method is particularly useful when connecting to servers that require challenge-response authentication.

To enable CRAM-MD5 authentication, set the `allowed_authentication` property of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class to CRAM_MD5, as shown in the following code sample:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.CRAM_MD5
```
