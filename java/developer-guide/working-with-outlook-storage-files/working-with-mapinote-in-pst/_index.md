---
title: Working with MapiNote in PST
type: docs
weight: 80
url: /java/working-with-mapinote-in-pst/
---

## **Adding MapiNote to PST**
[Create New PST, Add Sub-folders and Messages](/email/java/create-new-pst-add-sub-folders-and-messages/) showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add a MapiNote to the Notes subfolder of a PST file that you have created or loaded.

Below are the steps to add MapiNote to a PST:

1. Create a template MapiNote using Microsoft Outlook and save it as an MSG file.
1. Load saved MSG note into [MapiMessage](https://reference.aspose.com/email/java/com.aspose.email/MapiMessage) object.
1. Create a [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/MapiNote) object and load the template MSG note.
1. Set the [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/MapiNote) properties using different methods.
1. Create a PST using the [PersonalStorage.create()](https://reference.aspose.com/email/java/com.aspose.email/PersonalStorage#create\(java.io.OutputStream,%20int\)) method.
1. Create a pre-defined folder (Notes) at the root of the PST file by accessing the root folder and then calling the [addMapiMessageItem()](https://reference.aspose.com/email/java/com.aspose.email/FolderInfo#addMapiMessageItem\(com.aspose.email.IMapiMessageItem\)) method.

The code snippet below shows how to create a [MapiNote](https://reference.aspose.com/email/java/com.aspose.email/MapiNote) and then add it to the Notes folder of a newly created PST file.

{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-outlook-pst-AddMapiNoteToPST-.java" >}}
