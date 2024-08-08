---
title: Email Tutorial
type: docs
weight: 5
url: /net/email-tutorial/
---

## **Most Popular Email File Formats**

### MSG 

**Microsoft Outlook Message (MSG)** is a proprietary email format used by Microsoft Outlook to store individual email messages. These files contain the email content and metadata such as sender, recipients, subject, and timestamps. They support rich formatting, attachments, and Outlook-specific features like flags, importance, and sensitivity.

#### Key features

- MSG file represents a single email message.
- MSG files associate with Microsoft Outlook and can be opened by it.
- MSG files are commonly used for archiving, backup, and exchanging Outlook items between different instances of Outlook or other compliant email clients.

MSG is closely related within the context of Microsoft Outlook and **Messaging Application Programming Interface (MAPI)**. MAPI is a programming interface that allows applications to interact with messaging services, primarily Microsoft Exchange Server and Microsoft Outlook. It provides a set of functions and protocols for sending, receiving, and managing email messages, as well as accessing other messaging-related features such as calendars, contacts, and tasks. MAPI is used by Microsoft Outlook to create, manipulate, and manage email messages. When a user composes or receives an email in Outlook, MAPI handles the underlying communication with the mail server and provides the necessary functions for managing the message content.

#### Technical Basis for MSG Format

MSG files store message data using **MAPI properties**, which are attributes that define various aspects of the message. These properties include standard attributes such as sender, recipient, subject, and timestamps, as well as custom properties and extended attributes.
Properties organize the message into a hierarchical structure, with top-level properties defining the overall message attributes and nested properties representing specific components such as recipients, attachments, and embedded objects. MSG files may contain multiple property streams, each containing a set of related MAPI properties. These streams are structured according to the **Compound File Binary Format (CFBF)** and store both standard and custom properties.

### OFT

**Outlook File Template (OFT)** are email format used by Microsoft Outlook for creating standardized messages. Unlike MSG files, OFT files do not contain actual message content but serve as templates with predefined formatting, layout, and placeholders for dynamic content. 

#### Key features

 - OFT files streamline the creation of repetitive emails by providing pre-designed templates for common scenarios such as newsletters, announcements, or responses.
 - By using OFT templates, organizations ensure consistency in branding, formatting, and messaging across all outgoing communications.
 - Users can customize OFT templates by adding or modifying content before sending, allowing for personalized messages while maintaining standardized formatting.

### EML

**EML** is one of the most widely recognized and utilized email file formats, primarily designed to adhere to the **MIME (Multipurpose Internet Mail Extensions)** standard. This format is widely supported across various email clients and systems owing to its open and generalized approach to email storage and transmission.

#### Key Features

- Each EML file encapsulates a single email message along with its associated metadata such as sender, recipients, subject, and timestamps.
- EML files support rich formatting, attachments, and embedded elements, adhering to the MIME standard which allows for a versatile representation of email content.
-  Unlike proprietary formats such as MSG (Microsoft Outlook Message), which are closely tied to specific software (Outlook and MAPI), EML files offer a more universal approach compatible with various email programs across different platforms. EML files are compatible with a multitude of email clients, including but not limited to Microsoft Outlook, Mozilla Thunderbird, Apple Mail, and many web-based email services. 

#### Technical Basis for EML Format

The EML file format is inherently linked to the MIME standard, which is a specification for the format of Internet message bodies. MIME extends the basic email format to support text in character sets other than ASCII, as well as attachments of multimedia content.

**MIME Structure:**

   - An EML file begins with the header section, containing information such as the From, To, Subject, Date, and other headers. Additional headers might include Content-Type, Content-Transfer-Encoding, and more.
   - Following the headers, the body of an EML file is presented. This section can contain plain text, HTML, or multipart content allowing for the combination of different types of content within a single message.
   - An EML file may include attachments encoded in base64, allowing binary data to be transferred via email. These attachments are defined within their own MIME parts with appropriate headers indicating the file type and encoding.

**MIME Types:**

The content of an EML file is broken down into various MIME types to differentiate text, HTML, and other media types. Common MIME types found within an EML file include:

- `text/plain` for plain text messages.
- `text/html` for HTML formatted messages.
- `multipart/mixed` for emails that include both message content and attachments.
- `application/octet-stream` for binary file attachments.

### TNEF

**Transport Neutral Encapsulation Format (TNEF)** is a proprietary email format used by Microsoft Outlook and Microsoft Exchange Server to encapsulate email properties and rich text content that may not be supported by standard email protocols. 
It is used primarily by Microsoft email clients to encode and transmit rich text formatting, embedded objects, and other proprietary email features, ensuring that complex email content such as formatting, embedded files, and calendar events are preserved when emails are sent between different Microsoft email clients.

#### Key Features

- TNEF can encapsulate a wide array of MAPI properties, a Microsoft-specific rich text formatting and special properties that can't be conveyed through standard MIME or plain text emails.
- Outlook items, such as Calendar, Contacts, Tasks, Notes can be encapsulated within the TNEF format.
- Non-Microsoft email clients might not understand or properly process TNEF attachments, often resulting in the annoying `winmail.dat` file. This usually happens because they can't decode the proprietary formatting encoded in TNEF.

#### Technical Basis for TNEF Format

- TNEF encapsulates email content into a special binary attachment. This attachment typically carries a `.dat` file extension, most commonly named `winmail.dat`.
- TNEF data is often associated with the MIME type `application/ms-tnef`.
- TNEF format represents a hierarchy of message properties as a flat structure, which can be viewed as a sequential data stream. The typical format of a specific property in the stream includes an identifier with data type information, size (if not defined by the type), and data.

## **Common Email Storage Formats**

### MBOX

**MBOX (short for Mailbox)** is a widely used email storage format that has been prevalent for several decades. It is used to store a collection of email messages in a single file, with each message concatenated and demarcated by a separator line. 

MBOX was first developed in the 1970s and has since seen various versions and implementations over the years. It has been implemented in numerous email clients such as Unix mail, Mozilla Thunderbird, Eudora, and more.

#### Key Features

- MBOX is supported across a wide range of platforms, including Unix, Linux, and macOS.
- Clients like Mozilla Thunderbird, Apple Mail, and many others can read and write MBOX files.
- The format's plain text nature makes it simple to parse and process using text-manipulation tools.
- Due to its simple structure, MBOX is popularly used for archiving and backup purposes.
- Since all emails are stored in a single file, the file can become quite large over time, leading to inefficiencies.
#### Variants of MBOX

MBOX comes in several variants, each with slight differences in how they handle messages:

- **MBOXO:** The original format where "From " lines in the email body are quoted with a > character.
- **MBOXRD:** A variant of MBOXO that further extends the quoting method of "From " lines.
- **MBOXCL:** Introduced by the "Classic" MBOX variant where each "From " line is quoted with an ffrom string.
- **MBOXCL2:** A variation of MBOXCL where "From " lines are doubled to distinguish them.

#### Technical Basis for MBOX Format

**File Structure:**
  - An MBOX file is a plain text file that contains a series of EML messages.
  - Each message starts with a "From " line (a space after the word "From") that typically includes the sender's email address and the timestamp when the message was received.
  - Each message is followed by a blank line to separate it from the next message.
  
    **Example:**
    
    From user@example.com Fri Jan 01 00:00:00 2021
    (Headers)
    
    (Body)
    
    From user2@example.com Fri Jan 01 00:01:00 2021
    (Headers)
    
    (Body)
    

### PST/OST

 **Personal Storage Table (PST)** and **Offline Storage Table (OST)** are file formats used by Microsoft Outlook to store copies of emails, calendar events, and other items.
 
#### Key Features

- PST files are used to store personal information and are typically used for archiving older emails and data. Primarily used by home users and small organizations for local storage of email messages, contacts, and calendar events.
- OST files are used for offline storage and synchronization of emails and other data with the Exchange server. Primarily used by users who access Microsoft Exchange Server or Office 365.
- Stored locally on a user's computer. Can be accessed even when the user is not connected to the email server.
- PST files can be easily backed up and transferred to other computers. Users can transfer PST files across different systems or Outlook versions.
- OST files are not intended for manual backup or transfer since they are synchronized copies of server data. OST files are tied to specific profiles and cannot be moved to different systems easily.

### OLM

 **Outlook for Mac Archive File (OLM)** is a file format used by Microsoft Outlook for Mac to store email messages, calendar events, contacts, tasks, and other items.
 
#### Key Features

- OLM files are primarily used for archiving and backing up emails and other Outlook items on Mac systems.
- OLM files are stored locally on the user's Mac.
- OLM files can be opened and accessed via Microsoft Outlook for Mac. They are not directly compatible with Outlook for Windows without conversion.
- There is no fixed size limit for OLM files imposed by Microsoft, but performance issues can occur if the file becomes very large. Users typically manage the size by creating multiple smaller archives rather than one large OLM file.
- Backup: Since OLM files are stored locally, they can be backed up or copied to external storage devices.

### TGZ

**TGZ**  (used by Zimbra for mailbox backup file) is a file format used for archiving and compressing data, commonly associated with Unix and Linux systems. The term "TGZ" refers to a combination of two utilities: "tar" (Tape Archive) and "gzip." The .tar file format bundles multiple files and directories into a single archive file. It preserves file system information such as directory structures, file permissions, and timestamps. The .gz file format compresses data, making the tar archive smaller and easier to manage or transfer. The compressed nature of TGZ makes it suitable for transferring email archives over the internet or moving them between systems.

### NSF

 **Notes Storage Facility (NSF)** is a proprietary file format used primarily by IBM Lotus Notes (now HCL Notes) to store various types of data, including email, calendar events, tasks, and other application data. NSF files use a NoSQL, document-based database model. Each database is stored as a single NSF file with .nsf extension. The extension represents a database format used by IBM Notes and Domino Server. Each email, calendar entry, or task is stored as a document which can contain various types of data such as text, attachments, links, rich text formatting, and even metadata.
 
## **Mail Protocols**

### SMTP

**SMTP (Simple Mail Transfer Protocol)** is a protocol used for sending and receiving email messages over the Internet. It is a crucial part of the email communication process and is primarily responsible for transferring emails from the sender's mail server to the recipient's mail server as well as submitting emails from a client to a server. The default port for SMTP is 25 for communication between mail servers. Port 587 and Port 465 are also used for SMTP, with 587 commonly used for mail submission and 465 for SMTP over SSL (SMTPS). SMTP is defined by [RFC 5321 version](https://datatracker.ietf.org/doc/html/rfc5321).

#### Key Features

- Supports authentication mechanisms (e.g., SMTP AUTH) to ensure that only authorized users can send emails through the server.
- SMTP can use SSL/TLS to encrypt the connection between the client and server, ensuring that email data is transmitted securely.
- Provides detailed error messages and status codes to indicate the success or failure of email transmission.
- SMTP can handle multipart messages, allowing for the inclusion of attachments and various content types within an email.
- SMTP is a widely accepted and standardized protocol, ensuring compatibility across different email systems and clients,(e.g., Microsoft Outlook, Mozilla Thunderbird use SMTP to send outgoing emails). Automated systems and applications use SMTP to send notifications, alerts, and other automated emails.

### IMAP

**Internet Message Access Protocol (IMAP)** is a standard protocol used by email clients to access, retrieve, and manage email messages from a mail server. Among the supported clients are Microsoft Outlook, Mozilla Thunderbird, Apple Mail, and many webmail services like Gmail, Yahoo Mail, and Outlook.com. The most commonly used version is IMAP4, defined by [RFC 3501](https://datatracker.ietf.org/doc/html/rfc3501). Unlike **POP (Post Office Protocol)**, which downloads emails to a local device, IMAP stores emails on the server. The ability to view and manage email messages directly on the mail server provides flexibility to access them from multiple devices and locations, reducing the risk of data loss if a device is lost or damaged. IMAP synchronizes the email client with the server, ensuring that changes made on one client (such as reading or deleting an email) are reflected on all other clients. IMAP typically uses port 143 for non-encrypted communications and port 993 for encrypted (SSL/TLS) communications.

#### Key Features

- Folder Management. IMAP allows users to create, delete, and rename folders on the mail server. It supports hierarchical folder structures for organizing emails.
- IMAP tracks the status of each email (e.g., read, unread, flagged, answered). These status flags are stored on the server, so they are consistent across all devices.
- IMAP can fetch specific parts of an email, such as headers or body parts, which can be useful for previewing emails or handling large attachments.
- IMAP supports server-side searching and filtering of emails based on various criteria, allowing clients to retrieve specific messages without downloading all emails.
- Multiple clients can access the same mailbox simultaneously. IMAP handles concurrent access and updates the state of emails in real-time.
- Server Dependency. Since emails are stored on the server, a reliable internet connection is necessary to access and manage emails. Server downtime can impact email availability.
- IMAP can use SSL/TLS to encrypt the connection between the client and server, ensuring that email data is transmitted securely.
- IMAP supports various authentication methods, including OAuth, to verify user identities securely.

#### Protocol Extensions

- **IMAP IDLE:** An extension that allows the server to notify the client of new messages or changes in real-time, reducing the need for frequent polling.
- **IMAP QUOTA:** An extension that provides mechanisms for managing and reporting storage quotas, helping users manage their mailbox sizes.
- **IMAP MOVE:** An extension that optimizes the process of moving messages between folders on the server, improving performance.

### POP3

 **Post Office Protocol version 3 (POP3)** is a protocol used by email clients such as Microsoft Outlook, Mozilla Thunderbird, and Apple Mailto retrieve email from a mail server. It is one of the oldest and simplest protocols for email retrieval, designed to download emails to a local device and optionally delete them from the server.

#### Key Features

- Since emails are downloaded to the local device, users can access their emails offline without needing a constant internet connection.
- POP3 is simple to set up and use, making it accessible for users who need basic email retrieval without advanced features.
- POP3 does not synchronize email across multiple devices. Once an email is downloaded to one device, it is no longer available on the server by default.
- POP3 provides limited server-side management capabilities. Advanced features like folder management, server-side search, and message status flags are not supported.
- Since emails are stored locally, users need to ensure they back up their email data to prevent loss in case of device failure.
- Users can configure POP3 settings to delete emails from the server immediately after download, after a specified period, or when deleted from the local client.
- POP3 can use SSL/TLS to encrypt the connection between the client and server, ensuring that email data is transmitted securely.

#### Protocol Versions and Extensions

- **POP3 over SSL (POP3S)** is a version of POP3 that operates over an SSL/TLS connection, providing encrypted communication between the client and server.
- **APOP (Authenticated Post Office Protocol)** is an extension that provides a more secure authentication method by using hashed passwords.

## **API to Access Mail Services**

### Exchange Web Dav (has been officially deprecated)

**Exchange WebDAV (Web Distributed Authoring and Versioning)** was a protocol extension used by Microsoft Exchange Server to allow clients to access and manipulate mail, calendar, and contact items stored on the server via HTTP. Although it has been officially deprecated, it played a significant role in the development of web-based and remote access to Exchange data.

### EWS

**Exchange Web Services (EWS)** is an API provided by Microsoft to interact with Microsoft Exchange Server. It allows developers to access and manipulate Exchange data such as emails, calendar events, contacts, and tasks programmatically. EWS was introduced to replace older protocols like WebDAV and provides a more robust and efficient way to work with Exchange data. 

It uses the SOAP (Simple Object Access Protocol) over HTTP and HTTPS to send and receive messages between the client and the Exchange server. The SOAP-based nature of EWS can be complex to implement and debug compared to RESTful APIs. Microsoft is gradually shifting towards Microsoft Graph API, which provides a more modern and RESTful approach to accessing Microsoft 365 data, including Exchange Online.

### Microsoft Graph

**Microsoft Graph** is a powerful API that provides a unified endpoint for accessing a wide range of data and services in the Microsoft 365 ecosystem. It allows developers to interact with a variety of Microsoft services, including Office 365, Azure Active Directory, SharePoint, OneDrive, Outlook, Microsoft Teams, and more. It serves as a gateway to data and insights across Microsoft 365.

#### Key Features

- The base URL for the API is https://graph.microsoft.com.
- Uses OAuth 2.0 for authentication and authorization.
- Leverages Microsoft's AI and machine learning capabilities for enhanced data insights.

### Gmail API

**Gmail API** is a RESTful API provided by Google that allows developers to interact programmatically with Gmail mailboxes and perform various operations on email data (read, send, delete, and organize email messages). It offers a more flexible and powerful alternative to the traditional IMAP and SMTP protocols, enabling developers to access and manage Gmail messages, threads, labels, drafts, and more. It is available through the Google Cloud Platform.

#### Key Features

- Perform multiple API requests in a single HTTP call to improve efficiency and reduce the number of network requests.
- Uses OAuth 2.0 for secure authentication and authorization, ensuring that applications only access data that users have explicitly granted permission for.
- Provides various permission scopes, allowing applications to request only the level of access they need (e.g., read-only access, full access).
- All API interactions occur over HTTPS to ensure secure communication between the application and Google’s servers.

## **Advanced Technologies**

### S/MIME

**Secure/Multipurpose Internet Mail Extensions (S/MIME)** is a widely used standard for securing email communication. It provides a method for sending and receiving signed and encrypted email messages, ensuring message integrity, authenticity, and confidentiality.

#### Key Features

- S/MIME ensures that only the intended recipient can read the email content. It uses a combination of symmetric (for speed) and asymmetric (for key exchange) encryption algorithms. Commonly used algorithms include RSA (used for asymmetric encryption), AES or Advanced Encryption Standard (one of the symmetric algorithms), and Triple DES.
- Confirms the identity of the sender. 
- Verifies that the email content has not been tampered with during transit. Prevents the sender from denying the authorship of the email. 
- Uses the sender’s private key to create a signature and the recipient's client uses the sender's public key to verify it.
- S/MIME relies on a Public Key Infrastructure (PKI) for key management and exchange. Digital certificates, issued by Certificate Authorities (CAs), bind public keys to individual identities. Certificates usually follow the X.509 standard.

### DKIM

**DomainKeys Identified Mail (DKIM)** is an email authentication mechanism designed to detect forged sender addresses, a common technique used in phishing and email spoofing. It allows an organization to take responsibility for an email during its transit by associating a domain name with the message, thereby ensuring its authenticity and integrity. DKIM verifies that an email purportedly coming from a specific domain was indeed authorized by the domain owner, primarily focusing on the authenticity of the "From" email address. This is achieved by enabling the sender to electronically sign their email with a private key, while the recipient verifies this signature using a public key published in the sender's DNS records.

#### Key Features

- DKIM adds a "DKIM-Signature" header to the email which contains the digital signature and several key parameters. The email body and select headers are hashed using a hashing algorithm like SHA-256. This hash is then encrypted using the sender’s private key to generate the digital signature.
- The sender publishes the public key in their DNS records. The recipient’s email server looks up the sender’s public key in DNS to verify the digital signature.

### AMP Email

**Accelerated Mobile Pages (AMP)** for Email is an open-source framework designed to create dynamic, interactive, and engaging email experiences. It's designed to make emails more dynamic and functional, transforming a medium that has traditionally been static and passive.

#### Key features

- Allows users to take actions directly within the email, such as RSVPing to events, filling out forms, or interacting with product carousels.
- Emails can serve dynamic content that updates at the time of opening. This ensures that users see the most current information whether it be the latest pricing, stock status, or news updates.
- AMP emails is supported by several major email clients including Gmail, Yahoo Mail, Outlook.com. Each email client that supports AMP emails maintains its own set of requirements and rendering rules.
- AMP emails need to be sent in a multi-part MIME format containing a plain text version for basic accessibility, an HTML version for rich and visually appealing content, and an AMP version for dynamic and interactive elements, ensuring compatibility and an enhanced user experience across various email clients.
- Only verified senders can send AMP emails, ensuring that emails are secure and trusted.

### AntiSpam

AntiSpam refers to a range of techniques, technologies, and strategies designed to detect, prevent, and mitigate unsolicited and often harmful email messages, commonly known as spam. 

#### AntiSpam Techniques

1. **Filtering Methods**
   - Content-Based Filtering: Analyzes the content of the email for common spam indicators.
   - Blacklists: Lists of known spam IP addresses or domains that are automatically blocked.
   - Whitelists: Lists of approved senders that are always allowed through.
   - Heuristic Filtering: Uses rules and algorithms to detect spam based on patterns.
   - Bayesian Filtering: Uses statistical methods to identify spam based on historical data.
   - Greylisting: Temporarily rejects emails from unknown senders and accepts them if they are sent again after a delay.
   - Machine Learning: Uses complex models trained on large datasets to identify spam.

2. **Authentication Methods**
   - SPF (Sender Policy Framework): Verifies that the sender's IP address is authorized to send emails for the domain.
   - DKIM (DomainKeys Identified Mail): Uses digital signatures to verify that the email has not been altered during transit and is indeed from the domain it claims to be.
   - DMARC (Domain-based Message Authentication, Reporting & Conformance): Builds upon SPF and DKIM to provide a standardized method for email senders to indicate that their messages are protected and how receiving servers should handle authentication failures.

### Email bounces

#### Types of Email Bounces

1. **Hard Bounces.** Permanent delivery failures indicating that the email cannot be delivered to the intended recipient's address.
   - Common Causes:
     - Invalid or non-existent email addresses.
     - The recipient’s domain does not exist.
     - Permanent server issues on the recipient's end.
     - Typos or formatting errors in the email address.

2. **Soft Bounces.** Temporary delivery failures indicating that the email could not be delivered at the time but may be successful if retried later.
   - Common Causes:
     - The recipient's mailbox is full.
     - Temporary server issues on the recipient's end.
     - The recipient’s email server is down or offline.
     - Emails too large for the recipient’s email system.

Email servers typically return bounce codes that can help diagnose the reason for a bounce.

### Email threading

Email threading is a method used by email clients and applications to group related emails together based on their subject or conversation, making it easier for users to follow and manage email exchanges.

#### Key features

- **In-Reply-To and References Headers**. Email headers that point to previous messages in the thread, helping the email client to link replies and forwards to the original email.
- Subject Lines. Often used to group emails into threads. Emails with the same subject line, typically prefixed with "Re:" (reply) or "Fwd:" (forward), are grouped together.
- Users can expand or collapse threads, focusing only on the relevant portions of a conversation.