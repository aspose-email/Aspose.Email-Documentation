---
title: Connecting to IMAP Server
type: docs
weight: 10
url: /java/connecting-to-imap-server/
---


The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class allows applications to manage IMAP mailboxes using the IMAP protocol. The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class is used to connect to IMAP mail servers and manage emails in the IMAP email folders. To connect to an IMAP server

1. Create an instance of the [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class.
1. Specify the hostname, username, and password in the [ImapClient constructor](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#ImapClient\(java.lang.String,%20int,%20java.lang.String,%20java.lang.String,%20int\)).

Once the [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) instance is initiated, the next call to any operation using this instance will connect to the server. The following code snippet shows you how to connect to an IMAP server using the steps above.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an imapclient with host, user and password
ImapClient client = new ImapClient("localhost", "user", "password");
~~~
## **Connecting with SSL Enabled IMAP Server**
[Connecting with IMAP Server](/email/java/connecting-to-imap-server#connecting-with-imap-server) described how to connect to an IMAP server in four simple steps:

1. Create an instance of the [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class.
1. Specify the hostname, username, and password.
1. Specify the port.
1. Specify the Security Options.

The process for connecting to an SSL enables IMAP server is similar but requires that you set another few properties:

- Set Security Options to SSLImplicit.

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

1. Initialize [SocksProxy](https://apireference.aspose.com/email/java/com.aspose.email/socksproxy) with the required information, that is proxy address, port, and SOCKS version.
1. Initialize [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) with host address, user name, password, and any other settings.
1. Set the client's [SocksProxy](https://apireference.aspose.com/email/java/com.aspose.email/socksproxy) property to the [SocksProxy](https://apireference.aspose.com/email/java/com.aspose.email/socksproxy) object created above.

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
## **Connecting to Server in Read-Only mode**
The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class provides a [ReadOnly](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#getReadOnly\(\)) property which when set to **true**, indicates that no changes should be made to the permanent state of the mailbox. The following code sample demonstrates the use of [ImapClient.ReadOnly](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#getReadOnly\(\)) property. It gets the count of unread messages, then fetches one message and then gets the count of unread messages again in read-only mode. The count of the unread messages remains the same indicating that the permanent state of the mailbox was not changed.


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
