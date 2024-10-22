---
title: "Trabajando con propiedades de protección de contraseña PST"
url: /es/net/working-with-pst-password-protection-properties/
weight: 100
type: docs
---

## **Trabajando con propiedades de protección de contraseña PST**

Microsoft Outlook permite a los usuarios proteger archivos PST con una contraseña para restringir el acceso a ellos. Aspose.Email puede detectar la protección por contraseña en un archivo PST. La protección por contraseña se implementa en realidad solo en Outlook; los datos no están cifrados en absoluto. Y esto hace posible usar la API para extraer correos electrónicos sin conocer la contraseña.

{{% alert %}}
**¡Pruébalo!**

Ejecuta el proyecto de aplicación simple [PstPasswordManager](https://github.com/aspose-email/Aspose.Email-for-.NET/tree/master/Sample%20Apps/PstPasswordManager/PstPasswordManager) y experimenta las características de Aspose.Email para gestionar contraseñas de PST.
{{% /alert %}}

### **Leer archivos PST protegidos por contraseña**

Puedes leer archivos protegidos por contraseña de la misma manera que los archivos PST no protegidos.

```csharp
using var pst = PersonalStorage.FromFile(fileName);
foreach (var folder in pst.RootFolder.GetSubFolders())
{
    foreach (var msg in folder.EnumerateMessages())
    {

    }
}
```

## **Verificar si el archivo PST está protegido por contraseña**

La API proporciona la propiedad [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/). La propiedad [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/) devuelve true si el archivo PST está protegido por contraseña y false si no lo está.

El siguiente fragmento de código demuestra el uso de la propiedad [PersonalStorage.Store.IsPasswordProtected](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordprotected/).

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"El almacenamiento está protegido por contraseña - {pst.Store.IsPasswordProtected}");
```

## **Validar la contraseña en un PST protegido por contraseña**

El método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid) toma la cadena de la contraseña como parámetro y devuelve true si la contraseña es correcta y false si es incorrecta.

El siguiente fragmento de código demuestra el uso del método [PersonalStorage.Store.IsPasswordValid()](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/ispasswordvalid/#ispasswordvalid).

```csharp
using var pst = PersonalStorage.FromFile("passwordprotectedPST.pst");
Console.WriteLine($"La contraseña es válida - {pst.Store.IsPasswordValid("Password1")}");
```

## **Agregar/Cambiar/Eliminar la contraseña en archivos PST**

El método [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/) se utiliza para agregar, cambiar o eliminar una contraseña.

Para hacerlo, sigue estos pasos:

- Carga el PST desde un archivo o un flujo.
- Llama al método [PersonalStorage.Store.ChangePassword](https://reference.aspose.com/email/net/aspose.email.storage.pst/messagestore/changepassword/). Para agregar o cambiar la contraseña, pasa una cadena de contraseña como parámetro, y para eliminar la contraseña, pasa un valor nulo.

```csharp
using var pst = PersonalStorage.Create("SetPasswordOnPST_out.pst", FileFormatVersion.Unicode);
// Agregar o cambiar la contraseña
const string password = "Password1";
pst.Store.ChangePassword(password);
// Eliminar la contraseña
pst.Store.ChangePassword(null);
```