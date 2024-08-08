---
title: Connecting to SMTP Server
type: docs
weight: 10
url: /python-net/connecting-to-smtp-server/
---


## **Connecting SSL Enabled SMTP Server**
The following properties need to be set when connecting with an SMTP server with SSL support.

- SecurityOptions
- Port

In the examples below we show how to:

1. Set a username.
1. Set a password.
1. Set the port.
1. Set security option.

The following code snippet shows you how to connect SSL enabled SMTP server.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-SMTP-SSLEnabledSMTPServer-SSLEnabledSMTPServer.py" >}}

### **Set a Timeout for the Greeting Response from the Server**

To enhance the efficiency of email client operations, developers often rely on the timeout property to limit the duration of lengthy processes. However, specifying excessively long intervals for this property can hinder operations that require extended processing times. A notable scenario is during the establishment of a connection, where relying solely on the Timeout property may result in prolonged connection times.

In specific cases, the email client may employ an automatic mode for connection establishment, systematically cycling through various connection parameters until a successful connection is established. SMTP, IMAP, and POP3 servers, upon successful connection initiation, send a greeting string to the client. Notably, servers may employ either implicit or explicit (START TLS) SSL/TLS connection initiation methods.

A potential challenge arises when the connection mode mismatches between the server and the client. For example, if the server anticipates an implicit SSL connection while the client attempts to establish a non-secured or explicitly SSL connection, the server refrains from sending a greeting string. Consequently, users experience prolonged wait times until the timeout is reached, prompting the client to move on to the next connection option.

To address this issue, developers can leverage the 'greeting_timeout' property of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class. This property enables the specification of a timeout (in milliseconds) specifically for the greeting string, minimizing the time required for automatic connection establishment. By incorporating the 'greeting_timeout' property, developers can optimize connection processes and ensure a more responsive and efficient email client experience.

The following code sample demonstrates how to implement the property into a project:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("localhost", 25, "username", "password")
client.greeting_timeout = 4000
```
## **Send an Email via Socks Proxy Server**

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

## **Connecting to Server via HTTP Proxy Server**

The code sample below demonstrates the use of an HTTP proxy to send an email via an SMTP server: 

```py
import aspose.email as ae

http_proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.smtp.SmtpClient("host", 587, "username", "password")
client.proxy = http_proxy
client.send(ae.MailMessage("sender@domain.com", "receiver@domain.com", "Sending Email via proxy", "Body"))
```

## **Connecting to Server using Supported Authentication Method**

To establish a secure and successful connection to the server for sending emails, a client can select a supported authentication method based on the server's capabilities. Aspose.Email provides properties which return lists of supported authentication methods: 

- 'supported_authentication' property gets enumeration of authentication types supported by server 
- 'allowed_authentication' property gets or sets enumeration of authentication types allowed by user 

Using these properties, developers can ensure that the SMTP client and server are compatible in terms of supported authentication methods and establish a connection with an SMTP server. The following code snippet provides an example of using 'allowed_authentication' property in a project:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.LOGIN
```

## **How to Set Timeout for Mail Operations**

Setting a timeout can be important for handling network communication effeciently. The 'timeout' property of the [SmtpClient](https://reference.aspose.com/email/python-net/aspose.email.clients.smtp/smtpclient/#smtpclient-class) class is used to specify the maximum time (in milliseconds) to wait for a response from the SMTP server. This property allows the user to control the duration the client will wait for the server to respond to a particular operation, such as a connection or sending a command. If the server takes longer than the specified time to respond, the client will throw an exception, indicating a timeout error. This helps in managing the client's behavior when interacting with the server, ensuring that the client does not hang indefinitely if the server does not respond in a timely manner. Use the following code snippet to set the timeout for the server response:

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
# 60 seconds
client.timeout = 60000
```

## **Using Cryptographic Protocols with SMTP Client**

Aspose.Email supports SSL (obsolete) and TLS cryptographic protocols to provide communications security. You can enable cryptographic encryption to protect data exchange between your application and mail servers.

```
NOTE: You should set only those versions of the protocol, which are supported by Python Framework. If some versions of the cryptographic protocol are not supported by your current version of Python Framework, they will be ignored and skipped. In this case, exceptions won't be generated. Please use 'set_supported_encryption_unsafe(value)' method of the SmtpClient class if you want to set the protocols without any compatibility checks.
```
The code example below shows you how to set TLS 1.3 for SmtpClient class instance.

```py
import aspose.email as ae

client = ae.clients.smtp.SmtpClient("host", 587, "username", "password", ae.clients.SecurityOptions.SSL_EXPLICIT)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

## **Using the CRAM-MD5 Mechanism for Authentication**

The CRAM-MD5 authentication mechanism of Aspose.Email for Python provides an additional layer of security when accessing the server. The following code snippet shows how to implement this feature into your project:

```py
client.allowed_authentication = ae.clients.smtp.SmtpKnownAuthenticationType.CRAM_MD5
```
