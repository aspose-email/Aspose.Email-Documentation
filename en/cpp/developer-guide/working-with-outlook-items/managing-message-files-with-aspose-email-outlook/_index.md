---
title: Managing Outlook Message Files with C++ Email Parser API
linktitle: Managing Message Files with Aspose.Email.Outlook
type: docs
weight: 30
url: /cpp/managing-message-files-with-aspose-email-outlook/
description: C++ Email Parser Library API is useful in reading, writing outlook template OFT file, managing digitally signed messages, setting color category and accessing delivery receipt information.
---

## **Reading and Writing Outlook Template File (.OFT)**
Outlook templates are very useful when you want to send a similar email message again and again. Instead of preparing the message from scratch each time, first prepare the message in Outlook and save it as an Outlook template (OFT). After that, whenever you need to send the message, you can create it from the template, saving time writing the same text in the body or the subject line, setting formatting and so on. Aspose.Email’s MailMessage class can be used to load and read an Outlook template (OFT) file. Once the Outlook template is loaded in an instance of the MailMessage class, you can update the sender, recipient, body, subject and other properties. After updating the properties:

- Send the email using the SmtpClient class or
- Save the message as MSG and do further updates/validation using Microsoft Outlook.

In the code samples below, we:

1. Load the template using the MailMessage class.
1. Update some of the properties.
1. Save the message in MSG format.

The following code snippet shows you how to load the OFT file with C++ Email Parser Library API, updating the message and saving it in MSG format.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cpp" >}}

## **Managing Digitally Signed Messages**
Aspose.Email implements the complete S/MIME email object algorithm. This gives the API complete power to preserve digital signatures while converting messages between formats.

### **Preserving Signature when Converting from EML to MSG**
When converting from EML to MSG, set the preserveSignature flag to true to preserve a signature. The following code snippet shows you how to converting from EML to MSG.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cpp" >}}

### **Converting S/MIME Messages from MSG to EML**
Aspose.Email preserves the digital signature when converting from MSG to EML as shown in the following code snippet.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cpp" >}}

## **Setting Color Category for Outlook MSG Files**
A color category marks an email message for some kind of importance or category. Microsoft Outlook lets users assign color categories to differentiate emails. To handle the color category, use the FollowUpManager. It contains functions such as AddCategory, RemoveCategory, ClearCategories and GetCategories.

- AddCategory takes MapiMessage and the color category string, for example "Purple Category" or "Red Category" as arguments.
- RemoveCategory takes MapiMessage and the color category string to be removed from the message.
- ClearCategories() is used to remove all the color categories from the message.
- GetCategories is used to retrieve all the color categories from a particular message.

The following example performs the tasks as given below:

1. Add a color category.
1. Add another color category.
1. Retrieve the list of all categories.
1. Remove all categories.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-SetColorCategories-SetColorCategories.cpp" >}}

## **Accessing Follow Up Information form MSG file**
Aspose.Email API provides the capability to access the follow up information from a sent or received message. It can retrieve the Read, Delivery Read Receipt and vote results information from a message file.

### **Retrieving Read and Delivery Receipt Information**
The following code snippet shows you how to retrieve read and delivery receipt information.

{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cpp" >}}
