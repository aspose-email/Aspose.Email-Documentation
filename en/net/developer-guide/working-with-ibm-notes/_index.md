---
title: Working with IBM Notes
type: docs
weight: 130
url: /net/working-with-ibm-notes/
---


## **About IBM Notes**

IBM Notes is a client and IBM Domino is a server of a collaborative client-server software platform. IBM Notes provides collaboration features like email, calendars, to-do lists, contacts management, etc. The database file used by IBM Notes is saved in the Notes Storage Facility (NSF) format.

## **Detect a File is in NSF Format**

The code sample below will show you how to recognize the NSF file format:

```cs
var formatType = FileFormatUtil.DetectFileFormat("storage.nsf").FileFormatType; // Returns FileFormatType.Nsf
```

## **Read messages from NSF storage file**

{{% alert color="primary" %}}

Note, the NSF implementation is quite limited.
In general, it is possible to face some problems in the following cases:

1. The file was created by Notes version 7 and higher
  
2. LZ1 compression is used

{{% /alert %}}

Aspose.Email provides the [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) class to read NSF storage files. The [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) class provides the [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) method which iterates over the messages in the NSF storage file. The following sample code demonstrates the use of the [NotesStorageFacility](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/) class and the [EnumerateMessages](https://reference.aspose.com/email/net/aspose.email.storage.nsf/notesstoragefacility/enumeratemessages/#enumeratemessages) method to read messages from the NSF storage file. 

{{< gist "aspose-com-gists" "522d47278b8ca448dc1d7eb97193322c" "Examples-CSharp-Email-ReadMessagesFromNSFStorage-1.cs" >}}

{{% alert color="primary" %}} 

Please note that only message reading is implemented. Reading of folders is not supported yet due to lack of specification.

{{% /alert %}}
