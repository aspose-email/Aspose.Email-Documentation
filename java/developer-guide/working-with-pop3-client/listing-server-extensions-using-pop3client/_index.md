---
title: Listing Server Extensions using Pop3Client
type: docs
weight: 30
url: /java/listing-server-extensions-using-pop3client/
---


Aspose.Email's [Pop3Client](https://reference.aspose.com/email/java/com.aspose.email/pop3client) lets you retrieve the server extensions that a server supports such as IDLE, UNSELECT, QUOTA, etc. This helps in identifying the availability of an extension before using the client for that particular functionality. The [getCapabilities()](https://reference.aspose.com/email/java/com.aspose.email/EmailClient#getCapabilities\(\)) method returns the supported extension types in the form of a string array.
## **Retrieving Server Extensions**
The following code sample demonstrates retrieving server extensions using Pop3Client for Gmail server.


~~~Java
// For complete examples and data files, please go to https://github.com/aspose-email/Aspose.Email-for-Java

// Connect and log in to POP3
Pop3Client client = new Pop3Client("pop.gmail.com", "username", "password");
client.setSecurityOptions(SecurityOptions.Auto);
client.setPort(995);
String[] getCaps = client.getCapabilities();
for (String item : getCaps) {
    System.out.println(item);
}
~~~
