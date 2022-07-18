---
title: Converting Outlook Message File (MSG) to TIFF Image
type: docs
weight: 130
url: /net/converting-outlook-message-file-msg-to-tiff-image/
---


In this article, we show you how to convert an Outlook MSG file to a TIFF image.

1. First, read an MSG file and convert it to MHTML format with Aspose.Email for .NET. Use the [Aspose.Email.MailMessage](https://reference.aspose.com/net/email/aspose.email/mailmessage) class to load the message file.
1. After loading the file, call the [MailMessage.Save()](https://reference.aspose.com/net/email/aspose.email/mailmessage/methods/save/index) method and save it to stream in MHTML format.
1. Use Aspose.Words for .NET to convert the MHTML stream to TIFF. Use the [Aspose.Words.Document](https://reference.aspose.com/net/words/aspose.words/document) class to load the MHTML stream.
1. Finally, call the [Document.Save()](https://reference.aspose.com/net/words/aspose.words/document/methods/save/index) method to save the MHTML document to TIFF.

If the document contains multiple pages a multi-page TIFF file is generated. The code snippets below show how to convert Outlook Message File (MSG) to TIFF Image.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-ConvertMSGToTIFF-ConvertMSGToTIFF.cs" >}}
