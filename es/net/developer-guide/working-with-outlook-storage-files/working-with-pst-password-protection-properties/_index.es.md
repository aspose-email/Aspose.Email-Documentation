---
title: "Trabajando con las propiedades de protección con contraseña de PST"
url: /es/net/working-with-pst-password-protection-properties/
weight: 100
type: docs
---

## **Trabajando con las propiedades de protección con contraseña de PST**

Microsoft Outlook permite a los usuarios proteger los archivos PST con una contraseña para restringir el acceso a ellos. Aspose.Email puede detectar la protección con contraseña en un archivo PST. En realidad, la protección con contraseña solo se implementa en Outlook; los datos no están cifrados en absoluto. Y permite utilizar la API para extraer correos electrónicos sin conocer la contraseña.

{{% alert %}}
**¡Pruébalo!**

Ejecute el [PstPasswordManager](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/PstPasswordManager/PstPasswordManager) proyecto de aplicación simple y experimente las funciones de Aspose.Email para administrar las contraseñas PST.
{{% /alert %}}

### **Lea archivos PST protegidos con contraseña**

Puede leer los archivos protegidos con contraseña de la misma manera que los archivos pst normales desprotegidos.

```csharp
using var pst = PersonalStorage.FromFile(fileName);
foreach (var folder in pst.RootFolder.GetSubFolders())
{
    foreach (var msg in folder.EnumerateMessages())
    {

    }
}
```

## **Compruebe si el archivo PST está protegido con contraseña**

La API proporciona la [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) propiedad. El [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) la propiedad devuelve true si el archivo PST está protegido con contraseña y false si no lo está.

El siguiente fragmento de código demuestra el uso de [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) property.

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"The storage is password protected - {pst.Store.IsPasswordProtected}");
```

## **Validar la contraseña en PST protegido por contraseña**

The [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) El método toma la cadena password como parámetro y devuelve true si la contraseña es correcta y false si es incorrecta.

El siguiente fragmento de código demuestra el uso de [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) method.

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"Password is valid - {pst.Store.IsPasswordValid("Password1")}");
```

## **Añadir/cambiar/eliminar contraseñas en archivos PST**

The [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) Este método se utiliza para añadir, cambiar o eliminar una contraseña.

Para ello, sigue estos pasos:

- Cargue PST desde un archivo o una transmisión.
- Llame al [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) método. Para agregar o cambiar la contraseña, pase una cadena de contraseña como parámetro y, para eliminar la contraseña, pase un valor nulo.

```csharp
using var pst = PersonalStorage.Create("SetPasswordOnPST_out.pst", FileFormatVersion.Unicode);
// Add or change the password
const string password = "Password1";
pst.Store.ChangePassword(password);
// Remove the password
pst.Store.ChangePassword(null);
```
