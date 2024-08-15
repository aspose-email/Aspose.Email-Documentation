---
title: "Trabajando con listas de distribución"
url: /es/net/working-with-distribution-lists-in-pst/
weight: 40
type: docs
---

Es posible crear una lista de distribución utilizando la API Aspose.Email que es una colección de varios contactos. Una lista de distribución se puede guardar en un disco en formato MSG de Outlook y se puede ver o manipular abriéndola en MS Outlook.

### **Creación y almacenamiento de una lista de distribución**

El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cs" >}}

### **Lectura de una lista de distribución desde un PST**

El siguiente fragmento de código muestra cómo leer una lista de distribución desde un PST.

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

### **Actualizar una lista de distribución en PST**

El siguiente fragmento de código muestra cómo actualizar una lista de distribución en PST.

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
