---
title: Utility Features
type: docs
weight: 120
url: /java/utility-features/
---


## **Sending a Message with Voting Option**
Microsoft Outlook allows users to create a poll when composed a new message. This is done by including voting options such as Yes, No, Maybe, etc. The FollowUpOptions class offered by Aspose.Email, provides the VotingButtons property that can be used to set or get the value of the voting options. This article provides a detailed example of creating a MapiMessage with voting options for creating a poll and then sending the message using Exchange Web Service (EWS) client.
### **Creating and Sending a Message with Voting Options**
The following code snippet shows you how to create a new message and then send it with voting options.



~~~Java
String address = "firstname.lastname@aspose.com";

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
MailMessage message = createTestMessage(address);

// Set FollowUpOptions Buttons
FollowUpOptions options = new FollowUpOptions();
options.setVotingButtons("Yes;No;Maybe;Exactly!");

client.send(message, options);
~~~
### **Sample Methods Used in Examples**
The following code snippet shows you how to use methods used in above example.



~~~Java
private static MailMessage createTestMessage(String address) {
    MailMessage eml = new MailMessage(address, address, "Flagged message",
            "Make it nice and short, but descriptive. The description may appear in search engines' search results pages...");

    return eml;
}
~~~
## **Creating RE and FW messages from MSG files**
[IEWSClient](https://apireference.aspose.com/email/java/com.aspose.email/IEWSClient) lets developers create RE (Reply/Reply All) and FW (Forward) messages from a source message. The source message is identified by selecting a particular [ExchangeMessageInfo](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfo) from [ExchangeMessageInfoCollection](https://apireference.aspose.com/email/java/com.aspose.email/ExchangeMessageInfoCollection) obtained by IEWSClient.listMessages(). The other argument is the actual [MailMessage](https://apireference.aspose.com/email/java/com.aspose.email/MailMessage) to be sent as RE or FW message. The following code snippet shows you how to create a sample account is used to send a message and then the Reply and Forward message features are demonstrated against that sample message. To perform this task:

1. Initialize the IEWSClient object by providing valid credentials.
1. Send a few sample messages.
1. Call the IEWSClient.reply(), IEWSClient.replyAll() and IEWSClient.forward() functions to send messages.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);

try {
    MailMessage message = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");

    client.send(message);

    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
    if (messageInfoCol.size() == 1)
        System.out.println("1 message in Inbox");
    else
        System.out.println("Error! No message in Inbox");

    MailMessage message1 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");

    client.send(message1);
    messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());

    if (messageInfoCol.size() == 2)
        System.out.println("2 messages in Inbox");
    else
        System.out.println("Error! No new message in Inbox");

    MailMessage message2 = new MailMessage("user@domain.com", "user@domain.com", "TestMailRefw - " + UUID.randomUUID().toString(),
            "TestMailRefw Implement ability to create RE and FW messages from source MSG file");
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Test attachment 1", "Attachment Name 1"));
    message2.getAttachments().addItem(Attachment.createAttachmentFromString("Test attachment 2", "Attachment Name 2"));

    // Reply, Replay All and forward Message
    client.reply(message2, messageInfoCol.get_Item(0));
    client.replyAll(message2, messageInfoCol.get_Item(0));
    client.forward(message2, messageInfoCol.get_Item(0));
} catch (java.lang.RuntimeException ex) {
    System.out.println("Error in program" + ex.getMessage());
}
~~~
## **OAuth Support for EWS with Office 365**
Aspose.Email API provides support for Exchange Web Service (EWS) with Office 365. The API’s [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) interface provides overload method that provides the [OAuthNetworkCredential](https://apireference.aspose.com/email/java/com.aspose.email/OAuthNetworkCredential) as input for accessing the Exchange account via OAuth. User needs to provide the Authority, Client Id, Client App Uri, and Resource parameters for this to work. The following code snippet shows OAuth Support for EWS with Office 365.


~~~Java
// token provider
/*ITokenProvider provider = new ITokenProvider() {

    @Override
    public void dispose() {
    }

    @Override
    public OAuthToken getAccessToken(boolean ignoreExistingToken) {
        return null;
    }

    @Override
    public OAuthToken getAccessToken() {
        return null;
    }
};

NetworkCredential credentials = new OAuthNetworkCredential(provider);*/

// accessToken
NetworkCredential credentials = new OAuthNetworkCredential("accessToken");

IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", credentials);
client.listMessages();
~~~
## **Support for Logging in Exchange Clients**
Aspose.Email API provides the capability to provide logging facility of Exchange Web Service client.
### **Logging for EWS Client**


~~~Java
client.setLogFileName("logs/ews");
// OR
EWSClient.setCommonLogFileName("logs/ews");
~~~
## **Adding Headers in EWS Requests**
Aspose.Email API allows adding headers to Exchange requests. This can be used to add headers to the EWS requests for different headers that can be used for different purposes. Once such example could be adding the X-AnchorMailbox header that is used to manage the throttling issues on Exchange server. The addHeader method of the IEWSClient is used to add headers to the EWS requests as shown in the following code snippet.



~~~Java
final IEWSClient client = EWSClient.getEWSClient("exchange.domain.com/ews/Exchange.asmx", "username", "password", "");
try {
    client.addHeader("X-AnchorMailbox", "username@domain.com");
    ExchangeMessageInfoCollection messageInfoCol = client.listMessages(client.getMailboxInfo().getInboxUri());
} finally {
    client.dispose();
}
~~~

## **Return the Client Request ID in the Header**

The ```return-client-request-id``` header is sent in the request and used by the server to determine whether the ```client-request-id``` header specified by the client should be returned in the server response. The following methods are used in this operation:

- [getReturnClientRequestId()](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#getReturnClientRequestId--) 
- [setReturnClientRequestId(boolean value)](https://reference.aspose.com/email/java/com.aspose.email/iewsclient/#setReturnClientRequestId-boolean-) - Get or set a flag to indicate whether the client requires the server side to return the request id.

```java
try (IEWSClient client = createEWSClient())
{
    // Client will create random id and pass it to the server.
    // The server should include this id in request-id header of all responses.
    client.setReturnClientRequestId(true);
    
    client.setLogFileName("ews.log");
    client.getMailboxInfo();
}
```

## **Working with Unified Messaging**
Aspose.Email can retrieve unified messaging information from Exchange Server 2010. Unified messaging such as getting configuration information, initiating an outbound call, retrieving phone call information by call ID and disconnecting a phone call by ID is supported at present. The following code sample shows how to retrieve unified messaging configuration information from Microsoft Exchange Server 2010.



~~~Java
IEWSClient client = EWSClient.getEWSClient(mailboxUri, credential);
UnifiedMessagingConfiguration umConf = client.getUMConfiguration();
~~~
## **Getting Mail Tips**
Microsoft Exchange Server added several new features with Exchange Server 2010 and 2013. One of them lets users get mail tips when composing an email message. These tips are very useful as they provide information before the email is sent. For example, if an email address is wrong in the recipient’s list, a tip is displayed to let the you know that the email address is invalid. Mail tips also lets you see out of office replies before sending an email: Exchange Server (2010 & 2013) sends the mail tip when the email is being composed if one or more of the recipients have set out of office replies. Microsoft Exchange Server 2010 Service Pack 1 is required for all the features demonstrated in this article. The following code snippet shows you how to uses the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class which uses Exchange Web Services, available in Microsoft Exchange Server 2007 and later versions.



~~~Java
// Create instance of EWSClient class by giving credentials
IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser", "pwd", "domain");
System.out.println("Connected to Exchange server...");
// Provide mail tips options
MailAddressCollection addrColl = new MailAddressCollection();
addrColl.addMailAddress(new MailAddress("test.exchange@ex2010.local", true));
addrColl.addMailAddress(new MailAddress("invalid.recipient@ex2010.local", true));
GetMailTipsOptions options = new GetMailTipsOptions(MailAddress.to_MailAddress("administrator@ex2010.local"), addrColl, MailTipsType.All);

// Get Mail Tips
MailTips[] tips = client.getMailTips(options);

// Display information about each Mail Tip
for (MailTips tip : tips) {
    // Display Out of office message, if present
    if (tip.getOutOfOffice() != null) {
        System.out.println("Out of office: " + tip.getOutOfOffice().getReplyBody().getMessage());
    }

    // Display the invalid email address in recipient, if present
    if (tip.getInvalidRecipient() == true) {
        System.out.println("The recipient address is invalid: " + tip.getRecipientAddress());
    }
}
~~~
## **Exchange Impersonation**
Exchange impersonation allows someone to impersonate another account and perform tasks and operations using the impersonated account's permissions instead of their own. Where delegation lets users act on behalf of other users, Impersonation allows them to act as other users. Aspose.Email supports Exchange Impersonation. The [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class provides the ImpersonateUser and ResetImpersonation methods to facilitate this feature.

To perform this task:

1. Initialize the ExchangeWebServiceClient for user 1.
1. Initialize the ExchangeWebServiceClient for user 2.
1. Append test messages to the accounts.
1. Enable Impersonation.
1. Reset Impersonation.

The following code snippet shows you how to use the [EWSClient](https://apireference.aspose.com/email/java/com.aspose.email/ewsclient) class to implement the Impersonation feature.



~~~Java
// Create instance's of EWSClient class by giving credentials
IEWSClient client1 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser1", "pwd", "domain");
IEWSClient client2 = EWSClient.getEWSClient("https://outlook.office365.com/ews/exchange.asmx", "testUser2", "pwd", "domain");
{
    String folder = "Drafts";
    try {
        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
            client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj1 = "NETWORKNET_33354 User User1";
        client1.appendMessage(folder, new MailMessage("User1@exchange.conholdate.local", "To@aspsoe.com", subj1, ""));

        for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
            client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        String subj2 = "NETWORKNET_33354 User User2";
        client2.appendMessage(folder, new MailMessage("User2@exchange.conholdate.local", "To@aspose.com", subj2, ""));

        ExchangeMessageInfoCollection messInfoColl = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl.Count);
        // Assert.AreEqual(subj1, messInfoColl[0].Subject);

        client1.impersonateUser(ItemChoice.PrimarySmtpAddress, "User2@exchange.conholdate.local");
        ExchangeMessageInfoCollection messInfoColl1 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl1.Count);
        // Assert.AreEqual(subj2, messInfoColl1[0].Subject);

        client1.resetImpersonation();
        ExchangeMessageInfoCollection messInfoColl2 = client1.listMessages(folder);
        // Assert.AreEqual(1, messInfoColl2.Count);
        // Assert.AreEqual(subj1, messInfoColl2[0].Subject);
    } finally {
        try {
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client1.listMessages(folder))
                client1.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
            for (ExchangeMessageInfo messageInfo : (Iterable<ExchangeMessageInfo>) client2.listMessages(folder))
                client2.deleteItem(messageInfo.getUniqueUri(), DeletionOptions.getDeletePermanently());
        } catch (java.lang.RuntimeException e) {
        }
    }
}
~~~
## **Auto Discover Feature using EWS**
Aspose.Email API lets you discover about the Exchange Server settings using the EWS Client. 


~~~Java
AutodiscoverService svc = new AutodiscoverService();
svc.setCredentials(new NetworkCredential(email, password));

IGenericDictionary</* UserSettingName */Integer, Object> userSettings = svc.getUserSettings(email, UserSettingName.ExternalEwsUrl).getSettings();
String ewsUrl = (String) userSettings.get_Item(UserSettingName.ExternalEwsUrl);
System.out.println("Auto discovered EWS Url: " + ewsUrl);
~~~
## **Abort PST Restore to Exchange Server Operation**
Aspose.Email API lets you restore a PST file to Exchange Server. However, if the operation is taking long due to large size PST file, it may be required to specify criterion for aborting the operation. This can be achieved using the API as shown in the following sample code.


~~~Java
final IEWSClient client = EWSClient.getEWSClient("https://exchange.office365.com/ews/exchange.asmx", "username", "password");
try {
    final long startTime = System.currentTimeMillis();
    final AtomicInteger processedItems = new AtomicInteger(0);
    final long S15 = 15 * 1000;

    BeforeItemCallback callback = new BeforeItemCallback() {
        public void invoke(ItemCallbackArgs item) {
            if (System.currentTimeMillis() - startTime > S15) {
                throw new AbortRestoreException();
            }

            processedItems.incrementAndGet();
        }
    };

    try {
        // create a test pst and add some test messages to it
        PersonalStorage pst = PersonalStorage.create(new ByteArrayOutputStream(), FileFormatVersion.Unicode);
        FolderInfo folder = pst.getRootFolder().addSubFolder("My test folder");
        for (int i = 0; i < 20; i++) {
            MapiMessage message = new MapiMessage("from@gmail.com", "to@gmail.com", "subj", "body");
            folder.addMessage(message);
        }
        RestoreSettings rs = new RestoreSettings();
        rs.setBeforeItemCallback(callback);

        // now restore the PST with callback
        client.restore(pst, rs);
        System.out.println("Success!");
    } catch (AbortRestoreException e) {
        System.out.println("Timeout! " + processedItems.get());
    }
} finally {
    client.dispose();
}
~~~