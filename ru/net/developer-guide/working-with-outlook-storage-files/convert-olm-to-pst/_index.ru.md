---
title: "Конвертировать OLM в PST"
url: /ru/net/convert-olm-to-pst/
weight: 120
type: docs
---

[OLM](https://docs.fileformat.com/email/olm/) это формат файла базы данных, используемый системами Microsoft Outlook для Mac. В файлах OLM хранятся сообщения электронной почты, данные календаря, контактные данные и настройки приложения. Файл OLM не поддерживается Outlook для Windows. Таким образом, невозможно открыть файл Outlook для Mac (OLM) в Outlook для Windows. Если вы хотите перенести почтовый ящик из Outlook для Mac в Outlook для Windows, необходимо преобразовать файл Outlook для Mac OLM в формат файла Outlook PST.

## **Шаги по преобразованию файла OLM в PST**

Чтобы преобразовать файл OLM в PST, выполните следующие действия:

1. Создайте экземпляр [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) класс для OLM с открытым исходным кодом.
2. Откройте исходный файл OLM.
3. Создайте новый файл PST, используя [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4) method.
4. Создайте метод getContainerClass для сопоставления класса сообщений с классом папок.
5. Создайте метод AddTopST, который рекурсивно считывает каждую папку и сообщения из OLM с помощью метода EnumerateMapiMessages и добавляет их в PST в том же порядке с помощью методов AddSubFolder и AddMessage.

## **Пример кода**

В следующем примере кода показано, как преобразовать OLM в PST.

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

**GetContainerClass** реализация метода:

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

**AddToPst** реализация метода:

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
