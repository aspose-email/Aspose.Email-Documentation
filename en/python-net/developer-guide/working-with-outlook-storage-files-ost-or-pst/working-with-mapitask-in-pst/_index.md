---
title: Working with MapiTask in PST
ArticleTitle: Working with MapiTask in PST
type: docs
weight: 90
url: /python-net/working-with-mapitask-in-pst/
---


## **Adding MapiTask to PST**
Create a New PST File and Add Subfolders showed how to create a PST file and add a subfolder to it. With Aspose.Email you can add MapiTask to the Tasks subfolder of a PST file that you have created or loaded. Below are the steps to add MapiTask to a PST:

1. Create a MapiTask object.
1. Set the MapiTask properties using constructor and different methods.
1. Create a PST using the PersonalStorage.Create() method.
1. Create a pre-defined folder (Tasks) at the root of the PST file by accessing the Root folder and then calling the AddMapiMessageItem() method.

The following code snippet shows you how to create a MapiTask and then add it to the tasks folder of a newly created PST file.



{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookStorageFiles-AddMapiTaskToPST-AddMapiTaskToPST.py" >}}
