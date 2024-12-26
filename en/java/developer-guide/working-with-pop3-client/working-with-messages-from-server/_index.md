---
title: Working with Messages from Server
ArticleTitle: Working with Messages from Server
type: docs
weight: 50
url: /java/working-with-messages-from-server/
---


## **Getting Mailbox Information**

We can get information about the mailbox such as the number of messages and the mailbox size using the [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) and [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) methods of the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class.

- The [getMailBoxSize](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxSize--) method returns the size of the mailbox in bytes.
- The [getMailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#getMailboxInfo--) method returns an object of type [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/).

It is also possible to get the number of messages using the [MessageCount](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getMessageCount--) property and the size using the [OccupiedSize](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/#getOccupiedSize--) property of the [Pop3MailBoxInfo](https://reference.aspose.com/email/java/com.aspose.email/pop3mailboxinfo/) class. The following sample code shows how to get information about the mailbox. It shows how to:

1. Create a [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/).
1. Connect to a POP3 server.
1. Get the size of the mailbox.
1. Get mailbox info.
1. Get the number of messages in the mailbox.
1. Get the occupied size.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

Pop3Client client = new Pop3Client();
// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

// Get the size of the mailbox, Get mailbox info, number of messages in the mailbox
long nSize = client.getMailboxSize();
System.out.println("Mailbox size is " + nSize + " bytes.");
Pop3MailboxInfo info = client.getMailboxInfo();
int nMessageCount = info.getMessageCount();
System.out.println("Number of messages in mailbox are " + nMessageCount);
long nOccupiedSize = info.getOccupiedSize();
System.out.println("Occupied size is " + nOccupiedSize);
~~~

## **Getting Email Count in the Mailbox**

The following code snippet shows you how to count the email messages in a mailbox.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
Pop3Client client = new Pop3Client("pop3.server.com", "username", "password");
try {
    client.setSecurityOptions(SecurityOptions.Auto);
    int i = client.getMessageCount();
    System.out.println("Message count: " + i);
} catch (Pop3Exception ex) {
    System.out.println("Error:" + ex.toString());
}
~~~

Aspose.Email lets developers work with emails in many different ways. For example, they can retrieve header information before deciding whether to download an email. Or they can retrieve emails from a server and save them without parsing them (quicker) or after parsing them (slower). This article shows how to retrieve and convert emails.

## **Retrieving Email Headers Information**

Email headers can give us information about an email message that we can use to decide whether or not to retrieve the whole email message. Typically, the header information contains sender, subject, received date, etc. (Email headers are described in detail in [Customizing Email Headers](/email/java/creating-and-setting-contents-of-emails/#set-email-headers). That topic is specifically about sending an email with SMTP, but the email header content information remains valid for POP3 emails). The following examples show how to retrieve email headers from a POP3 server by the message sequence number.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username. password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    HeaderCollection headers = client.getMessageHeaders(1);
    for (int i = 0; i < headers.size(); i++) {
        // Display key and value in the header collection
        System.out.print(headers.getKey(i));
        System.out.print(" : ");
        System.out.println(headers.get(i));
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Retrieving Email Messages**

The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class component provides the capability to retrieve email messages from the POP3 server, and parse them into a [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance with the help of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) components. The [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) class contains several properties and methods for manipulating email content. By using [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) method of the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class, you can get a [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/) instance directly from the POP3 server. The following code snippet shows you how to retrieve a complete email message from the POP3 server.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);
try {
    int messageCount = client.getMessageCount();
    // Create an instance of the MailMessage class and Retrieve message
    MailMessage message;
    for (int i = 1; i <= messageCount; i++) {
        message = client.fetchMessage(i);
        System.out.println("From:" + message.getFrom());
        System.out.println("Subject:" + message.getSubject());
        System.out.println(message.getHtmlBody());
    }
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Retrieving Message Summary Information using Unique Id**

The POP3 Client of the API can retrieve message summary information from the server using the unique id of the message. This provides quick access to the message short information without first retrieving the complete message from the server. The following code snippet shows you how to retrieve message summary information.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
String uniqueId = "unique id of a message from server";
Pop3Client client = new Pop3Client("host.domain.com", 456, "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
Pop3MessageInfo messageInfo = client.getMessageInfo(uniqueId);

if (messageInfo != null) {
    System.out.println(messageInfo.getSubject());
    System.out.println(messageInfo.getDate());
}
~~~

## **Listing Messages with MultiConnection**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) provides a [UseMultiConnection](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setUseMultiConnection-int-) property which can be used to create multiple connections for heavy operations. You may also set the number of connections to be used during multiconnection mode by using [Pop3Client.ConnectionsQuantity](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#setConnectionsQuantity-int-). The following code snippet demonstrates the use of the multiconnection mode for listing messages and compares its performance with the single connection mode.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of the Pop3Client class
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

pop3Client.setConnectionsQuantity(5);
pop3Client.setUseMultiConnection(MultiConnectionMode.Enable);
long multiConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol1 = pop3Client.listMessages();
long multiConnectionModeTimeSpan = System.currentTimeMillis() - multiConnectionModeStartTime;

pop3Client.setUseMultiConnection(MultiConnectionMode.Disable);
long singleConnectionModeStartTime = System.currentTimeMillis();
Pop3MessageInfoCollection messageInfoCol2 = pop3Client.listMessages();
long singleConnectionModeTimeSpan = System.currentTimeMillis() - singleConnectionModeStartTime;

System.out.println("multyConnectionModeTimeSpan: " + multiConnectionModeTimeSpan);
System.out.println("singleConnectionModeTimeSpan: " + singleConnectionModeTimeSpan);
double performanceRelation = singleConnectionModeTimeSpan / multiConnectionModeTimeSpan;
System.out.println("Performance Relation: " + performanceRelation);
~~~

{{% alert color="primary" %}} 

Please note that the usage of multiconnection mode does not guarantee performance increase.

{{% /alert %}} 

## **Fetching Messages from Server and saving to Disc**

### **Save Message to Disk without Parsing**

If you want to download email messages from the POP3 server without parsing them, use the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage\(java.lang.String,%20java.io.OutputStream\)) function. The [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) function does not parse the email message so it is faster than the [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) function. The following code snippet shows how to save a message by its sequence number, in this case, number 1. The [saveMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#saveMessage-com.aspose.email.IConnection-java.lang.String-java.io.OutputStream-) method saves the message in the original EML format without parsing it.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "pop3/";
String dstEmail = dataDir + "InsertHeaders.eml";

// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username, password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Save message to disk by message sequence number
    client.saveMessage(1, dstEmail);
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
}
System.out.println("Retrieved email messages using POP3 ");
~~~

### **Parse Message Before Saving**

The following code snippet uses the [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) [fetchMessage](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessage-int-) method to retrieve a message from a POP3 server by its sequence number, then save the message to disk using the subject as the file name.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// The path to the File directory.
String dataDir = "pop3/";

// Create an instance of the Pop3Client class
Pop3Client client = new Pop3Client();

// Specify host, username and password, Port and SecurityOptions for your client
client.setHost("pop.gmail.com");
client.setUsername("your.username@gmail.com");
client.setPassword("your.password");
client.setPort(995);
client.setSecurityOptions(SecurityOptions.Auto);

try {
    // Fetch the message by its sequence number and Save the message using its subject as the file name
    MailMessage msg = client.fetchMessage(1);
    msg.save(dataDir + "first-message_out.eml", SaveOptions.getDefaultEml());
    client.dispose();
} catch (Exception ex) {
    System.out.println(ex.getMessage());
} finally {
    client.dispose();
}
~~~

## **Group Fetch Messages**

[Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) provides a [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) method which accepts iterable of Sequence Numbers or Unique ID and returns a list of [MailMessage](https://reference.aspose.com/email/java/com.aspose.email/mailmessage/). The following code snippet demonstrates the use of the [fetchMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#fetchMessagesBySequences-com.aspose.email.IConnection-java.lang.Iterable-java.lang.Integer--) method to fetch messages by Sequence Numbers and Unique ID.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Create an instance of the Pop3Client class
Pop3Client pop3Client = new Pop3Client();
pop3Client.setHost("<HOST>");
pop3Client.setPort(995);
pop3Client.setUsername("<USERNAME>");
pop3Client.setPassword("<PASSWORD>");

Pop3MessageInfoCollection messageInfoCol = pop3Client.listMessages();
System.out.println("ListMessages Count: " + messageInfoCol.size());

List<Integer> sequenceNumberAr = new ArrayList<Integer>();
List<String> uniqueIdAr = new ArrayList<String>();
for (Pop3MessageInfo mi : messageInfoCol) {
    sequenceNumberAr.add(mi.getSequenceNumber());
    uniqueIdAr.add(mi.getUniqueId());
}

for (MailMessage m : pop3Client.fetchMessagesBySequences(sequenceNumberAr)) {
    System.out.println("FetchMessages-sequenceNumberAr : " + m.getSubject());
}

for (MailMessage m : pop3Client.fetchMessagesByUids(uniqueIdAr)) {
    System.out.println("FetchMessages-uniqueIdAr : " + m.getSubject());
}
~~~

## **Filtering Messages on Sender, Recipient or Date**

The [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) class, described in [Connecting to a POP3 Server](/email/java/connect-to-pop3-server/#connecting-to-pop3-server), provides the [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) method which gets all the messages from a mailbox. To get only messages which match some condition, use the overloaded [listMessages](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages--) method which takes [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) as an argument. The [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) class provides various properties for specifying the query conditions, for example, date, subject, sender, recipient and so on. The [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) class is used to build the search expression. First, all the conditions and constraints are set and then [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) is filled with the query developed by [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/). The [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) class object is used by [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client/) to extract the filtered information from the server. This article shows how to filter email messages from a mailbox. The first example illustrates how to filter messages based on a date and a subject. We also show how to filter on other criteria and how to build more complex queries. It also shows the application of Date and Time filter to retrieve the specific emails from the mailbox. In addition, it also shows how to apply case-sensitive filtering.

### **Filtering Messages from Mailbox**

To filter messages from a mailbox:

1. [Connect and log in to a POP3 server](/email/java/connect-to-pop3-server#connecting-to-pop3-server).
1. Create an instance of [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) and set the desired properties.
1. Call the [Pop3Client.listMessages(MailQuery query)](https://reference.aspose.com/email/java/com.aspose.email/pop3client/#listMessages-com.aspose.email.MailQuery-) method and pass the [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) in parameters to get the filtered messages only.

The following code snippet shows you how to connect to a POP3 mailbox and get messages that arrived today and have the word "newsletter" in the subject.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to POP3
String host = "host";
int port = 110;
String username = "user@host.com";
String password = "password";
Pop3Client client = new Pop3Client(host, port, username, password);

// Set conditions, Subject contains "Newsletter", Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getSubject().contains("Newsletter");
builder.getInternalDate().on(new Date());
// Build the query and Get list of messages
MailQuery query = builder.getQuery();
Pop3MessageInfoCollection messages = client.listMessages(query);
System.out.println("Pop3: " + messages.size() + " message(s) found.");
~~~

### **Getting Messages that Meet Specific Criteria**

[The code samples above](/email/java/working-with-messages-from-server/#filtering-messages-from-mailbox) filters messages based on the email subject and date. We can use other properties to set other supported conditions as well. Below are some examples of setting the conditions using [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/).

The code snippets that follow show how to filter emails on other criteria:

- Find emails delivered today.
- Find emails received within a range.
- Find emails from a specific sender.
- Find emails sent from a specific domain.
- Find emails sent to a specific recipient.
  
#### **Today's Date**

The following code snippet shows you how to find emails delivered today.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived today
MailQueryBuilder builder = new MailQueryBuilder();
builder.getInternalDate().on(new Date());
~~~

#### **Date Range**

The following code snippet shows you how to find emails received within a range.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails that arrived in last 7 days
Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Specific Sender**

The following code snippet shows you how to find emails from a specific sender.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific sender
builder.getFrom().contains("saqib.razzaq@127.0.0.1");
~~~

#### **Specific Domain**

The following code snippet shows you how to find emails sent from a specific domain.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails from specific domain
builder.getFrom().contains("SpecificHost.com");
~~~

#### **Specific Recipient**

The following code snippet shows you how to find emails sent to a specific recipient.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Get emails sent to specific recipient
builder.getTo().contains("recipient");
~~~

### **Building Complex Queries**

If different [MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) properties are set in separate statements, then all the conditions would be matched. For example, if we want to get messages between a date range and from a specific host, we need to write three statements.

#### **Combining Queries with AND**

The following code snippet shows you how to combine queries with AND.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Emails from specific host, get all emails that arrived before today and all emails that arrived since 7 days ago
builder.getFrom().contains("SpecificHost.com");

Calendar calendar = Calendar.getInstance();

builder.getInternalDate().before(calendar.getTime());
calendar.add(Calendar.DATE, -7);
builder.getInternalDate().since(calendar.getTime());
~~~

#### **Combining Queries with OR**

[MailQueryBuilder](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/) provides the [or](https://reference.aspose.com/email/java/com.aspose.email/mailquerybuilder/#or-com.aspose.email.MailQuery-com.aspose.email.MailQuery-) method which takes two [MailQuery](https://reference.aspose.com/email/java/com.aspose.email/mailquery/) instances as parameters. It gets the messages that match any of the two conditions specified. The following code snippet shows how to filter messages that either have "test" in the subject or "noreply@host.com" as the sender. The following code snippet shows you how to combine queries with OR.

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Specify OR condition
builder.or(builder.getSubject().contains("test"), builder.getFrom().contains("noreply@host.com"));
~~~

#### **Applying Case Sensitive Filters**

The API also provides the capability to filter emails from the mailbox based on a case sensitive criteria. The following methods provide the capability to search emails specifying case sensitive flag.

- Method StringComparisonField.contains(String value, boolean ignoreCase)
- Method StringComparisonField.equals(String value, boolean ignoreCase)
- Method StringComparisonField.notContains(String boolean, bool ignoreCase)
- Method StringComparisonField.notEquals(String boolean, bool ignoreCase)

~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// IgnoreCase is True
MailQueryBuilder builder1 = new MailQueryBuilder();
builder1.getFrom().contains("tesT", true);
MailQuery query1 = builder1.getQuery();
Pop3MessageInfoCollection messageInfoCol1 = client.listMessages(query1);
~~~
