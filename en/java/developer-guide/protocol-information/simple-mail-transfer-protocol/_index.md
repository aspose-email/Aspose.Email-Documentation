---
title: Simple Mail Transfer Protocol
type: docs
weight: 10
url: /java/simple-mail-transfer-protocol/
---

{{% alert color="primary" %}} 

Simple Mail Transfer Protocol (SMTP) is used to transfer email messages across the internet. The default port for SMTP is 25. We specify one or more recipients, subject, body and other encoded objects in the email message. The message is then transferred to a remote SMTP server. The client connects to the remote SMTP server using the IP address or domain name on port 25. Authentication is performed with a username and password. SMTP server can also accept anonymous connections which do not require authentication. The server then delivers the message to the recipients on behalf of the client.

- [RFC2821](http://www.rfc-archive.org/getrfc.php?rfc=2821)
- [RFC821](http://www.rfc-archive.org/getrfc.php?rfc=821)

{{% /alert %}}
