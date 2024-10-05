---
title: Работа с свойствами защиты паролем PST
type: docs
weight: 100
url: /net/working-with-pst-password-protection-properties/
---

## **Работа с свойствами защиты паролем PST**

Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаружить защиту паролем в файле PST. На самом деле защита паролем реализована только в Outlook; данные вообще не шифруются. И это позволяет использовать API для извлечения электронных писем без знания пароля.

{{% alert %}}
**Попробуйте это!**

Запустите проект простого приложения [PstPasswordManager](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/PstPasswordManager/PstPasswordManager) и испробуйте возможности Aspose.Email для управления паролями PST.
{{% /alert %}}

### **Чтение файлов PST с защитой паролем**

Вы можете читать файлы с защитой паролем так же, как и обычные незащищенные файлы PST.

```csharp
using var pst = PersonalStorage.FromFile(fileName);
foreach (var folder in pst.RootFolder.GetSubFolders())
{
    foreach (var msg in folder.EnumerateMessages())
    {

    }
}
```

## **Проверка, защищён ли файл PST паролем**

API предоставляет свойство [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/). Свойство [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) возвращает true, если файл PST защищён паролем, и false, если нет.

Следующий кодовый фрагмент демонстрирует использование свойства [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/).

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"Хранилище защищено паролем - {pst.Store.IsPasswordProtected}");
```

## **Проверка пароля в защищенном паролем PST**

Метод [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) принимает строку пароля в качестве параметра и возвращает true, если пароль верен, и false, если он неверен.

Следующий кодовый фрагмент демонстрирует использование метода [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid).

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"Пароль верный - {pst.Store.IsPasswordValid("Password1")}");
```

## **Добавление/изменение/удаление пароля для файлов PST**

Метод [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) используется для добавления, изменения или удаления пароля.

Для этого выполните следующие шаги:

- Загрузите PST из файла или потока.
- Вызовите метод [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/). Чтобы добавить или изменить пароль, передайте строку пароля в качестве параметра, а чтобы удалить пароль, передайте значение null.

```csharp
using var pst = PersonalStorage.Create("SetPasswordOnPST_out.pst", FileFormatVersion.Unicode);
// Добавить или изменить пароль
const string password = "Password1";
pst.Store.ChangePassword(password);
// Удалить пароль
pst.Store.ChangePassword(null);
```