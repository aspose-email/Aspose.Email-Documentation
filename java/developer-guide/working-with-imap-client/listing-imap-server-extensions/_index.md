---
title: Listing IMAP Server Extensions
type: docs
weight: 80
url: /java/listing-imap-server-extensions/
---


Aspose.Email's [ImapClient](https://reference.aspose.com/email/java/com.aspose.email/ImapClient) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/EmailClient#getCapabilities\(\)) method returns the supported extension types in the form of a string array. The following code snippet shows you how to retrieve extensions.



~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java
// Connect and log in to IMAP
ImapClient client = new ImapClient("imap.gmail.com", "username", "password");
String[] getCapabilities = client.getCapabilities();
for (String getCap : getCapabilities) {
    System.out.println(getCap);
}
~~~
