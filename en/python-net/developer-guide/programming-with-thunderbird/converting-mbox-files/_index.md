---
title: Convert MBOX to PST with Aspose.Email for Python via .NET
ArticleTitle: Convert MBOX to PST
type: docs
weight: 40
url: /python-net/convert-mbox-to-pst-python/
---


## **Convert MBOX to PST while Preserving or Removing a Signature**

When converting MBOX files to PST format, you may want to exclude digital signatures from the messages for cleaner output or compatibility purposes. Aspose.Email provides a convenient option to remove these signatures during the conversion process by using the `remove_signature` property of the [MboxToPstConversionOptions](https://reference.aspose.com/email/python-net/aspose.email.storage/mboxtopstconversionoptions/) class.

The example below demonstrates how to enable this option in your Python project:


```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```


