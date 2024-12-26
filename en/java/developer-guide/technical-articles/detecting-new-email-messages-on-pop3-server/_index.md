---
title: Detecting New Email Messages on POP3 Server
ArticleTitle: Detecting New Email Messages on POP3 Server
type: docs
weight: 100
url: /java/detecting-new-email-messages-on-pop3-server/
---


With POP3 accounts you can leave messages on the server when downloading and reading them. Leaving emails on the server means that they are available to other applications and individuals, for example, users who access their email from several devices. Or you might want to only download messages that meet some special criteria, for example, messages with a particular subject line. To manage email, you can;

- Read all the messages from the POP3 mail server using Aspose.Email.
- Download the messages to your local database.

The messages don't get deleted but stay on the server. The first time it runs, this process works fine. All the required messages are downloaded to the database. But the second time it runs, the same messages are downloaded because they are still on the email server. This causes duplicate records. To solve this issue, use the [Pop3MessageInfo.UniqueID](https://apireference.aspose.com/email/java/com.aspose.email/Pop3MessageInfo#getUniqueId\(\)) property to check whether a message has already been downloaded. The message's unique ID must be stored in the database: it is the search key for detecting new messages.
## **Detecting New Messages**
To identify new emails from a list of emails on a POP3 server:

1. Connect to the server.
1. Get a list of emails.
1. Connect to the database.
1. Get a list of emails.
1. Compare the lists.
1. Save new emails to the database.

The process is faster when you:

1. Fetch all the unique IDs of messages into a hash table.
1. Search the hash table instead of the database for each email message in a for(…) loop.

Instead of querying the database for each message, requiring many database calls, this method only requires one call. The following code snippet shows you how to detect New Email messages on the POP3 server.



~~~Java
public static void run() {
    try {
        // Connect to the POP3 mail server and check messages.
        Pop3Client pop3Client = new Pop3Client("pop.domain.com", 993, "username", "password");

        // List all the messages
        Pop3MessageInfoCollection msgList = pop3Client.listMessages();
        for (Pop3MessageInfo msgInfo : msgList) {
            // Get the POP3 message's unique ID
            String strUniqueID = msgInfo.getUniqueId();

            // Search your local database or data store on the unique ID. If a match is found, that means it's already downloaded. Otherwise download and save it.
            if (searchPop3MsgInLocalDB(strUniqueID) == true) {
                // The message is already in the database. Nothing to do with this message. Go to next message.
            } else {
                // Save the message
                savePop3MsgInLocalDB(msgInfo);
            }
        }
    } catch (Exception ex) {
        System.err.println(ex);
    }

}

private static void savePop3MsgInLocalDB(Pop3MessageInfo msgInfo) {
    // Open the database connection according to your database. Use public properties (for example msgInfo.Subject) and store in database,
    // for example, " INSERT INTO POP3Mails (UniqueID, Subject) VALUES ('" + msgInfo.UniqueID + "' , '" + msgInfo.Subject + "') and Run the query to store in database.
}

private static boolean searchPop3MsgInLocalDB(String strUniqueID) {
    // Open the database connection according to your database. Use strUniqueID in the search query to find existing records,
    // for example, " SELECT COUNT(*) FROM POP3Mails WHERE UniqueID = '" + strUniqueID + "' Run the query, return true if count == 1. Return false if count == 0.
    return false;
}
~~~
