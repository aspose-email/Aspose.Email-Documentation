---
title: Working with IBM Notes
ArticleTitle: Working with IBM Notes
type: docs
weight: 120
url: /java/working-with-ibm-notes/
---


## **About IBM Notes**
IBM Notes is the client and IBM Domino is the server of a collaborative client-server software platform. IBM Notes provides collaboration features like email, calendars, to-do lists, contacts management, etc. The database file used by IBM Notes is saved in the Notes Storage Facility (NSF) format.
## **Read messages from NSF storage file**

{{% alert color="primary" %}} 

Note, the NSF implementation is quite limited.
In general, it is possible to face some problems in the following cases:
 - The file was created by Notes version 7 and higher
 - LZ1 compression is used

{{% /alert %}}

Aspose.Email provides the [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) class to read NSF storage files. The [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) class provides the [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) method which iterates over the messages in the NSF storage file. The following sample code demonstrates the use of the [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) class and the [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) method to read messages from the NSF storage file. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessagesFromNSFStorage-1.java" >}}

{{% alert color="primary" %}} 

Please note that only message reading is implemented. Reading of folders is not supported yet due to lack of specification.

{{% /alert %}}
