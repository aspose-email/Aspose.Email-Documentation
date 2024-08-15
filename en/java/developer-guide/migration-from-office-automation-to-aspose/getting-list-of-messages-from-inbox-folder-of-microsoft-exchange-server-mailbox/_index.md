---
title: Getting List of Messages from Inbox Folder of Microsoft Exchange Server Mailbox
type: docs
weight: 50
url: /java/getting-list-of-messages-from-inbox-folder-of-microsoft-exchange-server-mailbox/
---


{{% alert color="primary" %}} 

Our migration tips show how Aspose products can be used to improve your applications and free you from dependency on traditional automation.

This migration tip connects to a Microsoft Exchange Server mailbox and get a list of messages from the Inbox folder. The code samples below show how to use [Microsoft Office Interop](#using-microsoft-office-interop) to get a list of messages before doing the same thing using classes in the [Aspose.Email Exchange](#using-asposeemail), using Java.

{{% /alert %}} 
## **Using Microsoft Office Interop**
To use Office Automation objects for Microsoft Outlook, add references to Microsoft Office and Microsoft Office Interop for Outlook libraries to the project. Microsoft Office Outlook must also be installed on the machine that the code runs on.
### **Programming Samples**
**C#**

~~~cs

 // Create Application class and get namespace

Outlook.Application outlook = new Outlook.ApplicationClass();

Outlook.NameSpace ns = outlook.GetNamespace("Mapi");

object _missing = Type.Missing;

ns.Logon(_missing, _missing, false, true);

// Get Inbox information in objec of type MAPIFolder

Outlook.MAPIFolder inbox = ns.GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox);

// Unread emails

int unread = inbox.UnReadItemCount;

// Display the subject of emails in the Inbox folder
foreach (Outlook.MailItem mail in inbox.Items)

{

    Console.WriteLine(Wmail.Subject);


}


~~~
## **Using Aspose.Email**
The following code snippets do the same thing as [the snippets above](#using-microsoft-office-interop) but uses Aspose.Email.

However, Microsoft Outlook does not need to be installed on the machine where the code runs. Reference the Aspose.Email to build and run the project successfully.
### **Programming Samples**

~~~java

// Create instance of IEWSClient class by giving credentials
try (IEWSClient client = EWSClient.getEWSClient("https://outlook.office365.com/EWS/Exchange.asmx", "username", "password", "domain")) {
    // Call listMessages method to list messages info from Inbox

    ExchangeMessageInfoCollection msgCollection = client.listMessages(client.getMailboxInfo().getInboxUri());

    // Loop through the collection to display the basic information
    for (ExchangeMessageInfo msgInfo : msgCollection) {
        System.out.println("Subject: " + msgInfo.getSubject());
        System.out.println("From: " + msgInfo.getFrom().toString());
        System.out.println("To: " + msgInfo.getTo().toString());
        System.out.println("Message ID: " + msgInfo.getMessageId());
        System.out.println("Unique URI: " + msgInfo.getUniqueUri());
        System.out.println("==================================");
    }
}

~~~
