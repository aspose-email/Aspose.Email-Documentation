---
title: Managing Outlook Messages
ArticleTitle: Managing Outlook Messages
type: docs
weight: 30
url: /net/managing-outlook-mesages/
---

## **Save Emails as HTML**

Aspose.Email makes it possible to save email resources with relative paths when exporting messages to HTML format. This feature provides more flexibility in how resources are linked in the output HTML file, making it easier to share and display saved emails on different systems. In order to save resources with relative paths, use [HtmlSaveOptions.UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) property. The default property value is false (resources are saved with absolute paths). When set to true, resources are saved with relative paths.

HTML files with relative paths are more portable and can be viewed correctly regardless of the hosting environment’s file structure. You can choose between absolute and relative paths depending on the requirements. You can define custom paths for resources using the [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) event.

The following code sample demonstrates how to **save an email with default relative path to resources**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```

In this case, resources will be saved in the [html file name]_files folder, in the same path as the .html file and the HTML will reference the resources via relative paths.

The code sample below demonstrates how to **save with absolute path to resources**:

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = false
};

msg.Save(Path.Combine("target_files"), htmlSaveOptions);
```

As in the first case, resources will be saved in the [html file name]_files folder by default, but the HTML will reference resources using absolute paths.

By using the [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) event, you can set custom relative or absolute paths for resources. When customizing paths with the [ResourceHtmlRendering](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/) event handler, and since [UseRelativePathToResources](https://reference.aspose.com/email/net/aspose.email/htmlsaveoptions/userelativepathtoresources/) is set to true, you should assign a relative path to the [PathToResourceFile](https://reference.aspose.com/email/net/aspose.email/resourcehtmlrenderingeventargs/pathtoresourcefile/) property to ensure correct referencing.

The following code sample demonstrates how to **custom relative path using ResourceHtmlRendering Event**

```cs
var msg = MapiMessage.Load(sourceFileName);

var htmlSaveOptions = new HtmlSaveOptions
{
    ResourceRenderingMode = ResourceRenderingMode.SaveToFile,
    UseRelativePathToResources = true
};

htmlSaveOptions.ResourceHtmlRendering += (o, args) =>
{
    if (o is AttachmentBase attachment)
    {
	    // Since UseRelativePathToResources = true, you should assign a relative path to the PathToResourceFile property.
        args.PathToResourceFile = $@"images\{attachment.ContentType.Name}";
    }
};

msg.Save(Path.Combine(targetPath, "A Day in the Park.html"), htmlSaveOptions);
```

## **Convert MSG to MIME Messages**

Aspose.Email API provides the capability of converting MSG files to MIME messages using the [ToMailMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/tomailmessage/#tomailmessage) method.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMSGToMIMEMessage-ConvertMSGToMIMEMessage.cs" >}}

## **Set Timeouts for Message Conversion and Loading**

The following features will enable you to set the timeout in milliseconds for conversion and loading process:

- [MailConversionOptions.Timeout](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeout/#mailconversionoptionstimeout-property) property- Limits the time in milliseconds while converting a message.

- [MailConversionOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/timeoutreached/) - Raised if the time is out while converting to MailMessage.

- [MsgLoadOptions.Timeout](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeout/) - Limits the time in milliseconds while converting a message.

- [MsgLoadOptions.TimeoutReached](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/timeoutreached/) - Raised if the time is out while converting to MailMessage.

The code sample below will show you how to set timeout while converting a message:

```cs
var options = new MailConversionOptions();
// Set the timeout to 5 seconds
options.Timeout = 5000;

options.TimeoutReached += (object sender, EventArgs args) =>
{
    string subj = (sender as MailMessage).Subject;
	 // Set a flag indicating the timeout was reached
    isTimedOut = true;
};

var mailMessage = mapiMessage.ToMailMessage(options);
```

### **MSG to EML Convertion Preserving RTF body**

The convertion of a MSG file to EML preserving RTF body can be done in two ways:

- using [MsgLoadOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/preservertfcontent/) property of the [MsgLoadOptions](https://reference.aspose.com/email/net/aspose.email/msgloadoptions/) class;

- using [MailConversionOptions.PreserveRtfContent](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/preservertfcontent/) property of the [MailConversionOptions](https://reference.aspose.com/email/net/aspose.email.mapi/mailconversionoptions/) class;

Both properties get or set a value indicating whether to keep the rtf body in MailMessage.

The following code snippets show how to convert a MSG file to EML and preserve RTF body:

```cs
var loadOptions = new MsgLoadOptions
{
    PreserveRtfContent = true
};

var eml = MailMessage.Load("my.msg", loadOptions);
```

```cs
var conversionOptions = new MailConversionOptions
{
    PreserveRtfContent = true
};

var msg = MapiMessage.Load("my.msg");

var eml = msg.ToMailMessage(conversionOptions);
```

## **Handling Outlook Template Files (.OFT)**

Outlook templates are very useful when you want to send a similar email message again and again. Instead of preparing the message from scratch each time, first, prepare the message in Outlook and save it as an Outlook Template (OFT). After that, whenever you need to send the message, you can create it from the template, saving time writing the same text in the body or the subject line, setting formatting and so on. Aspose.Email’s [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class can be used to load and read an Outlook template (OFT) file. Once the Outlook template is loaded in an instance of the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class, you can update the sender, recipient, body, subject and other properties. After updating the properties:

- Send the email using the [SmtpClient](https://reference.aspose.com/email/net/aspose.email.clients.smtp/smtpclient/) class or
- Save the message as MSG and do further updates/validation using Microsoft Outlook.

In the code samples below, we:

1. Load the template using the [MailMessage](https://reference.aspose.com/email/net/aspose.email/mailmessage/) class.
1. Update some of the properties.
1. Save the message in MSG format.

The following code snippet shows you how to load the OFT file, updating the message and saving it in MSG format.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ReadAndWritingOutlookTemplateFile-ReadAndWritingOutlookTemplateFile.cs" >}}

### **Save MSG Files as Templates**

The following code snippet shows you how to save the outlook MSG file as a template.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SaveMsgAsTemplate-SaveMsgAsTemplate.cs" >}}

### **Determine MAPI Message Type (OFT or MSG)**

When loading a MapiMessage object from a file, you may need to determine if the loaded message is a template file or a regular email file. By using the [IsTemplate](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/istemplate/) property of the [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/#mapimessage-class) class, you can accurately detect whether an email is a template or not.  This functionality can be valuable when handling and processing various types of email files within applications and systems.

The code example below demonstrates how to determine if a MapiMessage is OFT or MSG: 

```cs
var msg = MapiMessage.Load("message.msg");
var isOft = msg.IsTemplate; // returns false

var msg = MapiMessage.Load("message.oft");
var isOft = msg.IsTemplate; // returns true
```

### **Save MapiMessage or MailMessage in OFT Format**

The [SaveOptions](https://reference.aspose.com/email/net/aspose.email/saveoptions/#saveoptions-class) class allows you to specify additional options when saving a MailMessage or MapiMessage into a particular format.

The following code sample demonstrates how to save a message to OFT format:

```cs
// Save the MailMessage to OFT format
using (var eml = MailMessage.Load("message.eml"))
{
    eml.Save("message.oft", SaveOptions.DefaultOft);
	
	// or alternative way #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);
	
	// or alternative  way #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    eml.Save("message.oft", saveOptions);

}

// Save the MapiMessage to OFT format
using (var msg = MapiMessage.Load("message.msg"))
{
    msg.Save("message.oft", SaveOptions.DefaultOft);
	
	// or alternative way #2
	var saveOptions = new MsgSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
	
	// or alternative  way #3
	saveOptions = SaveOptions.CreateSaveOptions(MailMessageSaveType.OutlookTemplateFormat);
    msg.Save("message.oft", saveOptions);
}
```

## **Managing Digitally Signed Messages**

Aspose.Email implements the complete S/MIME email object algorithm. This gives the API complete power to preserve digital signatures while converting messages between formats.

### **Preserve Signature during EML to MSG Conversion**

Aspose.Email preserves the digital signature when converting from EML to MSG. The following code snippet shows you how to convert from EML to MSG.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertEMLToMSG-ConvertEMLToMSG.cs" >}}

### **Convert S/MIME Messages from MSG to EML**

Aspose.Email preserves the digital signature when converting from MSG to EML as shown in the following code snippet.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-ConvertMIMEMessagesFromMSGToEML-ConvertMIMEMessagesFromMSGToEML.cs" >}}

### **Check Signatures of Secure Emails**

The following features are available to check the signature of MapiMessage objects.

- [SecureEmailManager](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/#secureemailmanager-class) class for checking the signature of secure emails.
- [SmimeResult](https://reference.aspose.com/email/net/aspose.email/smimeresult/#smimeresult-class) class to store the results of the check.
- [SecureEmailManager.CheckSignature(MapiMessage msg)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_3) method.
- [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_4) method.
- [SecureEmailManager.CheckSignature(MapiMessage msg, X509Certificate2 certificateForDecrypt, X509Store store)](https://reference.aspose.com/email/net/aspose.email/secureemailmanager/checksignature/#checksignature_5) method.

The code sample below shows how to implement the features in your project:

```cs
var msg = MapiMessage.Load(fileName, new EmlLoadOptions());
var result = new SecureEmailManager().CheckSignature(msg);

var certFileName = "cert.pfx";
var cert = new X509Certificate2(certFileName, "pass");
var eml = MapiMessage.Load(fileName);
var store = new X509Store();
store.Open(OpenFlags.ReadWrite);
store.Add(cert);
store.Close();

var result = new SecureEmailManager().CheckSignature(eml, cert, store);
```

### **Remove Signatures from MapiMessages**

For better compatibility, the [MapiMessage.RemoveSignature](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/removesignature/) method and [MapiMessage.IsSigned](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/issigned/) property are used to remove a digital signature from a message.

The follwoing code snippet shows how to implement these features into your project:

```cs
var msg = MapiMessage.Load(fileName);

if (msg.IsSigned)
{
    var unsignedMsg = msg.RemoveSignature();
}
```

## **Decrypt MapiMessages with Certificates**

If you have encrypted MAPI messages and need to decrypt them using the private key stored in a certificate, the following features of Aspose.Email can be useful:

- [MapiMessage.IsEncrypted](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/isencrypted/#mapimessageisencrypted-property) - Gets a value indicating whether the message is encrypted.
- [MapiMessage.Decrypt()](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt) - Decrypts this message(method searches the current user and computer My stores for the appropriate certificate and private key).
- [MapiMessage.Decrypt(X509Certificate2 certificate)](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/decrypt/#decrypt_1) - Decrypts this message with certificate.

The following code snippet shows how to work with encrypted MAPI messages: 

```cs
var privateCert = new X509Certificate2(privateCertFile, "password");
var msg = MapiMessage.Load("encrypted.msg");

if (msg.IsEncrypted);
{
    var decryptedMsg = msg.Decrypt(privateCert);
}
```

## **Set Color Categories for MSG Files**

A color category marks an email message for some kind of importance or category. Microsoft Outlook lets users assign color categories to differentiate emails. To handle the color category, use the [FollowUpManager](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/). It contains functions such as [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory), [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory), [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) and [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories).

- [AddCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/addcategory/#addcategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) and the color category string, for example, "Purple Category" or "Red Category" as arguments.
- [RemoveCategory](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/removecategory/#removecategory) takes [MapiMessage](https://reference.aspose.com/email/net/aspose.email.mapi/mapimessage/) and the color category string to be removed from the message.
- [ClearCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/clearcategories/#clearcategories) is used to remove all the color categories from the message.
- [GetCategories](https://reference.aspose.com/email/net/aspose.email.mapi/followupmanager/getcategories/#getcategories) is used to retrieve all the color categories from a particular message.

The following example performs the tasks as given below:

1. Add a color category.
1. Add another color category.
1. Retrieve the list of all categories.
1. Remove all categories.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-SetColorCategories-SetColorCategories.cs" >}}

## **Access Follow Up Information in MSG Files**

Aspose.Email API provides the capability to access the follow-up information from a sent or received message. It can retrieve the Read, Delivery Read Receipt and vote results information from a message file.

### **Retrieve Read and Delivery Receipt Information**

The following code snippet shows you how to retrieve read and delivery receipt information.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-RetrieveReadAndDeliveryReceiptInformation-RetrieveReadAndDeliveryReceiptInformation.cs" >}}

## **Create Forward and Reply Messages**

Aspose.Email API provides the capability of creating and formatting the forward and reply messages. The [ReplyMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/replymessagebuilder/) and [ForwardMessageBuilder](https://reference.aspose.com/email/net/aspose.email.tools/forwardmessagebuilder/) classes of the API are used to create the Reply and Forward messages respectively. A Reply or Forward message can be specified to be created using any of the modes of [OriginalMessageAdditionMode](https://reference.aspose.com/email/net/aspose.email.tools/originalmessageadditionmode/) enum. This enum has the following values:

- **OriginalMessageAdditionMode.None** - The original message is not included in the response message.
- **OriginalMessageAdditionMode.Attachment** - The original message is included as an attachment in the response message
- **OriginalMessageAdditionMode.Textpart** - The original message is included as a text in the body of response message

### **Create Reply Messages**

The following code snippet shows you how to create a reply message.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreatReplyMessage-CreatReplyMessage.cs" >}}

### **Create Forward Messages**

The following code snippet shows you how to create a forward message.

{{< gist "aspose-com-gists" "6e5185a63aec6fd70d83098e82b06a32" "Examples-CSharp-Outlook-CreateForwardMessage-CreatForwardMessage.cs" >}}
