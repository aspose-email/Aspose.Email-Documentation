---
title: Connect to POP3 Server
type: docs
weight: 10
url: /python-net/connect-to-pop3-server/
---

## **Connecting to POP3 Server**
The Pop3Client class allows applications to manage email boxes using the Post Office Protocol, Version 3 (POP3). To connect to a server, use the Pop3Client class. The Pop3Client class is the major entry for developers who want to add POP3 management to their .NET applications. This article explains how to use it. To connect to a POP3 server:

1. Create an instance of the Pop3Client class as client.
1. Specify the host, username and password in the Pop3Client instance.

The following code snippet shows you how to connect with POP3 server.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-ConnectingToPOP3-ConnectingToPOP3.py" >}}
## **Connecting to SSL server**
Connecting to a POP3 Server described how to connect to a POP3 server in three simple steps:

1. Create an instance of the Pop3Client class.
1. Specify the host, username and password.

The process for connecting to an SSL enabled POP3 server is similar but requires that you set another few properties:

- SecurityOptions
- Port

To connect to an SSL enabled POP3 server, use the Aspose.Email.Pop3.Pop3Client class and set the SecurityOptions and Port properties. The following code snippet shows you how to connect to an SSL enables POP3 server.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-POP3-SSLEnabledPOP3Server-SSLEnabledPOP3Server.py" >}}

## **Connecting with an APOP Server**

APOP or Authenticated Post Office Protocol is an extension of the traditional Post Office Protocol (POP), providing a secure method for client authentication during the email retrieval process. The key advantage of APOP is that the actual password is never transmitted over the network. An access to the user's mailbox is granted as a result of a successful hash value exchange between a server and a client.

### **Connecting to Server via Proxy**

Proxy servers are very common for communicating with the outside world. In such cases, proxy addresses are used for email clients to access mailboxes over the Internet. Aspose.Email provides support for versions 4, 4a and 5 of the SOCKS proxy protocol. Its [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class allows applications to access and manipulate messages by using the Post Office Protocol Version 3 (POP3). The 'get_mailbox_info()' method of the class retrieves information about the mailbox, such as the number of messages, total size, etc. The following code sample demonstrates the process of retrieving email using a proxy mail server: 

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
# Set proxy address, Port and Proxy
proxy_address = "192.168.203.142"
proxy_port = 1080
proxy = ae.clients.SocksProxy(proxy_address, proxy_port, ae.clients.SocksVersion.SOCKS_V5)
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Connecting to Server via HTTP Proxy**

There are various types of proxies, including HTTP proxies, SOCKS proxies, and more, each serving different purposes and providing different levels of functionality. The specific steps and configurations may vary based on the type of proxy being used. The code sample below demonstrates how to set up the POP3Client with the additional configuration of an HTTP proxy and fetch information about the mailbox:

```py
import aspose.email as ae

proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client = ae.clients.pop3.Pop3Client("pop.domain.com", "username", "password")
client.socks_proxy = proxy
mailboxInfo = client.get_mailbox_info()
```
### **Connecting to server via CRAM-MD5 authentication mechanism**

CRAM-MD5 (Challenge-Response Authentication Mechanism with MD5) is commonly used in email protocols such as POP3 and IMAP, where secure authentication is important. It provides a stronger level of security compared to plaintext password transmission. Aspose.Email for .NET allows users to securely authenticate and access email servers supporting this authentication method. 

```py
client.allowed_authentication = ae.clients.pop3.Pop3KnownAuthenticationType.CRAM_MD5
```
## **How to Set Timeout for Mail Operations**

Aspose.Email provides 'timeout' property of the [Pop3Client](https://reference.aspose.com/email/python-net/aspose.email.clients.pop3/pop3client/#pop3client-class) class to get or set the timeout for mail operations in order to prevent hanging or blocking, handle network or server issues, enhance responsiveness, and ensure efficient resource management. The following code sample shows how to implement the property into a project:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
#  60 seconds
client.timeout = 60000
```
## **Using Cryptographic Protocols with POP3 Client**

Aspose.Email supports SSL (obsolete) and TLS cryptographic protocols to provide communications security. You can enable cryptographic encryption to protect data exchange between your application and mail servers.

```
NOTE: It's important to know that you can only configure protocol versions supported by the .NET Framework. If your current .NET Framework version does not support certain protocol versions, those unsupported versions will be disregarded and skipped. This could result in a potential downgrade in TLS security level, and it's crucial to be aware that no exceptions will be raised in this situation. Developers should exercise caution to ensure the desired TLS security level is maintained based on the supported protocols in their .NET Framework environment.
```
The following code sample demonstrates how to set up a POP3 client with configurations for the TLS 1.3 encryption protocol for secure communication:

```py
import aspose.email as ae

client = ae.clients.pop3.Pop3Client("host", 995, "username", "password", ae.clients.SecurityOptions.AUTO)
client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```
In case of a specified encryption protocol is not supported in the current version of .NET Framework, the difference in behavior between 'SetSupportedEncryptionUnsafe' method and 'SupportedEncryption' property is the following:

If 'SupportedEncryption' property is used, the email client downgrades the encryption protocol to a supported level.

If 'SetSupportedEncryptionUnsafe' method is used, the email client throws exceptions.