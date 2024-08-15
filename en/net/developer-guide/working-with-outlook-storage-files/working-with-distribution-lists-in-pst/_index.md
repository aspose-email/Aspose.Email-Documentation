---
title: Working with Distribution Lists
type: docs
weight: 40
url: /net/working-with-distribution-lists-in-pst/
---

It is possible to create a Distribution list using Aspose.Email API that is a collection of multiple contacts. A distribution list can be saved to disc in Outlook MSG format and can be viewed/manipulated by opening it in MS Outlook.

### **Creating and Saving a Distribution List**

The following code snippet shows you how to create and save a distribution list.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cs" >}}

### **Reading a Distribution List from a PST**

The following code snippet shows you how to read a distribution list from a PST.

```cs
using Aspose.Email.Storage.Pst;
using Aspose.Email.Mapi;

// Load the PST file
using (var pst = PersonalStorage.FromFile("your.pst"))
{
    // Get the Contacts folder
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    if (folder != null)
    {
        foreach (var msgInfo in folder.EnumerateMessages())
        {
            // Check if the message has the "IPM.DistList" message class
            if (msgInfo.MessageClass == "IPM.DistList")
            {
                // Extract the distribution list
                var distList = (MapiDistributionList)pst.ExtractMessage(msgInfo).ToMapiMessageItem();
                
                // Now, you can work with the distribution list
                // (e.g., access its members, display its properties, or make modifications)
            }
        }
    }
}
```

### **Update a Distribution List in PST**

The following code snippet shows you how to update a distribution list in PST.

```cs
using Aspose.Email.Mapi;
using Aspose.Email.Storage.Pst;

// Load PST file
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
{
    // Get Contacts folder
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    // Add a new member to each distribution list in PST
    foreach (var msg in folder.EnumerateMessages())
    {
        // Check if the message has the "IPM.DistList" message class
        if (msg.MessageClass == "IPM.DistList")
        {
            var distList = pst.ExtractMessage(msg).ToMapiMessageItem();

            // Create a new member to add
            var member = new MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com");
            distList.Members.Add(member);

            // Update Distribution List in PST
            folder.UpdateMessage(msg.EntryIdString, distList);
        }
    }
}
```
