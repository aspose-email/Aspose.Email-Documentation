---
title: Mail Services
ArticleTitle: Mail Services
type: docs
weight: 8
url: /net/mail-services/
---

## **API to Access Mail Services**

### **Exchange Web Dav (has been officially deprecated)**

**Exchange WebDAV (Web Distributed Authoring and Versioning)** was a protocol extension used by Microsoft Exchange Server to allow clients to access and manipulate mail, calendar, and contact items stored on the server via HTTP. Although it has been officially deprecated, it played a significant role in the development of web-based and remote access to Exchange data.

### **EWS**

**Exchange Web Services (EWS)** is an API provided by Microsoft to interact with Microsoft Exchange Server. It allows developers to access and manipulate Exchange data such as emails, calendar events, contacts, and tasks programmatically. EWS was introduced to replace older protocols like WebDAV and provides a more robust and efficient way to work with Exchange data. 

It uses the SOAP (Simple Object Access Protocol) over HTTP and HTTPS to send and receive messages between the client and the Exchange server. The SOAP-based nature of EWS can be complex to implement and debug compared to RESTful APIs. Microsoft is gradually shifting towards Microsoft Graph API, which provides a more modern and RESTful approach to accessing Microsoft 365 data, including Exchange Online.

### **Microsoft Graph**

**Microsoft Graph** is a powerful API that provides a unified endpoint for accessing a wide range of data and services in the Microsoft 365 ecosystem. It allows developers to interact with a variety of Microsoft services, including Office 365, Azure Active Directory, SharePoint, OneDrive, Outlook, Microsoft Teams, and more. It serves as a gateway to data and insights across Microsoft 365.

**Key Features**

- The base URL for the API is https://graph.microsoft.com.
- Uses OAuth 2.0 for authentication and authorization.
- Leverages Microsoft's AI and machine learning capabilities for enhanced data insights.

### **Gmail API**

**Gmail API** is a RESTful API provided by Google that allows developers to interact programmatically with Gmail mailboxes and perform various operations on email data (read, send, delete, and organize email messages). It offers a more flexible and powerful alternative to the traditional IMAP and SMTP protocols, enabling developers to access and manage Gmail messages, threads, labels, drafts, and more. It is available through the Google Cloud Platform.

**Key Features**

- Perform multiple API requests in a single HTTP call to improve efficiency and reduce the number of network requests.
- Uses OAuth 2.0 for secure authentication and authorization, ensuring that applications only access data that users have explicitly granted permission for.
- Provides various permission scopes, allowing applications to request only the level of access they need (e.g., read-only access, full access).
- All API interactions occur over HTTPS to ensure secure communication between the application and Google’s servers.
