---
title: Mail Protocols
ArticleTitle: Mail Protocols
type: docs
weight: 7
url: /net/mail-protocols/
---

## **SMTP**

**SMTP (Simple Mail Transfer Protocol)** is a protocol used for sending and receiving email messages over the Internet. It is a crucial part of the email communication process and is primarily responsible for transferring emails from the sender's mail server to the recipient's mail server as well as submitting emails from a client to a server. The default port for SMTP is 25 for communication between mail servers. Port 587 and Port 465 are also used for SMTP, with 587 commonly used for mail submission and 465 for SMTP over SSL (SMTPS). SMTP is defined by [RFC 5321 version](https://datatracker.ietf.org/doc/html/rfc5321).

### Key Features

- Supports authentication mechanisms (e.g., SMTP AUTH) to ensure that only authorized users can send emails through the server.
- SMTP can use SSL/TLS to encrypt the connection between the client and server, ensuring that email data is transmitted securely.
- Provides detailed error messages and status codes to indicate the success or failure of email transmission.
- SMTP can handle multipart messages, allowing for the inclusion of attachments and various content types within an email.
- SMTP is a widely accepted and standardized protocol, ensuring compatibility across different email systems and clients,(e.g., Microsoft Outlook, Mozilla Thunderbird use SMTP to send outgoing emails). Automated systems and applications use SMTP to send notifications, alerts, and other automated emails.

## **IMAP**

**Internet Message Access Protocol (IMAP)** is a standard protocol used by email clients to access, retrieve, and manage email messages from a mail server. Among the supported clients are Microsoft Outlook, Mozilla Thunderbird, Apple Mail, and many webmail services like Gmail, Yahoo Mail, and Outlook.com. The most commonly used version is IMAP4, defined by [RFC 3501](https://datatracker.ietf.org/doc/html/rfc3501). Unlike **POP (Post Office Protocol)**, which downloads emails to a local device, IMAP stores emails on the server. The ability to view and manage email messages directly on the mail server provides flexibility to access them from multiple devices and locations, reducing the risk of data loss if a device is lost or damaged. IMAP synchronizes the email client with the server, ensuring that changes made on one client (such as reading or deleting an email) are reflected on all other clients. IMAP typically uses port 143 for non-encrypted communications and port 993 for encrypted (SSL/TLS) communications.

### Key Features

- Folder Management. IMAP allows users to create, delete, and rename folders on the mail server. It supports hierarchical folder structures for organizing emails.
- IMAP tracks the status of each email (e.g., read, unread, flagged, answered). These status flags are stored on the server, so they are consistent across all devices.
- IMAP can fetch specific parts of an email, such as headers or body parts, which can be useful for previewing emails or handling large attachments.
- IMAP supports server-side searching and filtering of emails based on various criteria, allowing clients to retrieve specific messages without downloading all emails.
- Multiple clients can access the same mailbox simultaneously. IMAP handles concurrent access and updates the state of emails in real-time.
- Server Dependency. Since emails are stored on the server, a reliable internet connection is necessary to access and manage emails. Server downtime can impact email availability.
- IMAP can use SSL/TLS to encrypt the connection between the client and server, ensuring that email data is transmitted securely.
- IMAP supports various authentication methods, including OAuth, to verify user identities securely.

### Protocol Extensions

- **IMAP IDLE:** An extension that allows the server to notify the client of new messages or changes in real-time, reducing the need for frequent polling.
- **IMAP QUOTA:** An extension that provides mechanisms for managing and reporting storage quotas, helping users manage their mailbox sizes.
- **IMAP MOVE:** An extension that optimizes the process of moving messages between folders on the server, improving performance.

## **POP3**

 **Post Office Protocol version 3 (POP3)** is a protocol used by email clients such as Microsoft Outlook, Mozilla Thunderbird, and Apple Mailto retrieve email from a mail server. It is one of the oldest and simplest protocols for email retrieval, designed to download emails to a local device and optionally delete them from the server.

### Key Features

- Since emails are downloaded to the local device, users can access their emails offline without needing a constant internet connection.
- POP3 is simple to set up and use, making it accessible for users who need basic email retrieval without advanced features.
- POP3 does not synchronize email across multiple devices. Once an email is downloaded to one device, it is no longer available on the server by default.
- POP3 provides limited server-side management capabilities. Advanced features like folder management, server-side search, and message status flags are not supported.
- Since emails are stored locally, users need to ensure they back up their email data to prevent loss in case of device failure.
- Users can configure POP3 settings to delete emails from the server immediately after download, after a specified period, or when deleted from the local client.
- POP3 can use SSL/TLS to encrypt the connection between the client and server, ensuring that email data is transmitted securely.

### Protocol Versions and Extensions

- **POP3 over SSL (POP3S)** is a version of POP3 that operates over an SSL/TLS connection, providing encrypted communication between the client and server.
- **APOP (Authenticated Post Office Protocol)** is an extension that provides a more secure authentication method by using hashed passwords.
