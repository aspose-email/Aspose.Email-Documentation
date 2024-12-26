---
title: Working with PST Password Protection 
ArticleTitle: Working with PST Password Protection 
type: docs
weight: 70
url: /net/working-with-pst-password-protection/
---

## **Working with PST Password Protection**

Microsoft Outlook lets users to protect PST files with a password to restrict access to them. Aspose.Email can detect password protection on a PST file. The password protection is actually only implemented in Outlook; the data are not encrypted at all. And it makes it possible to use the API to extract emails without knowing the password.

{{% alert %}}
**Try it out!**

Run the [PstPasswordManager](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/PstPasswordManager/PstPasswordManager) simple app project, and experience Aspose.Email's features for managing PST passwords.
{{% /alert %}}

### **Read Password Protected PST Files**

You can read password-protected files just like regular unprotected pst files.

```csharp
using var pst = PersonalStorage.FromFile(fileName);
foreach (var folder in pst.RootFolder.GetSubFolders())
{
    foreach (var msg in folder.EnumerateMessages())
    {

    }
}
```

## **Check if PST is Password Protected**

The API provides the [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) property. The [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) property returns true if the PST file is password protected and false if it is not.

The following code snippet demonstrates the use of [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) property.

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"The storage is password protected - {pst.Store.IsPasswordProtected}");
```

## **Validate Password**

The [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) method takes the string password as a parameter and returns true if the password is correct and false if it is incorrect.

The following code snippet demonstrates the use of [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) method.

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"Password is valid - {pst.Store.IsPasswordValid("Password1")}");
```

## **Add/Change/Remove Passwords**

The [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) method is used to add, change or delete a password.

To do this, follow these steps:

- Load PST from a file or a stream.
- Call the [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) method. To add or change the password, pass a password string as a parameter, and to remove the password, pass null value.

```csharp
using var pst = PersonalStorage.Create("SetPasswordOnPST_out.pst", FileFormatVersion.Unicode);
// Add or change the password
const string password = "Password1";
pst.Store.ChangePassword(password);
// Remove the password
pst.Store.ChangePassword(null);
```
