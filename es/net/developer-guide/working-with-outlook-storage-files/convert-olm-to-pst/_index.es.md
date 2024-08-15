---
title: "Convertir OLM a PST"
url: /es/net/convert-olm-to-pst/
weight: 120
type: docs
---

[OLM](https://docs.fileformat.com/email/olm/) es un formato de archivo de base de datos utilizado por Microsoft Outlook para sistemas Mac. Los archivos OLM almacenan los mensajes de correo electrónico, los datos del calendario, los datos de contacto y la configuración de las aplicaciones. Outlook para Windows no admite ningún archivo OLM. Por lo tanto, no es posible abrir un archivo de Outlook para Mac (OLM) en Outlook para Windows. Si desea migrar su buzón de Outlook para Mac a Outlook para Windows, es necesario convertir el archivo OLM de Outlook para Mac al formato de archivo PST de Outlook.

## **Pasos para convertir un archivo OLM a PST**

Para convertir un archivo OLM a PST, siga los pasos que se indican a continuación:

1. Crea una instancia de [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) de clase a OLM de código abierto.
2. Abra un archivo OLM de origen.
3. Cree un nuevo archivo PST usando [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Cree un método getContainerClass para asignar la clase de mensaje a una clase de carpeta.
5. Cree un método AddToPST que lea de forma recursiva cada carpeta y sus mensajes desde OLM mediante el método EnumerateMapiMessages y los agregue al PST en el mismo orden mediante los métodos AddSubFolder y AddMessage.

## **Ejemplo de código**

El siguiente ejemplo de código muestra cómo convertir un OLM en un PST.

**Main** method:

```cs
// create an instance of OlmStorage class to open source OLM
using (var olm = new OlmStorage("my.olm"))
// create a new PST file
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    // recursively reads each folder and its messages
    // and adds them to the PST in the same order
    foreach (var olmFolder in olm.FolderHierarchy)
    {
        AddToPst(pst.RootFolder, olmFolder);
    }
}
```

**GetContainerClass** implementación del método:

```cs
public string GetContainerClass(string messageClass)
{
    if (messageClass.StartsWith("IPM.Contact") || messageClass.StartsWith("IPM.DistList"))
    {
        return "IPF.Contact";
    }

    if (messageClass.StartsWith("IPM.StickyNote"))
    {
        return "IPF.StickyNote";
    }

    if (messageClass.StartsWith("IPM.Activity"))
    {
        return "IPF.Journal";
    }

    if (messageClass.StartsWith("IPM.Task"))
    {
        return "IPF.Task";
    }

    if (messageClass.StartsWith("IPM.Appointment") || messageClass.StartsWith("IPM.Schedule.meeting"))
    {
        return "IPF.Appointment";
    }

    return "IPF.Note";
}
```

**AddToPst** implementación del método:

```cs
public void AddToPst(FolderInfo pstFolder, OlmFolder olmFolder)
{
    FolderInfo pstSubFolder = pstFolder.GetSubFolder(olmFolder.Name);

    foreach (var msg in olmFolder.EnumerateMapiMessages())
    {
        if (pstSubFolder == null)
        {
            pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name, GetContainerClass(msg.MessageClass));
        }

        pstSubFolder.AddMessage(msg);
    }

    if (pstSubFolder == null)
    {

        pstSubFolder = pstFolder.AddSubFolder(olmFolder.Name);
    }

    foreach (var olmSubFolder in olmFolder.SubFolders)
    {
        AddToPst(pstSubFolder, olmSubFolder);
    }
}
```
