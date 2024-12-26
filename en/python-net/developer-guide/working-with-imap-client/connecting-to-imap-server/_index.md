---
title: Connecting to IMAP Server
ArticleTitle: Connecting to IMAP Server
type: docs
weight: 10
url: /python-net/connecting-to-imap-server/
---

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class in Aspose.Email for Python serves as a component for interacting with email accounts using the IMAP protocol. IMAP (Internet Message Access Protocol) is a standard protocol for accessing and managing email messages stored on a mail server.

The [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class provides functionalities to connect to an email server over IMAP, authenticate users, retrieve emails, manage folders, and perform various operations such as reading, moving, deleting, or updating email messages. This class essentially allows developers to integrate IMAP functionality into their Python applications, enabling them to interact with email accounts in a standardized and protocol-compliant manner.

To connect to IMAP server follow three simple steps. The code sample below shows how to connect to IMAP server programmatically.

1. Create an instance of the ImapClient class.
2. Specify the hostname, port, username and password.
3. Specify the Security Options.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
```
## **Connecting to SSL Enabled IMAP Server**

The process for connecting to an SSL enabled IMAP server is similar to the one described above but requires that you set another property:

- Set Security Options to SSLImplicit.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

# Set the security mode to implicit
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```
## **Connecting to Server via Proxy**

Proxy server acts as an intermediary between a user's device and the internet. It can be used for various reasons such as improving network performance, increasing security and privacy, bypassing geographical restrictions, and caching web content to reduce bandwidth usage. Proxy servers can also be used to filter and monitor internet usage in an organization or provide anonymity for users. Aspose.Email provides support for versions 4, 4a and 5 of the SOCKS proxy protocol. The following code sample and steps demonstrate how to set up an IMAP client to connect to an IMAP server through a SOCKS proxy server for secure and private communication with the mail server.

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) and set the IMAP server details.
2. Set security options to automatic for the IMAP client.
3. Define the proxy server details, such as the IP address and port.
4. Create a SocksProxy object with the defined proxy address and port, using SOCKS version 5.
5. Set the created proxy as the proxy for the IMAP client.
6. Connect to the IMAP server and select the "Inbox" folder using the proxy for the communication.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")

client.security_options = ae.clients.SecurityOptions.AUTO
proxy_address = "192.168.203.142"
proxy_port = 1080

proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = proxy
client.select_folder("Inbox")
```
## **Connecting to Server via HTTP Proxy**

Aspose.Email also provides the functionality to access a mailbox using the HTTP proxy. The code sample below demonstrates how to set up an IMAP client to connect to an IMAP server through an HTTP proxy server for secure and private communication with the mail server.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Inbox")
```
## **Connecting to Server in Read-Only mode**

Implementing a read-only mode functionality for a mailbox involves providing the capability to control and restrict modifications to the mailbox’s permanent state, ensuring data integrity, compliance, and user experience. A True value set to this property indicates that changes are not permitted. The following code sample shows how to use this property in a project:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```
## **Connecting to Server using CRAM-MD5 authentication**

Using CRAM-MD5 authentication provides a secure way to authenticate with a mail server. With Aspose.Email you can implement this capability into your python project easily.

The following code sample demonstrates how to configure the client to accept CRAM-MD5 as one of the supported authentication methods for connecting to an IMAP server:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```
## **How to Set Timeout for Mail Operations**

The 'timeout' property of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class prevents the client from waiting indefinitely for a response when communicating with the mail server and allows for handling potential connection delays, network issues, or latency. The timeout is calculated in milliseconds. The following code snippet shows how to set a timeout period of 60,000 milliseconds (60 seconds) for the client to wait for the server response:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 seconds
client.timeout = 60000
```
## **How to Restrict Greeting Timeout**

Setting a timeout on the greeting operation between a client and a server allows the client to limit the amount of time it waits for a response from the server during the initial handshaking process. This is important because if the server is unresponsive or there are network issues, the client should not wait indefinitely for a response.

The API provides the 'greeting_timeout' property of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class to set a timeout on the greeting operation. The following code snippet shows how to restrict greeting timeout:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```
## **Using Cryptographic Protocols with IMAP Client**

Aspose.Email supports SSL (obsolete) and TLS cryptographic protocols to provide communications security. The 'supported_encryption' property of the [EmailClient](https://reference.aspose.com/email/python-net/aspose.email.clients/emailclient/#emailclient-class) class defines the versions of SSL/TLS encryption protocols to be used.

> **_NOTE:_** you may set only those versions of protocol, which are supported by .net framework. If some versions of protocol are not supported by your current version of .NET framework, they will be ignored and skipped. It may lead to downgrading TLS security level. In this case, exceptions won't be generated. Please use 'set_supported_encryption_unsafe(value)' method if you want to set the protocols without any compatibility checks.

The code example below shows you how to set TLS 1.3 for [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class instance.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
In case of a specified encryption protocol is not supported in the current version of .NET Framework, the difference in behavior between 'set_supported_encryption_unsafe(value)' method and 'supported_encryption' property is the following:

If 'supported_encryption' property is used, the email client downgrades the encryption protocol to a supported level.
If 'set_supported_encryption_unsafe(value)' method is used, the email client throws exceptions.
