---
title: Features Overview
ArticleTitle: Features Overview
type: docs
weight: 25
url: /net/features-overview/
---

In Aspose.Email for .NET, a diverse set of classes and methods are categorized into namespaces, each serving distinct purposes related to email processing. From handling email protocols like SMTP, POP3, and IMAP to managing tasks such as calendar integrations and task scheduling, each namespace is created to address specific use cases. This structured approach not only simplifies coding but also ensures that developers can implement email solutions with ease.

Below we will delve into the various namespaces provided by Aspose.Email for .NET, exploring their primary functions and reffering to the most important classes.

## **Aspose.Email**
**Contains common classes for handling various aspects of email messages**

The central component of this namespace is the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, a versatile and powerful entity that facilitates the creation, manipulation, and processing of email messages. The MailMessage class supports a wide array of features, including composing emails with rich text formatting, embedding images, attaching files, and specifying multiple recipients with different roles (to, cc, bcc). It also provides robust functionalities for parsing and reading incoming email messages, enabling developers to extract details such as subject, sender, recipients, and body content seamlessly. Furthermore, MailMessage integrates smoothly with various email protocols like SMTP, IMAP, and POP3, ensuring that sending and receiving emails is both straightforward and reliable.

## **Aspose.Email.Amp**
**Provides classes for handling messages with AMP HTML body**

[Aspose.Email.Amp](https://reference.aspose.com/email/net/aspose.email.amp/) offers a robust set of classes dedicated to handling messages that include AMP HTML bodies, making it an tool for developers looking to incorporate dynamic and interactive email content. At the heart of this capability is the [AmpMessage](https://reference.aspose.com/email/net/aspose.email.amp/ampmessage/#ampmessage-class) class, which serves as the primary component for constructing, manipulating, and rendering AMP-infused email messages. This class allows developers to seamlessly integrate rich media and interactive elements directly into the body of an email, leveraging the speed and engaging features of AMP HTML.

With AmpMessage, you can add elements like image carousels, real-time data fetching, and interactive forms, all designed to work efficiently within an email client.  

## **Aspose.Email.AntiSpam**
**Offers classes for implementing self-learning filters to detect spam emails**

[Aspose.Email.AntiSpam](https://reference.aspose.com/email/net/aspose.email.antispam/) offers a solution for email filtering with its core class [SpamAnalyzer](https://reference.aspose.com/email/net/aspose.email.antispam/spamanalyzer/) designed for detecting spam emails using a self-learning Bayesian filter. This class allows applications to analyze and classify incoming emails as spam or not, based on Bayesian statistics. The SpamAnalyzer can learn from user input, allowing it to improve its accuracy over time by adjusting its internal model based on previously classified emails.

## **Aspose.Email.Bounce**
**Provides classes for handling bounce messages**

[Aspose.Email.Bounce](https://reference.aspose.com/email/net/aspose.email.bounce/) offers a comprehensive solution for email applications to efficiently manage bounce messages. The [BounceResult] (https://reference.aspose.com/email/net/aspose.email.bounce/bounceresult/#bounceresult-class)  class, represents the result of the message examination as a bounce message.

## **Aspose.Email.Calendar**
**Contains classes for working with calendars**

[Aspose.Email.Calendar](https://reference.aspose.com/email/net/aspose.email.calendar/) is an namespace designed to empower developers with tools for managing and manipulating calendar data. The [Appointment](https://reference.aspose.com/email/net/aspose.email.calendar/appointment/) class encapsulates functionality for handling calendar events and appointments. With the Appointment class, developers can effortlessly create, modify, and manage calendar events, including setting start and end times, recurring patterns, reminders, and inviting attendees. The class supports iCalendar (ICS) format ensuring compatibility and integration with different calendar systems. Additionally, the Appointment class enables exporting calendar files to MSG format, facilitating smooth data exchange and synchronization across diverse platforms.

## **Aspose.Email.Clients.DeliveryService.Mailgun**
**Implements the client for Mailgun email delivery service**

The [Aspose.Email.Clients.DeliveryService.Mailgun](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.mailgun/) namespace provides a client implementation tailored for the Mailgun email delivery service, facilitating seamless integration for developers seeking reliable and efficient email dispatch capabilities. At the heart of this namespace is the pivotal class, [MailgunClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.mailgun/mailgunclient/#mailgunclient-class), which serves as the primary component for interfacing with Mailgun's API.

## **Aspose.Email.Clients.DeliveryService.SendGrid**
**Implements the client for SendGrid email delivery service**

Within the [Aspose.Email.Clients.DeliveryService.SendGrid](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/) namespace lies an implementation tailored specifically for the SendGrid email delivery service, offering developers seamless integration for efficient email dispatching. At the core of this namespace stands the pivotal class, [SendGridClient](https://reference.aspose.com/email/net/aspose.email.clients.deliveryservice.sendgrid/sendgridclient/#sendgridclient-class), serving as the primary component for interfacing with SendGrid's API.

## **Aspose.Email.Clients.Exchange.Dav**
**Provides classes for accessing Exchange Server using WebDav Exchange Store Protocol**

[Aspose.Email.Clients.Exchange.Dav](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/) namespace has tools for interaction with Exchange Server through the WebDav Exchange Store Protocol. The [ExchangeClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.dav/exchangeclient/) class serve for accessing Exchange Server resources.

## **Aspose.Email.Clients.Exchange.WebService**
**Provides access to MS Exchange Server using Exchange Web Services (EWS)**

[Aspose.Email.Clients.Exchange.WebService](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/) is designed to provide access to Microsoft Exchange Server using Exchange Web Services (EWS). Its primary class, [EWSClient](https://reference.aspose.com/email/net/aspose.email.clients.exchange.webservice/ewsclient/), facilitates interactions with the Exchange Server. EWSClient enables developers to connect to the server efficiently and perform various operations, including managing emails, calendars, contacts, tasks, and public folders. This class supports functionalities such as sending and receiving emails, organizing mailbox folders, scheduling appointments, and handling meeting requests.

## **Aspose.Email.Clients.Google**
**Provides classes for accessing Google accounts**

[Aspose.Email.Clients.Google](https://reference.aspose.com/email/net/aspose.email.clients.google/) is a namespace that provides classes for accessing and managing Google accounts with ease. The central component class within this namespace is the [GmailClient](https://reference.aspose.com/email/net/aspose.email.clients.google/gmailclient/). This class allows developers to integrate and interact with Google Mail services, leveraging OAuth 2.0 authentication.

## **Aspose.Email.Clients.Graph**
**Provides classes for accessing Microsoft 365 services using REST API**

The [Aspose.Email.Clients.Graph](https://reference.aspose.com/email/net/aspose.email.clients.graph/) is designed for accessing and managing Microsoft 365 services through REST API, offering an approach for integrating email functionalities within .NET applications. At the heart of this namespace lies the [GraphClient](https://reference.aspose.com/email/net/aspose.email.clients.graph/graphclient/) class, that empowers developers to seamlessly interact with a Microsoft 365 services. The GraphClient enables a wide array of operations, including sending and receiving emails, managing calendar events, and handling contacts. With support for OAuth 2.0 authentication, it ensures secure access to user data, maintaining compliance with modern security standards. Additionally, the GraphClient facilitates the manipulation of folders, synchronization of mailboxes, and retrieval of email metadata.

## **Aspose.Email.Clients.Imap**
**Provides classes for accessing and manipulating messages using IMAP**

The [Aspose.Email.Clients.Imap](https://reference.aspose.com/email/net/aspose.email.clients.imap/) namespace is designed to interact with email servers using the Internet Message Access Protocol (IMAP). Central to this namespace is the [ImapClient](https://reference.aspose.com/email/net/aspose.email.clients.imap/imapclient/) class, which serves as the primary interface for performing a wide range of email operations. Once connected, developers can use the ImapClient to list, fetch, delete, and search emails within various mail folders. Additionally, it offers capabilities to manage and manipulate these folders, including creating, renaming, and deleting them.

## **Aspose.Email.Clients.Pop3**
**Provides classes for accessing and manipulating messages using POP3**

The [Aspose.Email.Clients.Pop3](https://reference.aspose.com/email/net/aspose.email.clients.pop3/) namespace is engineered to streamline the interaction with email servers utilizing the Post Office Protocol version 3 (POP3), offering a set of classes for accessing and manipulating email messages. At the heart of this namespace lies the [Pop3Client](https://reference.aspose.com/email/net/aspose.email.clients.pop3/pop3client/) class. The Pop3Client class facilitates establishing secure connections to POP3 servers, supporting a variety of authentication mechanisms to ensure safe and reliable access. Once connected, the Pop3Client allows developers to perform essential email operations, such as retrieving messages from the server, listing emails, marking specific messages for deletion, and fetching full message details, including headers and attachments. Additionally, it provides built-in support for SSL and TLS protocols.

## **Aspose.Email.Clients.Smtp**
**Provides classes for sending messages using SMTP**

The [Aspose.Email.Clients.Smtp](https://reference.aspose.com/email/net/aspose.email.clients.smtp/) namespace is designed for developers looking to integrate SMTP (Simple Mail Transfer Protocol) functionality into their .NET applications for sending email messages. At the core of this namespace lies the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class. The SmtpClient class offers a set of capabilities, empowering developers to establish secure connections to SMTP servers and send emails. It supports various authentication methods, ensuring compatibility with a wide range of SMTP servers, and provides options for specifying message priority, delivery notifications, and custom headers. With built-in support for SSL and TLS encryption protocols, the SmtpClient class ensures secure communication.

## **Aspose.Email.DKIM**
**Contains classes for working with DKIM signatures**

The [Aspose.Email.DKIM](https://reference.aspose.com/email/net/aspose.email.dkim/) namespace offers classes for handling DomainKeys Identified Mail (DKIM) signatures, to ensure email integrity and authenticity. The [DKIMSignatureInfo](https://reference.aspose.com/email/net/aspose.email.dkim/dkimsignatureinfo/) class serves as the principal component for providing DKIM-related info.

## **Aspose.Email.Mapi**
**Contains classes that represent Outlook messages, contacts, appointments, and work with Microsoft Outlook PST/OST file format**

The [Aspose.Email.Mapi](https://reference.aspose.com/email/net/aspose.email.mapi/) namespace is designed for work with Microsoft Outlook data. The main component class within this namespace is [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/), which serves for handling Outlook messages. MapiMessage provides capabilities for creating, reading, modifying, and saving Outlook messages in MSG format. Developers can use this class to access and manipulate the content of Outlook items, including the subject, body, attachments, recipients, and properties. 

Beyond managing individual emails, the Aspose.Email.Mapi namespace also includes:

- classes for handling contacts ([MapiContact](https://reference.aspose.com/email/net/aspose.email.mapi/mapicontact/)),
- appointments ([MapiCalendar](https://reference.aspose.com/email/net/aspose.email.mapi/mapicalendar/)),
- and other Outlook items, making it possible to programmatically interact with various elements typically housed within PST (Personal Storage Table) and OST (Offline Storage Table) files. This suite of classes allows for integration with Outlook data storage formats, facilitating tasks such as email migration, backup, and synchronization.

## **Aspose.Email.PersonalInfo.VCard**
**Contains classes to work with VCard file format**

The [Aspose.Email.PersonalInfo.VCard](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/) namespace is essential for developers looking to manipulate VCard file formats within their applications. The primary class within this namespace is the [VCardContact](https://reference.aspose.com/email/net/aspose.email.personalinfo.vcard/vcardcontact/). This class is pivotal for creating, parsing, and managing VCard files, which are widely used for exchanging contact information. With VCardContact, developers can read VCard files to extract contact details or generate VCard files from existing data. This class supports various VCard versions for compatibility and flexibility in handling different VCard formats. Additionally, it includes capabilities for encoding and decoding contact information, allowing integration with other systems and platforms that utilize VCard standards.

## **Aspose.Email.Printing**
**Contains classes that represent the message printing functionality**

The [Aspose.Email.Printing](https://reference.aspose.com/email/net/aspose.email.printing/) namespace is designed to provide tools necessary for printing email messages directly from applications. A printer for mail messages is represented by the [MailPrinter](https://reference.aspose.com/email/net/aspose.email.printing/mailprinter/) class. This class offers a set of functionalities to facilitate printing of various message formats, including MSG, EML, and MHTML. The MailPrinter makes it possible to customize the print layout, tailor page settings to ensure that rendered emails meet specific requirements.

## **Aspose.Email.Storage.Mbox**
**Provides classes for working with MBOX format**

The [Aspose.Email.Storage.Mbox](https://reference.aspose.com/email/net/aspose.email.storage.mbox/) namespace offers a suite of classes designed for managing and manipulating MBOX file formats, which are widely used for storing collections of email messages. The central classes of this namespace are [MboxStorageReader](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragereader/) class and [MboxStorageWriter](https://reference.aspose.com/email/net/aspose.email.storage.mbox/mboxstoragewriter/), which serve as the main components for interacting with MBOX files.
The MboxrdStorageReader class provides capabilities to read and traverse through MBOX files. It allows developers to extract individual email messages, giving them the ability to process or analyze email content programmatically. Furthermore, this class supports the seamless conversion of extracted messages to other popular email formats such as EML or MSG, expanding its utility in diverse application scenarios.
The MboxrdStorageWriter class is designed to create and write MBOX files.

## **Aspose.Email.Storage.Olm**
**Provides classes for working with Microsoft Outlook OLM file format**

The [Aspose.Email.Storage.Olm](https://reference.aspose.com/email/net/aspose.email.storage.olm/) namespace is a set of classes designed for managing and manipulating Microsoft Outlook. OLM file formats, which are primarily used for storing email data on MacOS. Here the [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) class is the main component responsible for interacting with OLM files. The OlmStorage class empowers developers with the ability to load OLM files and then extract, read, and manipulate their content including emails, contacts, calendar items, and notes. Particularly, it enables the browsing of folder hierarchies, filtering of specific message types, and efficient data extraction.

## **Aspose.Email.Storage.Pst**
**Provides classes for working with Microsoft Outlook PST/OST file format**

The [Aspose.Email.Storage.Pst](https://reference.aspose.com/email/net/aspose.email.storage.pst/) namespace offers classes designed for handling Microsoft Outlook PST and OST file formats, which are essential for managing email data on Windows. Central to this namespace is the [PersonalStorage](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/) class, the primary component responsible for interacting with PST and OST files. The PersonalStorage class provides features for loading, creating, and manipulating these file types. It allows developers to perform a wide range of operations, including the extraction and management of emails, contacts, calendar entries, tasks, and notes. The class also supports hierarchical folder navigation, enabling efficient data organization and retrieval. Additionally, the PersonalStorage class facilitates the conversion of PST and OST contents to various other formats such as EML, MSG, or MBOX, thereby broadening its utility.

## **Aspose.Email.Storage.Zimbra**
**Provides classes for working with Zimbra storage**

[Aspose.Email.Storage.Zimbra](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/) is a namespace within the Aspose.Email library with the [TgzReader](https://reference.aspose.com/email/net/aspose.email.storage.zimbra/tgzreader/#tgzreader-class) class which serves for accessing and managing Zimbra TGZ (Tar GZip) archives. The TgzReader class offers capabilities to work with email archives, including the ability to parse and extract emails, contacts, and calendar items from TGZ files, particularly, reading TGZ archives, iterating through their contents, and programmatically accessing individual items for customized processing.

## **Aspose.Email.Tools.Logging**
**Provides classes for logging functionality**

The [Aspose.Email.Tools.Logging](https://reference.aspose.com/email/net/aspose.email.tools.logging/) is a namespace for incorporating logging functionality within email-based applications. The main component class within this namespace is the [LoggerManager](https://reference.aspose.com/email/net/aspose.email.tools.logging/loggermanager/#loggermanager-class) class, which is designed to offer logging capabilities, allowing applications to track and record various operational events.

## **Aspose.Email.Tools.Merging**
**Contains classes for constructing email messages using templates**

The [Aspose.Email.Tools.Merging](https://reference.aspose.com/email/net/aspose.email.tools.merging/) ia a namespace for  automating the creation of tailored email messages through templating. At the heart of this namespace is the [TemplateEngine](https://reference.aspose.com/email/net/aspose.email.tools.merging/templateengine/) class, which is the primary class responsible for constructing email messages using templates. The TemplateEngine class enables the merging of data into predefined templates, allowing for the substitution of placeholders with actual information. This is particularly useful for generating personalized emails in bulk, ensuring each recipient receives a unique message tailored to their specific context.

## **Aspose.Email.Tools.Search**
**Contains base classes for message search by criteria**

The [Aspose.Email.Tools.Search](https://reference.aspose.com/email/net/aspose.email.tools.search/) namespace is designed to streamline the process of locating email messages based on a wide range of criteria. The cornerstone of this namespace is the [MailQuery](https://reference.aspose.com/email/net/aspose.email.tools.search/mailquery/) class, which serves as the main component responsible for defining search parameters and executing queries against email stores. With MailQuery, you can specify various search conditions such as sender, recipient, subject keywords, date ranges, and even content-specific terms. This capability allows filtering and retrieving relevant email messages from extensive archives or current mailboxes. MailQuery supports the construction of complex queries using logical operators.

## **Aspose.Email.Tools.Verifications**
**Provides classes for message validating functionality**

The [Aspose.Email.Tools.Verifications](https://reference.aspose.com/email/net/aspose.email.tools.verifications/) namespace offers classes that are essential for ensuring the integrity and validity of email messages. At the heart of this namespace is the [EmailValidator](https://reference.aspose.com/email/net/aspose.email.tools.verifications/emailvalidator/#emailvalidator-class) class, which serves as the primary component for implementing various validation checks on emails.

## **Aspose.Email.Windows.Forms**
**Contains classes for handling files dragged from Outlook in Windows Forms applications**

[Aspose.Email.Windows.Forms](https://reference.aspose.com/email/net/aspose.email.windows.forms/) is a specialized namespace designed to facilitate the integration of email-related functionalities within Windows Forms applications, particularly focusing on handling files dragged from Microsoft Outlook. The main component class in this namespace, [FileDropTargetManager](FileDropTargetManager), provides developers with capabilities to manage and process drag-and-drop operations involving Outlook items. FileDropTargetManager allows applications to capture, handle, and process email messages, attachments, and other Outlook elements when they are dragged into a Windows Forms application. With this class, you can implement features such as extracting and displaying the content of dragged items, saving attachments to specific locations, or triggering custom actions based on the type of item dropped.

## **Aspose.Email.Windows.WPF**
**Contains classes for handling files dragged from Outlook in Windows Presentation Foundation (WPF) applications**

The [Aspose.Email.Windows.WPF](https://reference.aspose.com/email/net/aspose.email.windows.wpf/) namespace is designed to enable the integration of email-related functionalities within WPF applications, particularly focusing on handling files dragged from Microsoft Outlook. The cornerstone of this namespace is the [FileDropPanel](https://reference.aspose.com/email/net/aspose.email.windows.wpf/filedroppanel/) class, which allows developers to implement drag-and-drop operations. The FileDropPanel acts as a specialized panel that captures items dragged from Outlook, including emails, attachments, and other related elements. It automatically detects when items are dropped onto the panel and provides events and methods to process these items accordingly. By utilizing FileDropPanel, developers can extract email content, save attachments to specified locations, or execute custom business logic based on the type of item received.
