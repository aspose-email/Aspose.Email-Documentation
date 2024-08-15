---
title: "Trabajando con las propiedades de protección con contraseña de PST"
url: /es/python-net/working-with-pst-password-protection-properties/
weight: 110
type: docs
---


Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección con contraseña en un archivo PST. Este artículo muestra cómo:

- Compruebe la protección con contraseña de un PST
- Lea archivos PST protegidos con contraseña
- Validar la contraseña en PST protegido por contraseña
- Añadir/cambiar/eliminar la contraseña en los archivos PST
## **Compruebe la protección con contraseña**

Para comprobar si un archivo PST está protegido con una contraseña, utilice *is_password_protected* método del [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) clase como se muestra en el ejemplo de código siguiente:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"The storage is password protected - {pst.store.is_password_protected}")
```

## **Lea archivos PST protegidos con contraseña**

Puede leer los archivos protegidos con contraseña de la misma manera que los archivos pst normales desprotegidos. El siguiente fragmento de código le permite acceder a cada mensaje individual con la posibilidad de procesarlo posteriormente:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

for folder in pst.root_folder.get_sub_folders():
    for msg in folder.enumerate_messages():
    # do something
```
## **Validar la contraseña en PST protegido por contraseña**

Para comprobar si una contraseña de un archivo PST es válida, Aspose.Email proporciona la *is_password_valid(password)* método del [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) clase. Toma la contraseña de la cadena como parámetro y devuelve True si la contraseña es correcta y False si es incorrecta.

El siguiente fragmento de código demuestra el uso de *is_password_valid(password)* method.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"Password is valid - {pst.store.is_password_valid('Password1')}")
```

## **Añadir/cambiar/eliminar la contraseña en los archivos PST**

The *change_password(password)* método del [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) La clase se usa para manipular contraseñas en archivos PST. El siguiente ejemplo de código muestra cómo agregar, cambiar o eliminar una contraseña:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.create("SetPasswordOnPST_out.pst", ae.storage.pst.FileFormatVersion.UNICODE)
# Add or change the password
password = "Password1"
pst.store.change_password(password)
# Remove the password
pst.store.change_password(None)
```
