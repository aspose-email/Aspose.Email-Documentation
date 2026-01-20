---
title: Managing Digital Signatures with Aspose.Email
ArticleTitle: Managing Digital Signatures with Aspose.Email
type: docs
weight: 30
url: /python-net/managing-digital-signatures-in-python/
---

The library provides the [LoadOptions](https://reference.aspose.com/email/python-net/aspose.email/loadoptions/#loadoptions-class) class, an abstract base class that allows the user to specify additional options when loading a [MailMessage](https://reference.aspose.com/email/python-net/aspose.email/mailmessage/) from a particular format. The signature preserving option is set by default.

## **Convert EML to MSG While Preserving Signatures** 

The code sample below demonstrates how to load a message, convert it to MSG format and save as MSG (the signature is preserved by default): 

```python
import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
message = ae.MailMessage.load("Message.eml", loadOptions)
# Save as MSG
message.save("ConvertEMLToMSG_out.msg", ae.SaveOptions.default_msg_unicode)
```

## **Convert S/MIME Messages from MSG to EML**

Aspose.Email allows you to convert from MSG to EML preserving a digital signature as shown in the following code snippet.

```python
import aspose.email as ae

# Load mail message
loadOptions = ae.EmlLoadOptions()
smime_eml = ae.MailMessage.load("smime.eml", loadOptions)

conversion_options = ae.mapi.MapiConversionOptions(ae.mapi.OutlookMessageFormat.UNICODE)
msg = ae.mapi.MapiMessage.from_mail_message(smime_eml, conversion_options)
# Save File to disk
msg.save("ConvertMIMEMessagesFromMSGToEML_out.msg")
```
