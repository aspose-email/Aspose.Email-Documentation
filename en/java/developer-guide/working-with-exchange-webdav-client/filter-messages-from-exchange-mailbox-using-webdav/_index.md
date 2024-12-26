---
title: Filter Messages from Exchange Mailbox using WebDav
ArticleTitle: Filter Messages from Exchange Mailbox using WebDav
type: docs
weight: 40
url: /java/filter-messages-from-exchange-mailbox-using-webdav/
---

{{% alert color="primary" %}} 

The [ExchangeClient](http://www.aspose.com/api/java/email/com.aspose.email/classes/ExchangeClient) class provides the listMessages() method which gets all messages from a mailbox. To get only messages which match some condition, use the overloaded listMessages() method which takes the [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) class as an argument. The [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery) class provides various properties for specifying conditions, for example date, subject, sender and recipient. In addition, the API also allows to apply case-sensitivity filters for retrieving emails from mailbox.

{{% /alert %}} 
## **Filter Messages using Web Dav**
To get filtered messages from a mailbox:

1. Connect to Exchange server.
1. Create an instance of MailQuery and set the desired properties.
1. Call the ExchangeClient.listMessages(MailQuery query) method and pass the MailQuery in the parameters to get the filtered messages only.

The code examples below show how to connect to an Exchange mailbox and get messages that have the string "Newsletter" in the subject and were sent today.


~~~Java
ExchangeClient client = new ExchangeClient("http://MachineName/exchange/Username", "username", "password", "domain");
SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");

// Query building by means of ExchangeQueryBuilder class
ExchangeQueryBuilder builder = new ExchangeQueryBuilder();
// Subject contains "Newsletter"
builder.getSubject().contains("Newsletter");

// Emails that arrived today
try {
	builder.getInternalDate().on(sdf.parse("10/05/2016 10:00:00"));
} catch (ParseException e) {
	e.printStackTrace();
}

// Build the query
MailQuery query = builder.getQuery();

// Get list of messages
ExchangeMessageInfoCollection messages = client.listMessages(client.getMailboxInfo().getInboxUri(), query, false);
System.out.println("Imap: " + messages.size() + " message(s) found.");
~~~
## **Get Messages that Meet Specific Criteria**
The code samples above filters messages based on the email subject and date. We can filter on other properties too. Below are some examples of setting the conditions using [MailQuery](http://www.aspose.com/api/java/email/com.aspose.email/classes/MailQuery).
#### **Filter Criteria Today’s Date**
The following code snippet shows you how to filter all emails on the basis of today’s date.


~~~Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~
#### **Filter Criteria Date Range**
The following code snippet shows you how to filter all emails on the basis of the date range.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().beforeOrEqual(new Date());
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(1)));
~~~
#### **Filter Criteria Specific Sender**
The following code snippet shows you how to filter all emails on the basis of a specific sender.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~
#### **Filter Criteria Specific Domain**
The following code snippet shows you how to filter all emails on the basis of a specific domain.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~
#### **Filter Criteria Specific Recipient**
The following code snippet shows you how to filter all emails on the basis of a specific recipient.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~
#### **Filter Criteria By MessageID**
The following code snippet shows you how to filter all emails on the basis of MessageID.


~~~Java
// Get email with specific MessageId
ExchangeQueryBuilder builder1 = new ExchangeQueryBuilder();
builder1.getMessageId().equals("MessageID");
~~~
#### **Filter Criteria All Mail Delivery Notifications**
The following code snippet shows you how to filter all emails on the basis of all mail delivery notifications.


~~~Java
// Get Mail Delivery Notifications
builder1 = new ExchangeQueryBuilder();
builder1.getContentClass().equals(ContentClassType.getMDN().toString());
~~~
## **Building Complex Queries**
If different QueryBuilder properties are set in separate statement, all the conditions are matched. For example,to get a message in a particular date range and from a specific host, write three statements:
#### **Combining Queries with AND**


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();

// Emails from specific host
builder.getFrom().contains("SpecificHost.com");
// AND all emails that arrived before today
builder.getInternalDate().before(new Date());
// AND all emails that arrived since 7 days ago
builder.getInternalDate().since(new Date(new Date().getTime() + TimeUnit.DAYS.toDays(-7)));
~~~
#### **Combining Queries with OR**
QueryBuilder provides the or() method which takes two MailQuery instances as parameters. It gets messages that match any of the two conditions specified. The example below filters messages that either has the word "test" in the subject or "noreply@host.com" as the sender.


~~~Java
MailQueryBuilder builder = new MailQueryBuilder();
		
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~
#### **Case-Sensitive Email Filtering**
Emails can be filtered based on case-sensitivity by specifying the IgnoreCase flag in the filter criteria as shown in the following example.


~~~Java
//IgnoreCase is True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
~~~
