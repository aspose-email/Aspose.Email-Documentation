---
title: "Работа со свойствами защиты паролем PST"
url: /ru/net/working-with-pst-password-protection-properties/
weight: 100
type: docs
---

## **Работа со свойствами защиты паролем PST**

Microsoft Outlook позволяет пользователям защищать файлы PST паролем для ограничения доступа к ним. Aspose.Email может обнаруживать защиту паролем в PST-файле. Защита паролем на самом деле реализована только в Outlook; данные вообще не зашифрованы. Кроме того, это позволяет использовать API для извлечения электронных писем без знания пароля.

{{% alert %}}
**Попробуйте!**

Запустите [PstPasswordManager](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/PstPasswordManager/PstPasswordManager) простой проект приложения и попробуйте функции Aspose.Email для управления паролями PST.
{{% /alert %}}

### **Чтение защищенных паролем файлов PST**

Вы можете читать защищенные паролем файлы так же, как обычные незащищенные pst-файлы.

```csharp
using var pst = PersonalStorage.FromFile(fileName);
foreach (var folder in pst.RootFolder.GetSubFolders())
{
    foreach (var msg in folder.EnumerateMessages())
    {

    }
}
```

## **Проверьте, защищен ли PST-файл паролем**

API предоставляет [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) имущество. Это [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) свойство возвращает значение true, если PST-файл защищен паролем, и false, если это не так.

Следующий фрагмент кода демонстрирует использование [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) property.

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"The storage is password protected - {pst.Store.IsPasswordProtected}");
```

## **Подтвердите пароль в защищенном паролем PST**

The [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) метод принимает строковый пароль в качестве параметра и возвращает true, если пароль правильный, и false, если он неверен.

Следующий фрагмент кода демонстрирует использование [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) method.

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"Password is valid - {pst.Store.IsPasswordValid("Password1")}");
```

## **Добавление/изменение/удаление пароля в файлах PST**

The [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) метод используется для добавления, изменения или удаления пароля.

Для этого выполните следующие действия:

- Загрузите PST из файла или потока.
- Позвоните [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) метод. Чтобы добавить или изменить пароль, передайте строку пароля в качестве параметра, а чтобы удалить пароль, передайте нулевое значение.

```csharp
using var pst = PersonalStorage.Create("SetPasswordOnPST_out.pst", FileFormatVersion.Unicode);
// Add or change the password
const string password = "Password1";
pst.Store.ChangePassword(password);
// Remove the password
pst.Store.ChangePassword(null);
```
