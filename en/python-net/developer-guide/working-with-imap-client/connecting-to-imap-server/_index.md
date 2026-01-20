---
title: Connect to IMAP Servers in Python Using Aspose.Email
ArticleTitle: Connect to IMAP Servers in Python
type: docs
weight: 10
url: /python-net/connect-to-imap-servers-python/
---

Aspose.Email for Python via .NET includes the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class, which allows developers to connect to mail servers using the IMAP (Internet Message Access Protocol). This class enables secure and efficient email management within Python applications, including retrieving, reading, moving, deleting, and updating email messages.

Using the IMAP client, you can authenticate users, manage mailbox folders, connect through SSL, set custom timeouts, and access email accounts through proxy servers or CRAM-MD5 authentication.

## **Basic IMAP Connection**

To connect to an IMAP server using Aspose.Email, follow these three simple steps: 

1. Create an instance of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class.
2. Specify the hostname, port, username and password.
3. Specify the desired security option.

The code sample below shows how to connect to IMAP server programmatically:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
```

## **Enable SSL for IMAP Connections**

To connect to an SSL-enabled IMAP server, set the [security_options](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#properties) property to SSLImplicit:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

# Set the security mode to implicit
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
```

## **Connect via SOCKS Proxy**

Aspose.Email supports SOCKS versions 4, 4a, and 5 for proxy-based connections. Use the following steps to connect through a SOCKS proxy:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.security_options = ae.clients.SecurityOptions.AUTO

proxy = ae.clients.SocksProxy("192.168.203.142", 1080, ae.clients.SocksVersion.SOCKS_V5)
client.proxy = proxy

client.select_folder("Inbox")
```

## **Connecting to Server via HTTP Proxy**

Aspose.Email also allows IMAP connections through an HTTP proxy:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", "username", "password")
client.proxy = ae.clients.HttpProxy("18.222.124.59", 8080)
client.select_folder("Inbox")
```

## **Read-Only Mailbox Access**

To prevent changes to mailbox contents, enable read-only mode. The [read_only](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#properties) property set to *True* indicates that changes are not permitted. The following code sample shows how to use this property in a project:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.security_options = ae.clients.SecurityOptions.SSL_EXPLICIT
client.read_only = True
```

## **Use CRAM-MD5 Authentication**

For enhanced security, configure the client to use CRAM-MD5 authentication:

The following code sample demonstrates how to configure the client to accept CRAM-MD5 as one of the supported authentication methods for connecting to an IMAP server:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")
client.allowed_authentication = ae.clients.imap.ImapKnownAuthenticationType.CRAM_MD5
```

## **Set Operation Timeout**

Prevent the client from waiting indefinitely by setting a timeout (in milliseconds):

The following code snippet shows how to set a timeout period of 60,000 milliseconds (60 seconds) for the client to wait for the server response:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)
#  60 seconds
client.timeout = 60000
```

## **Set Greeting Timeout**

Control how long the client waits during the initial handshake with the mail server.

The following code snippet shows how to restrict greeting timeout using the *greeting_timeout* property of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class:  

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd")

client.greeting_timeout = 4000
client.select_folder(ae.clients.imap.ImapFolderInfo.IN_BOX)
```

## **Use TLS with the IMAP Client**

Aspose.Email supports TLS and SSL for secure communication. Use the [supported_encryption](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#properties) property to define acceptable protocol versions.

> **_NOTE:_** you may set only those versions of protocol, which are supported by .net framework. If some versions of protocol are not supported by your current version of .NET framework, they will be ignored and skipped. It may lead to downgrading TLS security level. In this case, exceptions won't be generated. Please use 'set_supported_encryption_unsafe(value)' method if you want to set the protocols without any compatibility checks.

The code example below shows you how to set TLS 1.3 for [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class instance.

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

client.supported_encryption = ae.clients.base.EncryptionProtocols.TLS13
```

In case, a specified encryption protocol is not supported in the current version of .NET Framework, the difference in behavior between *set_supported_encryption_unsafe(value)* method and *supported_encryption* property is the following:

- If *supported_encryption* property is used, the email client downgrades the encryption protocol to a supported level.
- If *set_supported_encryption_unsafe(value)* method is used, the email client throws exceptions.

## **Validate IMAP Server Credentials**

To establish a secure connection to an IMAP server before undertaking further actions, the user credentials are checked and validated. The *validate_credentials* method of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class helps to check if the provided username and password are correct. If the credentials are indeed valid, the client can successfully authenticate with the IMAP server. The following code sample shows how to implement this method into your project:

```py
import aspose.email as ae

with ae.clients.imap.ImapClient("your imap server", 993, "your username", "your password", ae.clients.SecurityOptions.AUTO) as client:
    client.timeout = 4000

    if client.validate_credentials():
        # Further actions
```

## **Enable IMAP Activity Logging**

Activity logging involves recording server connections, transmission details of messages sent and received, error messages during email processing, and any other actions performed by the client or server. To track IMAP client activity and interactions with the server, use the following code sample which uses the *log_file_name* property of the [ImapClient](https://reference.aspose.com/email/python-net/aspose.email.clients.imap/imapclient/#imapclient-class) class to log the information to the specified log file:

```py
import aspose.email as ae

client = ae.clients.imap.ImapClient("imap.domain.com", 993, "user@domain.com", "pwd", ae.clients.SecurityOptions.SSL_IMPLICIT)

# Set the path to the log file using the LogFileName property.
client.log_file_name = "C:\\Aspose.Email.IMAP.log"
# Set the UseDateInLogFileName property if it is necessary.
client.use_date_in_log_file_name = False
```