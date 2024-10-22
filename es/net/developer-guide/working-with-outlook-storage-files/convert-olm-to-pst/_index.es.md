---
title: "Convertir OLM a PST"
url: /es/net/convert-olm-to-pst/
weight: 120
type: docs
---

[OLM](https://docs.fileformat.com/email/olm/) es un formato de archivo de base de datos utilizado por Microsoft Outlook para sistemas Mac. Los archivos OLM almacenan mensajes de correo electrónico, datos de calendario, datos de contactos y configuraciones de aplicación. Un archivo OLM no es compatible con Outlook para Windows. Por lo tanto, no es posible abrir un archivo de Outlook para Mac (OLM) en Outlook para Windows. Si desea migrar su buzón de Outlook para Mac a Outlook para Windows, es necesario convertir el archivo OLM de Outlook para Mac al formato de archivo PST de Outlook.

## **Pasos para convertir un archivo OLM a PST**

Para convertir un archivo OLM a PST, siga los pasos que se indican a continuación:

1. Cree una instancia de la clase [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) para abrir el OLM de origen.
2. Abra un archivo OLM de origen.
3. Cree un nuevo archivo PST utilizando el método [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
4. Cree un método GetContainerClass para mapear la clase de mensaje a una clase de carpeta.
5. Cree un método AddToPst que lea recursivamente cada carpeta y sus mensajes del OLM utilizando el método EnumerateMapiMessages y los agregue al PST en el mismo orden utilizando los métodos AddSubFolder y AddMessage.

## **Ejemplo de código**

El siguiente ejemplo de código muestra cómo convertir un OLM a un PST.

**Método** Main:

```cs
// crear una instancia de la clase OlmStorage para abrir el OLM de origen
using (var olm = new OlmStorage("my.olm"))
// crear un nuevo archivo PST
using (var pst = PersonalStorage.Create("my.pst", FileFormatVersion.Unicode))
{
    // lee recursivamente cada carpeta y sus mensajes 
    // y los agrega al PST en el mismo orden
    foreach (var olmFolder in olm.FolderHierarchy)
    {
        AddToPst(pst.RootFolder, olmFolder);
    }
} 
```

**Implementación del método** GetContainerClass:

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

**Implementación del método** AddToPst:

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