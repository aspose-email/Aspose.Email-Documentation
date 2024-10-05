---
title: "Работа с Распределительными Списками"
url: /ru/net/working-with-distribution-lists-in-pst/
weight: 40
type: docs
---

Возможность создания распределительного списка с использованием Aspose.Email API, который является коллекцией нескольких контактов. Распределительный список может быть сохранен на диске в формате Outlook MSG и может быть просмотрен/изменен, открыв его в MS Outlook.

### **Создание и Сохранение Распределительного Списка**

Следующий фрагмент кода показывает, как создать и сохранить распределительный список.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-CreateDistributionListInPST-CreateDistributionListInPST.cs" >}}

### **Чтение Распределительного Списка из PST**

Следующий фрагмент кода показывает, как прочитать распределительный список из PST.

```cs
using Aspose.Email.Storage.Pst;
using Aspose.Email.Mapi;

// Загрузка файла PST
using (var pst = PersonalStorage.FromFile("your.pst"))
{
    // Получить папку Контактов
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    if (folder != null)
    {
        foreach (var msgInfo in folder.EnumerateMessages())
        {
            // Проверить, имеет ли сообщение класс сообщения "IPM.DistList"
            if (msgInfo.MessageClass == "IPM.DistList")
            {
                // Извлечь распределительный список
                var distList = (MapiDistributionList)pst.ExtractMessage(msgInfo).ToMapiMessageItem();
                
                // Теперь вы можете работать с распределительным списком
                // (например, получать доступ к его членам, отображать его свойства или вносить изменения)
            }
        }
    }
}
```

### **Обновление Распределительного Списка в PST**

Следующий фрагмент кода показывает, как обновить распределительный список в PST.

```cs
using Aspose.Email.Mapi;
using Aspose.Email.Storage.Pst;

// Загрузка файла PST
using (PersonalStorage pst = PersonalStorage.FromFile("my.pst"))
{
    // Получить папку Контактов
    var folder = pst.GetPredefinedFolder(StandardIpmFolder.Contacts);

    // Добавить нового члена в каждый распределительный список в PST
    foreach (var msg in folder.EnumerateMessages())
    {
        // Проверить, имеет ли сообщение класс сообщения "IPM.DistList"
        if (msg.MessageClass == "IPM.DistList")
        {
            var distList = pst.ExtractMessage(msg).ToMapiMessageItem();

            // Создать нового члена для добавления
            var member = new MapiDistributionListMember("Эдвард Р. Мануэль", "EdwardRManuel@example.com");
            distList.Members.Add(member);

            // Обновить распределительный список в PST
            folder.UpdateMessage(msg.EntryIdString, distList);
        }
    }
}
```