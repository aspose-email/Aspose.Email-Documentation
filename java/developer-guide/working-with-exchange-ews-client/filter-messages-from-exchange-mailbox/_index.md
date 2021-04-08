---
title: Filter Messages From Exchange Mailbox
type: docs
weight: 30
url: /java/filter-messages-from-exchange-mailbox/
---


{{% alert color="primary" %}} 

Aspose.Email for Java provides the capability to filter messages from Exchange Mailbox using the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/EWSClient) and [ExchangeQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeQueryBuilder). Messages can be filtered via different criteria such as by date, domain, message-id, and by Mail Delivery Notifications. This article shows how to filter messages from Exchange Server using different Criteria.

{{% /alert %}} 
## **Filtering Messages using EWS**
The [IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) class provides the [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(\)) method which gets all messages from a mailbox. To get only messages which match some condition, use the overloaded [listMessages()](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient#listMessages\(java.lang.String,%20com.aspose.email.MailQuery\)) method which takes the [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) class as an argument. The [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) class provides various properties for specifying conditions, for example, date, subject, sender and recipient. In addition, the API also allows applying case-sensitivity filters for retrieving emails from the mailbox.
### **Filtering Messages**
To get filtered messages from a mailbox:

1. Connect to the Exchange server.
1. Create an instance of MailQuery and set the desired properties.
1. Call the IEWSClient.listMessages() method and pass the MailQuery in the parameters to get the filtered messages only.

The following code snippet shows you how to connect to an IMAP mailbox and get messages that have the string "Newsletter" in the subject and were sent today.

~~~Java
try {
    // Connect to EWS
    final String mailboxUri = "https://outlook.office365.com/ews/exchange.asmx";
    final String username = "username";
    final String password = "password";
    final String domain = "domain";

    IEWSClient client = EWSClient.getEWSClient(mailboxUri, username, password, domain);

    // Query building by means of ExchangeQueryBuilder class
    ExchangeQueryBuilder builder = new ExchangeQueryBuilder();

    // Set Subject and Emails that arrived today
    builder.getSubject().contains("Newsletter");
    builder.getInternalDate().on(new Date());

    MailQuery query = builder.getQuery();

    // Get list of messages
    ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
    System.out.println("EWS: " + messages.size() + " message(s) found.");

    // Disconnect from EWS
    client.dispose();
} catch (java.lang.RuntimeException ex) {
    System.out.println(ex.getMessage());
}
~~~
### **Filter Messages on Criteria**
The code samples above filters messages based on the email subject and date. We can filter on other properties too. Below are some examples of setting the conditions using [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery).
#### **Filter Criteria Today's Date**
The following code snippet shows you how to filter all emails on the basis of today's date.

~~~Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Filter Criteria Date Range**
The following code snippet shows you how to filter all emails on the basis of the date range.



~~~Java
// Emails that arrived in last 7 days
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Filter Criteria Specific Sender**
The following code snippet shows you how to filter all emails on the basis of a specific sender.

~~~Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Filter Criteria Specific Domain**
The following code snippet shows you how to filter all emails on the basis of a specific domain.

~~~Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Filter Criteria Specific Recipient**
The following code snippet shows you how to filter all emails on the basis of a specific recipient.

~~~Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
#### **Filter Criteria By MessageID**
The following code snippet shows you how to filter all emails on the basis of MessageID.

~~~Java
// Get email with specific MessageId
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getMessageId().equals("MessageID");
~~~
#### **Filter Criteria All Mail Delivery Notifications**
The following code snippet shows you how to filter all emails on the basis of all mail delivery notifications.

~~~Java
// Get Mail Delivery Notifications
builder = new ExchangeQueryBuilder();
builder.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
#### **Filter by Message Size**
~~~Java
builder = new ExchangeQueryBuilder();
builder.getItemSize().greater(80000);
~~~
### **Building Complex Queries**
If different [MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) properties are set in a separate statement, all the conditions are matched. For example, to get a message in a particular date range and from a specific host, write three statements:
#### **Combining Queries with AND**
The following code snippet shows you how to Combine Queries with AND.

~~~Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");
Calendar cal = Calendar.getInstance();
builder.getInternalDate().before(cal.getTime());
cal.add(Calendar.DATE, -7);
builder.getInternalDate().since(cal.getTime());
~~~
#### **Combining Queries with OR**
[MailQueryBuilder](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder) provides the [or()](https://apireference.aspose.com/email/java/com.aspose.email/MailQueryBuilder#or\(com.aspose.email.MailQuery,%20com.aspose.email.MailQuery\)) method which takes two [MailQuery](https://apireference.aspose.com/email//java/com.aspose.email/mailquery) instances as parameters. It gets messages that match any of the two conditions specified. The example below filters messages that either have the word "test" in the subject or "noreply@host.com" as the sender. The following code snippet shows you how to combine queries with OR.

~~~Java
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
### **Case-Sensitive Email Filtering**
Emails can be filtered based on case-sensitivity by specifying the IgnoreCase flag in the filter criteria as shown in the following code snippet.

~~~Java
// Query building by means of ExchangeQueryBuilder class
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
builder.getSubject().contains("Newsletter", true);
builder.getInternalDate().on(new Date());
MailQuery query = builder.getQuery();
~~~
## **Filtering Messages with Paging Support**
~~~Java
int itemsPerPage = 5;
String sGuid = UUID.randomUUID().toString();
String str1 = sGuid + " - " + "Query 1";
String str2 = sGuid + " - " + "Query 2";

MailQueryBuilder queryBuilder1 = new MailQueryBuilder();
queryBuilder1.getSubject().contains(str1);
MailQuery query1 = queryBuilder1.getQuery();
List<ExchangeMessagePageInfo> pages = new ArrayList<ExchangeMessagePageInfo>();
ExchangeMessagePageInfo pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), query1, itemsPerPage);
pages.add(pageInfo);
int str1Count = pageInfo.getItems().size();
while (!pageInfo.getLastPage()) {
    pageInfo = client.listMessagesByPage(client.getMailboxInfo().getInboxUri(), query1, itemsPerPage, pageInfo.getPageOffset() + 1);
    pages.add(pageInfo);
    str1Count += pageInfo.getItems().size();
}
~~~