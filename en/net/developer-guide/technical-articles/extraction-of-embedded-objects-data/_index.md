---
title: Extraction of Embedded Objects data
type: docs
weight: 220
url: /net/extraction-of-embedded-objects-data/
---


Sometimes Embedded OLE data is represented as "oleData.mso" attachment by [MapiAttachment](https://apireference.aspose.com/net/email/aspose.email.mapi/mapiattachment) and needs to be extracted manually. These oleData.mso files are Microsoft Computer Document File (MCDF) format and support for such files is beyond the occupation of Aspose.Email. However, Aspose.Email can be used in combination with other open-source libraries, such as OpenMCDF, for reading the contents of such files for saving to disc. Aspose.Email provides the [InlineAttachmentExtractor](https://apireference.aspose.com/net/email/aspose.email.mapi/inlineattachmentextractor) class to enumerate MSO packages from the binary data of oledata.mso, which can then be used for extraction of contents by Compound Files reading libraries.

If a message body type is HTML (not RTF), and there are OLE objects in a message, the MapiPropertyTag.PR_ATTACH_DATA_OBJ property is absent. In this case, the information about OLE objects is contained in oldedata.mso.
## **Extraction of Embedded Objects**
This article shows how to extract the contents from such a file using Aspose.Email and [OpenMCDF](http://sourceforge.net/projects/openmcdf/). This can be done as follow:

- Enumerate MSO packages from the Binary data of oledata.mso attachment
- for each OLE data, read the CompoundFile
- Read the stream with CONTENTS
- Save the contents to FileStream



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-ExtractEmbeddedObjectdata-ExtractEmbeddedObjectdata.cs" >}}
