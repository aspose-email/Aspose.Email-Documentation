---
title: Managing Outlook MAPI Tasks in PST Files
ArticleTitle: Managing Outlook MAPI Tasks in PST Files
type: docs
weight: 90
url: /python-net/managing-mapitasks-in-pst/
---


## **Add Outlook MAPI Tasks to PST Files**

[Create New PST File and Add Subfolders](https://docs.aspose.com/email/python-net/create-new-pst-file-and-add-subfolders/) demonstrates how to create a PST file and include subfolders within it. With Aspose.Email you can also add MAPI Tasks to the Tasks subfolder of a PST file that you have created or loaded. The code sample below demonstrates how to create and manage a task using the [MapiTask](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapitask/) class in an environment that supports manipulating personal storage table (PST) files. It defines a task with specific parameters and then saves this task to a PST file under a predefined "Tasks" folder.

1. Create a [MapiTask](https://reference.aspose.com/email/python-net/aspose.email.mapi/mapitask/) object setting the start date to the current date and the due date to three days from now.
1. Set the task properties.
1. Create a PST using the [PersonalStorage.Create()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/personalstorage/#methods) method.
1. Create a pre-defined folder (Tasks) at the root of the PST file by accessing the Root folder and then calling the [add_mapi_message_item()](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/folderinfo/#methods) method.


{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}
