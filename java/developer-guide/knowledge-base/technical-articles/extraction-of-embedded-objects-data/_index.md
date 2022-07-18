---
title: Extraction of Embedded Objects data
type: docs
weight: 220
url: /java/extraction-of-embedded-objects-data/
---


Sometimes Embedded OLE data is represented as "oleData.mso" attachment by [MapiAttachment](https://reference.aspose.com/email/java/com.aspose.email/MapiAttachment) and needs to be extracted manually. These oleData.mso files are Microsoft Computer Document File (MCDF) format and support for such files is beyond the occupation of Aspose.Email. However, Aspose.Email can be used in combination with other open-source libraries, such as OpenMCDF, for reading the contents of such files for saving to disc. Aspose.Email provides the [InlineAttachmentExtractor](https://reference.aspose.com/email/java/com.aspose.email/InlineAttachmentExtractor) class to enumerate MSO packages from the binary data of oledata.mso, which can then be used for extraction of contents by Compound Files reading libraries.

If a message body type is HTML (not RTF), and there are OLE objects in a message, the MapiPropertyTag.PR_ATTACH_DATA_OBJ property is absent. In this case, the information about OLE objects is contained in oldedata.mso.
## **Extraction of Embedded Objects**
This article shows how to extract the contents from such a file using Aspose.Email:



~~~Java
// The path to the File directory
String dataDir = "/data";

MapiMessage msg = MapiMessage.fromFile(dataDir + "double.msg");
for (MapiAttachment mapiAttachment : msg.getAttachments()) {
    if ("oledata.mso".equals(mapiAttachment.getLongFileName())) {
        IGenericDictionary<String, byte[]> oledata = InlineAttachmentExtractor.enumerateMsoPackage(new ByteArrayInputStream(mapiAttachment.getBinaryData()));

        for (String oleItem : oledata.getKeys()) {
            // Use binary data
            processBynaryData(oledata.get_Item(oleItem));
        }
    }
}
~~~