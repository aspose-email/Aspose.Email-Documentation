---
title: Working with MapiTask in PST
type: docs
weight: 90
url: /cpp/working-with-mapitask-in-pst/
---

## **Adding MapiTask to PST**
With Aspose.Email you can add MapiTask to the Tasks subfolder of a PST file that you have created or loaded. Below are the steps to add MapiTask to a PST:

1. Create a MapiTask object.
1. Set the MapiTask properties using constructor and different methods.
1. Create a PST using the PersonalStorage.Create() method.
1. Create a pre-defined folder (Tasks) at the root of the PST file by accessing the Root folder and then calling the AddMapiMessageItem() method.

The following code snippet shows you how to create a MapiTask and then add it to the tasks folder of a newly created PST file.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-AddMapiTaskToPST-AddMapiTaskToPST.cpp" >}}
