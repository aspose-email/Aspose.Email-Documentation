---
title: "Конвертирование OLM в PST"
url: /ru/net/convert-olm-to-pst/
weight: 120
type: docs
---

[OLM](https://docs.fileformat.com/email/olm/) — это формат файла базы данных, используемый Microsoft Outlook для систем Mac. Файлы OLM хранят электронные письма, данные календаря, данные контактов и настройки приложения. Файл OLM не поддерживается Outlook для Windows. Таким образом, невозможно открыть файл Outlook для Mac (OLM) в Outlook для Windows. Если вы хотите перенести свою почтовую корзину из Outlook для Mac в Outlook для Windows, необходимо конвертировать файл OLM Outlook для Mac в файл формата PST Outlook.

## **Шаги для конвертации файла OLM в PST**

Чтобы конвертировать файл OLM в PST, выполните следующие шаги:

1. Создайте экземпляр класса [OlmStorage](https://reference.aspose.com/email/net/aspose.email.storage.olm/olmstorage/) для открытия исходного OLM.
2. Откройте исходный файл OLM.
3. Создайте новый файл PST с помощью метода [Create](https://reference.aspose.com/email/net/aspose.email.storage.pst/personalstorage/create/#create_4).
4. Создайте метод GetContainerClass для сопоставления класса сообщения с классом папки.
5. Создайте метод AddToPst, который рекурсивно считывает каждую папку и ее сообщения из OLM с помощью метода EnumerateMapiMessages и добавляет их в PST в том же порядке с использованием методов AddSubFolder и AddMessage.

## **Пример кода**

Следующий пример кода показывает, как конвертировать OLM в PST.

**Метод Main**:

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

**Реализация метода GetContainerClass**:

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

**Реализация метода AddToPst**:

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