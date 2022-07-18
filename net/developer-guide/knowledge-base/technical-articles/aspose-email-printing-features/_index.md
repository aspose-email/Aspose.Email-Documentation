---
title: Aspose.Email.Printing Features
type: docs
weight: 150
url: /net/aspose-email-printing-features/
---

## **Printing Features**
The [Aspose.Email.Printing](https://reference.aspose.com/net/email/aspose.email.printing/) namespace provides a rich set of features for printing mail messages to different formats (XPS or TIFF) and configuring page layouts. This article describes them. There are several options for how an email message can be printed from Aspose.Email:

1. Printing the message body only.
1. Printing the message body and headers.
1. Printing an HTML body.
1. Setting the page layout.
1. Auto-fit a TIFF to the printer.
1. Adjust Target DPI for output TIFF.
### **Printing the Message Body**
The following code snippet shows you how to creates a message and prints it without headers first to an XPS file and then to a TIFF file.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageBody-PrintMessageBody.cs" >}}
### **Printing Message Headers and Body**
The following code snippet shows you how to display the headers and print them as well as the message body, change the [FormattingFlags](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags) to [MailInfo](https://reference.aspose.com/net/email/aspose.email.printing/messageformattingflags).



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHeadersAndBody-PrintMessageHeadersAndBody.cs" >}}
### **Printing Message with HTML Body**
Messages with an HTML body can also be printed. The following code snippet shows you how to print a message with HTML Body.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-PrintMessageHTMLBody-PrintMessageHTMLBody.cs" >}}
### **Setting Page Layout for Printing**
[Aspose.Email.Printing.MailPrinter](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter) provides controls for setting the following properties of the page layout:

|**Property**|**Description**|**Default Value**|
| :- | :- | :- |
|[FormattingFlags](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/formattingflags)|Show or hide message details.|None [1]|
|[MarginTop](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/margintop)|Get or set the top margin.|0.5|
|[MarginLeft](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginleft)|Get or set the left margin.|0.5|
|[MarginBottom](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginbottom)|Get or set the bottom margin.|0.5|
|[MarginRight](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/marginright)|Get or set the right margin.|0.5|
|[PageUnit](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageunit)|Get or set measurement units.|Inch [2]|
|[PageHeight](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pageheight)|Get or set the page height.|11.69|
|[PageWidth](https://reference.aspose.com/net/email/aspose.email.printing/mailprinter/properties/pagewidth)|Get or set the page width.|8.27|
- There are two flags: MailInfo and None
- Page units can be one of Inch, Pixel, Point, Cm, or Millimeter.

The code snippet that follows uses arbitrary settings to illustrate how these properties are used. It sets up a page 20 cm high and 8 cm wide, with 2 cm margins.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetPrintPageLayout-SetPrintPageLayout.cs" >}}
### **Auto-fit a TIFF**
[Aspose.Email.Printing](https://reference.aspose.com/net/email/aspose.email.printing/) provides the [MessageFormattingFlags.AutoFitWidth](https://reference.aspose.com/net/email/aspose.email.printing/messageformattingflags) property which allows you to auto-fit the TIFF to the printer. The following code snippet shows you how to use Auto-fit.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-SetAutofitForPrinting-SetAutofitForPrinting.cs" >}}
### **Adjust Target DPI for Output TIFF**
The following code snippet shows you how to use DPI for Output TIFF.



{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Knowledge-Base-AdjustTargetDPIForPrinting-AdjustTargetDPIForPrinting.cs" >}}
