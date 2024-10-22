---
title: "Trabajando con Listas de Distribución"
url: /es/net/working-with-distribution-lists-in-pst/
weight: 40
type: docs
---

Es posible crear una lista de distribución utilizando la API de Aspose.Email, que es una colección de múltiples contactos. Una lista de distribución se puede guardar en disco en formato MSG de Outlook y se puede ver/manipular abriéndola en MS Outlook.

### **Creando y Guardando una Lista de Distribución**

El siguiente fragmento de código muestra cómo crear y guardar una lista de distribución.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cs" >}}

### **Leyendo una Lista de Distribución desde un PST**

El siguiente fragmento de código muestra cómo leer una lista de distribución desde un PST.

```cs
using Aspose.Email.Storage.Pst;
using Aspose.Email.Mapi;

// Cargar el archivo PST
using (var pst = PersonalStorage.FromFile("your.pst"))
{
    // Obtener la carpeta de Contactos
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    if (folder != null)
    {
        foreach (var msgInfo in folder.EnumerateMessages())
        {
            // Verificar si el mensaje tiene la clase de mensaje "IPM.DistList"
            if (msgInfo.MessageClass == "IPM.DistList")
            {
                // Extraer la lista de distribución
                var distList = (MapiDistributionList)pst.ExtractMessage(msgInfo).ToMapiMessageItem();
                
                // Ahora, puedes trabajar con la lista de distribución
                // (por ejemplo, acceder a sus miembros, mostrar sus propiedades o hacer modificaciones)
            }
        }
    }
}
```

### **Actualizar una Lista de Distribución en PST**

El siguiente fragmento de código muestra cómo actualizar una lista de distribución en PST.

```cs
using Aspose.Email.Mapi;
using Aspose.Email.Storage.Pst;

// Cargar archivo PST
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
{
    // Obtener la carpeta de Contactos
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    // Agregar un nuevo miembro a cada lista de distribución en PST
    foreach (var msg in folder.EnumerateMessages())
    {
        // Verificar si el mensaje tiene la clase de mensaje "IPM.DistList"
        if (msg.MessageClass == "IPM.DistList")
        {
            var distList = pst.ExtractMessage(msg).ToMapiMessageItem();

            // Crear un nuevo miembro para agregar
            var member = new MapiDistributionListMember("Edward R. Manuel", "EdwardRManuel@example.com");
            distList.Members.Add(member);

            // Actualizar la lista de distribución en PST
            folder.UpdateMessage(msg.EntryIdString, distList);
        }
    }
}
```