---
title: Filter Messages from Server using IMAP Client
type: docs
weight: 40
url: /java/filter-messages-from-server-using-imap-client/
---


The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) class provides the [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#listMessages\(\)) method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#listMessages\(\)) method which takes [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery) as an argument. The [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery) class provides various properties for specifying the conditions, for example, date, subject, sender, recipient and so on. The first example illustrates how to filter messages based on date and subject. We also show how to filter on other criteria and how to build more complex queries. The API also provides the capability to apply case-sensitive searching criteria to match exact filtering criteria. The API also allows specifying the search string encoding for filtering messages from the mailbox.
## **Filtering Messages from Mailbox**
1. [Connect and log in to an IMAP server](/email/java/connecting-to-imap-server#connecting-with-imap-server)
1. Create an instance of the [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery) and set the properties
1. Call the [ImapClient.listMessages(MailQuery query)](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient#listMessages\(com.aspose.email.MailQuery\)) method and pass the [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery) with the parameters to get filtered messages only.

The following code snippet shows you how to connect to an IMAP mailbox and get messages that arrived today and have the word "newsletter" in the subject.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");
// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Build the query and Get list of messages
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
System.out.println("Imap: " + messages.size() + " message(s) found.");
// Disconnect from IMAP
client.dispose();
~~~
## **Get Messages that Meet Specific Criteria**
[The code samples above](#filtering-messages-from-mailbox) filter messages based on the email subject and date. We can use other properties to set other supported conditions as well. Below are some examples of setting the conditions using [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery). The code snippets that follow show how to filter emails on:

1. Today's date.
1. A date range.
1. From a specific sender.
1. From a specific domain.
1. From a specific recipient.
### **Today's Date**
The following code snippet shows you how to filter emails on Today's Date.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
### **Date Range**
The following code snippet shows you how to filter emails on the date range.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived in last 7 days
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
### **Specific Sender**
The following code snippet shows you how to filter emails on a specific sender.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
### **Specific Domain**
The following code snippet shows you how to filter emails on a specific domain.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
### **Specific Recipient**
The following code snippet shows you how to filter emails on a specific recipient.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
## **Building Complex Queries**
If different [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) properties are set in separate statements, then all the conditions would be matched. For example, if we want to get messages between a date range and from a specific host, we need to write three statements.
### **Combining Queries with AND**
The following code snippet shows you how to combine queries with AND.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");

Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
### **Combining Queries with OR**
[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) provides the [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) method which takes two [MailQuery](https://apireference.aspose.com/email/java/com.aspose.email/mailquery) instances as parameters. It gets the messages that match any of the two conditions specified. The following code snippet shows how to filter messages that either have “test” in the subject or “noreply@host.com” as the sender. The following code snippet shows you how to combine queries with OR.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
## **Filtration on InternalDate**
Messages can be extracted from the server based upon the InternalDate however sometimes the server does not return all messages as visible in the inbox. Its reason can be the server timezone because it may not be UTC for all the servers like [Gmail](https://www.google.com.ua/search?client=opera&q=timezone+gmail&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#channel=suggest&q=gmail+server+timezone++). Aspose sends commands like 008 SEARCH ON 4-May-2014 as per the [IMAP protocol](http://tools.ietf.org/html/rfc1730) however result can differ due to server timezone settings. A new member is added in [ImapMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/imapmessageinfo) as [InternalDate](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfo#getInternalDate\(\)) which further helps in filtering the messages. The following code snippet shows the use of [InternalDate](https://apireference.aspose.com/email/java/com.aspose.email/ImapMessageInfo#getInternalDate\(\)) to filter messages.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
final String host = "host";
final int port = 143;
final String username = "user@host.com";
final String password = "password";
ImapClient client = new ImapClient(host, port, username, password);
client.selectFolder("Inbox");

// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());

// Build the query and Get list of messages
MailQuery query = builder.getQuery();
ImapMessageInfoCollection messages = client.listMessages(query);
for (ImapMessageInfo info : messages) {
    System.out.println("Internal Date: " + info.getInternalDate());
}

// Disconnect from IMAP
client.dispose();
~~~
### **Case-Sensitive Emails Filtering**
The following code snippet shows you how to use case-sensitive emails filtering.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set conditions, Subject contains "Newsletter", Emails that arrived today
ImapQueryBuilder builder = new ImapQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~
### **Specify Encoding for Query Builder**
The API's [ImapQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ImapQueryBuilder) constructor can be used to specify the Encoding for the search string. This can also be set using the [DefaultEncoding](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#getDefaultEncoding\(\)) property of the MailQueryBuilder. The following code snippet shows you how to specify the encoding for query builder.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Set conditions
ImapQueryBuilder builder = new ImapQueryBuilder(Charset.forName("utf-8"));
builder.getSubject().contains("ğüşıöç", true);
MailQuery query = builder.getQuery();
~~~
### **Filter Messages with Paging Support**
The [ImapClient](https://apireference.aspose.com/email/java/com.aspose.email/ImapClient) provides the capability to search for messages from the mailbox and list them with paging support. The following code snippet shows you how to filter messages with paging support.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
/// <summary>
/// This example shows how to search for messages using ImapClient of the API with paging support
/// Introduced in Aspose.Email for .NET 6.4.0
/// </summary>
final ImapClient client = new ImapClient("host.domain.com", 84, "username", "password");
try {
    try {
        // Append some test messages
        int messagesNum = 12;
        int itemsPerPage = 5;
        MailMessage message = null;
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), "111111111111111");
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }
        String body = "2222222222222";
        for (int i = 0; i < messagesNum; i++) {
            message = new MailMessage("from@domain.com", "to@domain.com", "EMAILNET-35128 - " + UUID.randomUUID(), body);
            client.appendMessage(ImapFolderInfo.IN_BOX, message);
        }

        client.selectFolder("Inbox");
        ImapQueryBuilder iqb = new ImapQueryBuilder();
        iqb.getBody().contains(body);
        MailQuery query = iqb.getQuery();

        client.selectFolder(ImapFolderInfo.IN_BOX);
        ImapMessageInfoCollection totalMessageInfoCol = client.listMessages(query);
        System.out.println(totalMessageInfoCol.size());

        //////////////////////////////////////////////////////

        List<ImapPageInfo> pages = new ArrayList<ImapPageInfo>();

        PageSettings ps = new PageSettings();
        ps.setFolderName(ImapFolderInfo.IN_BOX);
        PageInfo pi = new PageInfo(itemsPerPage);
        ImapPageInfo pageInfo = client.listMessagesByPage(query, pi, ps);

        pages.add(pageInfo);
        while (!pageInfo.getLastPage()) {
            pageInfo = client.listMessagesByPage(query, pageInfo.getNextPage(), ps);
            pages.add(pageInfo);
        }
        int retrievedItems = 0;
        // foreach to while statements conversion
        for (ImapPageInfo folderCol : pages) {
            retrievedItems += folderCol.getItems().size();
        }
    } finally {
    }
} finally {
    if (client != null)
        client.dispose();
}
~~~
## **Filter Messages with Custom Flag**
~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
ImapQueryBuilder queryBuilder = new ImapQueryBuilder();

queryBuilder.hasFlags(ImapMessageFlags.keyword("custom1"));

queryBuilder.hasNoFlags(ImapMessageFlags.keyword("custom2"));
~~~
