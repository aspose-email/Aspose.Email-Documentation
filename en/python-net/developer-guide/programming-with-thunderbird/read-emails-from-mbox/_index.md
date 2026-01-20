---
title: Read Emails from MBOX in Python
ArticleTitle: Reading Messages from Mozilla Thunderbird
type: docs
weight: 10
url: /python-net/read-emails-from-mbox-thunderbird/
---


Mozilla Thunderbird is a popular open-source, cross-platform email client developed by the Mozilla Foundation. It stores emails in its own file structure and manages message indexes and subfolders using proprietary file formats. Aspose.Email can work with Thunderbird mail storage structures. Specifically, the API features the [MboxrdStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragereader/) class which allows developers to read messages from Mozilla Thunderbird mail storage files. This article explains how to read messages from Thunderbird's email storage using Aspose.Email.

## **How to Read Messages from MBOX Files**

To read messages from Thunderbird mail storage, follow these steps:

1. Open the Thunderbird storage file.
2. Create an instance of the [MboxrdStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragereader/) class and pass the file stream to its constructor.
3. Call the [read_next_message()](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragereader/#methods) method to retrieve the first message.
4. Use a while loop with the *read_next_message()* to iterate through all messages.
5. Close all file streams after processing.

The following code snippet demonstrates how to read all messages from a Thunderbird mail storage file:


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-ReadMessagesFromThunderbird-ReadMessagesFromThunderbird.py" >}}

## **Retrieve Email Properties from MBOX Messages**

Aspose.Email provides the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class for reading messages and the [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) class for loading MBOX files. The [MboxMessageInfo](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#mboxmessageinfo-class) class contains various properties to access and display specific message details, including:

- **date**: Retrieves the message date.

- **from_address**: Retrieves the sender's address.

- **subject**: Retrieves the message subject.

- **to**: Retrieves recipient addresses.

- **cc**: Retrieves CC recipient addresses.

- **bcc**: Retrieves BCC recipient addresses.

The following code snippet demonstrates how to extract and display message details from an MBOX file:


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

## **Extract Messages by ID from MBOX Files**

Aspose.Email allows extracting messages from an MBOX file using entry IDs. The following methods and properties facilitate this process:

- [enumerate_message_info()](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods): Iterates through each message in the MBOX file.
- [extract_message()](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods): Extracts each message by its Entry ID.
- [entry_id](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxmessageinfo/#properties): Gets the entry identifier.

The code sample below demonstrates the use of these features to read and extract messages from an MBOX file:

1. Create MBOX reader using the [MboxStorageReader.create_reader()](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#methods) method. Specify the file to be processed and pass [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) to configure loading options.
2. Enumerate messages iterating through each *mbox_message_info* by calling *enumerate_message_info()* on the reader. This gives access to metadata of each email in the MBox file.
3. Extract individual messages. For each message info entry, extract the actual email using *extract_message()* method. Pass the *entry_id* from the *mbox_message_info* and [EmlLoadOptions()](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/) for loading configurations of the email.

```py
import aspose.email as ae

reader = ae.storage.mbox.MboxStorageReader.create_reader("my.mbox", ae.storage.mbox.MboxLoadOptions())

for mbox_message_info in reader.enumerate_message_info():
    eml = reader.extract_message(mbox_message_info.entry_id, ae.EmlLoadOptions())
```

## **Configure Load Options When Reading MBOX Files**

The Aspose.Email [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) class allows you to customize the loading process of MailMessage from EML format. For instance, you can set an option to preserve TNEF attachments while loading an EML file by setting the `preserve_tnef_attachments` property of the [EmlLoadOptions](https://reference.aspose.com/email/python-net/aspose.email/emlloadoptions/#emlloadoptions-class) class.

To read the next email message from an MBOX file with your specified load options, use the `read_next_message` method of the [MboxStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxstoragereader/#mboxstoragereader-class) class. Additionally, you can convert the file to PST format using the `mbox_to_pst` method of the [MailStorageConverter](https://reference.aspose.com/email/python-net/aspose.email.storage/mailstorageconverter/#mailstorageconverter-class) class.

The following code sample demonstrates how to use these methods and properties to manage email storage files, including reading messages from MBOX format, preserving TNEF attachments, and converting messages from MBOX to PST format:

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

## **Set Preferred Text Encoding for Reading MBOX Files**

You can specify text encoding to be used while loading a MBOX file. The `preferred_text_encoding` property of the [MboxLoadOptions](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxloadoptions/#mboxloadoptions-class) class sets an additional option and ensures that a message with the encoded content will be correctly read and processed.

The following code snippet shows how to use this feature in a project:

```py
import aspose.email as ae

load_options = ae.storage.mbox.MboxLoadOptions()
load_options.preferred_text_encoding = 'utf-8'
reader = ae.storage.mbox.MboxrdStorageReader("sample.mbox", load_options)
message = reader.read_next_message()
```


## **Get Total Number of Messages in an MBOX File**

The [MboxrdStorageReader](https://reference.aspose.com/email/python-net/aspose.email.storage.mbox/mboxrdstoragereader/) class provides the capability to read the number of items available in an MBox file. This can be used to develop applications for showing progress of activity while processing such a file.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetNumberOfItemsFromMBox-GetNumberOfItemsFromMBox.py" >}}

## **Get the Size of a Specific Message in MBOX**

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-Thunderbird-GetCurrentMessageSize-GetCurrentMessageSize.py" >}}
