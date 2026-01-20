---
title: Managing Outlook MAPI Journal Entries in PST Files
ArticleTitle: Managing Outlook MAPI Journal Entries in PST Files
type: docs
weight: 70
url: /python-net/managing-mapijournal-entries-in-pst/
---


## **Add MAPI Journal Entries to PST Files**

[Create a New PST File and Add Subfolders](https://docs.aspose.com/email/python-net/create-new-pst-file-and-add-subfolders/) shows how to create a new PST file and add a subfolder to it. With Aspose.Email you can also create a new MAPI journal entry and add it to a PST file. The code sample below demonstrates how to create a journal entry, set its properties, and store it in a newly created PST file:

1. **Create MAPI Journal Entry**: Instantiate a [MapiJournal](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapijournal/) object with the subject, the body and the type.
2. **Set Journal Timing**: Define the start time of the journal entry as the current datetime using `dt.datetime.now()` and set the end time to one hour later using `dt.datetime.today() + timedelta(hours=1)`.
3. **Create PST File**: Use [PersonalStorage.create](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) to generate a new PST file with the UNICODE format.
4. **Create Journal Folder**: Within the new PST file, create a predefined folder named "Journal" using [create_predefined_folder](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) with the `StandardIpmFolder.JOURNAL` parameter.
5. **Add Journal Entry to Folder**: Add the previously created MAPI journal entry to the "Journal" folder using [add_mapi_message_item](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods).



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-CreateNewMapiJournalAndAddToPST-CreateNewMapiJournalAndAddToPST.py" >}}

## **Add Attachments to MAPI Journal Entries in PST Files**

The code sample below demonstrates how to create and save a MAPI journal item using the Aspose.Email library. The journal entry is related to a phone call and includes attachment files.

1. **Define Directory and Attachments**:
   - `data_dir`: A variable that holds the path to the data directory where files and outputs will be stored.
   - `attach_file_names`: A list containing the full path filenames of the attachments to be added to the journal. 
2. **Create a MapiJournal Object**:
   - A [MapiJournal](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapijournal/) object is created with the title "testJournal". This journal entry is described as a "Phone call" in both the subject and type fields.
   - `journal.start_time` is set to the current time using `datetime.now()`.
   - `journal.end_time` is calculated by adding one hour to the start time using `timedelta(hours=1)`.
3. **Set Companies Involved**:
   - The `journal.companies` attribute is updated with a list of companies involved in this journal entry.
4. **Attach Files to the Journal**:
   - A loop iterates over each file in `attach_file_names`. For each file, it appends the file to the `journal.attachments` by reading the file content in binary mode.
5. **Save the MapiJournal**:
   - Finally, the journal entry is saved as a ".msg" file in the specified data directory.


```py
import os
from datetime import datetime, timedelta
from aspose.email.mapi import MapiJournal

data_dir = "path_to_data_directory"
attach_file_names = [os.path.join(data_dir, "Desert.jpg"), os.path.join(data_dir, "download.png")]

journal = MapiJournal("testJournal", "This is a test journal", "Phone call", "Phone call")
journal.start_time = datetime.now()
journal.end_time = journal.start_time + timedelta(hours=1)
journal.companies = ["company 1", "company 2", "company 3"]

for attach in attach_file_names:
    journal.attachments.append(attach, open(attach, 'rb').read())

journal.save(os.path.join(data_dir, "AddAttachmentsToMapiJournal_out.msg"))
```
