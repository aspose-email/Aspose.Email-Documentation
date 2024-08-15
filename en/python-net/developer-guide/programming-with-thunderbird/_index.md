---
title: Programming with Thunderbird
type: docs
weight: 80
url: /python-net/programming-with-thunderbird/
---


## **Reading Messages**
Mozilla Thunderbird is an open source, cross-platform email client, developed by the Mozilla Foundation. It stores emails in its own file structure, managing messages indices and subfolders through proprietary file formats. Aspose.Email can work with Thunderbird mail storage structures. The MboxrdStorageReader class lets developers read messages from Mozilla Thunderbird’s mail storage file. This article shows how to read the messages from Thunderbird email storage:

1. Open the Thunderbird’s storage file
1. Create an instance of the MboxrdStorageReader class and pass the above stream to the constructor.
1. Call read_next_message() to get the first message.
1. Use the same read_next_message() in a while loop to read all the messages.
1. Close all the streams.

The following code snippet shows you how to read all the messages from a Thunderbird mail storage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

### **Retrieving message properties**

In order to read and retrieve information from an Mbox file, Aspose.Email provides the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class to create a reader object for the Mbox file and the [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) class to load the file. The following properties of the [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class can be used to access and display specific message details:

- 'date' - Gets the date of the message.
- 'from_address' - Gets the from address.
- 'subject' - Gets the message subject.
- 'to' - Gets the address collection that contains the recipients of the message.
- 'cc' - Gets the address collection that contains CC recipients.
- 'bcc' - Gets the address collection that contains BCC recipients of the message.

The following code sample demonstrates the use of these properties to read and extract message information from an Mbox file: 

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader(file_name, ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    print(f"Subject: {mbox_message_info.subject}")
    print(f"Date: {mbox_message_info.date}")
    print(f"From: {mbox_message_info.from_address}")
    print(f"To: {mbox_message_info.to}")
    print(f"CC: {mbox_message_info.cc}")
    print(f"Bcc: {mbox_message_info.bcc}")
```
### **Extract Messages from MBOX by Identifiers**

In order to read messages from an MBOX file, Aspose.Email provides the 'create_reader()' method of the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class to create a reader object for the file. It takes the file name and [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) as arguments, allowing the user to load the MBOX file with specific options if needed.

In order to extract messages, the following methods and properties are used:

- 'enumerate_message_info()' method of the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class - Iterates through each message in the MBOX file.
- 'extract_message()" method of the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class - Extracts each message by its Entry ID.
- 'entry_id' property of the [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class - Gets the entry identifier.

Finally, the message is converted into an EML format using [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class).

The code sample below demonstrates the use of these features to read and extract messages from an MBOX file:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())

```
### **Configuring the load options when reading messages from MBOX**

With Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) class, you can specify additional options when loading MailMessage from Eml format. As an example, you can set an option to preserve TNEF attachments while loading an EML file with the 'preserve_tnef_attachments' property of the [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) class.

You can read the next email message from the mbox file using the specified load options with the 'read_next_message' method of the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class and convert the file to PST format with the 'mbox_to_pst' method of the [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class) class .

The code sample below demonstrates the use of these methods and properties to work with email storage files, including reading messages from mbox format, preserving TNEF attachments, and converting messages from mbox to pst format:

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxrdStorageReader(fileName, ae.storage.mbox.MboxLoadOptions())
# Read messages preserving tnef attachments.
load_options = ae.EmlLoadOptions()
load_options.preserve_tnef_attachments = True
eml = reader.read_next_message(load_options)
ae.storage.MailStorageConverter.MboxMessageOptions(load_options)
# Convert messages from mbox to pst preserving tnef attachments.
pst = ae.storage.MailStorageConverter.mbox_to_pst("Input.mbox", "Output.pst")
```
### **Setting Preferred Text Encoding when Loading Mbox Files for Reading**

You can specify text encoding to be used while loading a MBOX file. The 'preferred_text_encoding' property available for the [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) class sets an additional option and ensures that a message with the encoded content will be correctly read and processed.

The following code snippet shows how to use this feature in a project:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```
### **Converting MBOX to PST Preserving or Removing a Signature**

To remove the signature from a file during the process of conversion, set the MboxToPstConversionOptions.remove_signature property to true.

The following code sample shows how to utilize this property:
```py
import aspose.email as ae

personalStorage = ae.storage.pst.PersonalStorage.create("target.pst", ae.storage.pst.FileFormatVersion.UNICODE)
conversion_options = ae.storage.MboxToPstConversionOptions()
conversion_options.remove_signature = True
ae.storage.MailStorageConverter.mbox_to_pst( ae.storage.mbox.MboxrdStorageReader("source.mbox", ae.storage.mbox.MboxLoadOptions()), personalStorage, "Inbox", conversion_options)
```

## **Writing Messages**
The MboxrdStorageWriter class provides the facility to write new messages to Thunderbird’s mail storage file. To write messages:

1. Open the Thunderbird storage file in FileStream.
1. Create an instance of the MboxrdStorageWriter class and pass the above stream to the constructor.
1. Prepare a new message using the MailMessage class.
1. Call the write_message() method and pass the above MailMessage instance to add the message to Thunderbird storage.
1. Close all streams.

The following code snippet shows you how to writes messages to Thunderbird’s mail storage.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-CreateNewMessagesToThunderbird-CreateNewMessagesToThunderbird.py" >}}
## **Getting Total Number of Messages from MBox File**
The MboxrdStorageReader class provides the capability to read the number of items available in an MBox file. This can be used to develop applications for showing progress of activity while processing such a file.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}
## **Get Current Message Size**
{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}
