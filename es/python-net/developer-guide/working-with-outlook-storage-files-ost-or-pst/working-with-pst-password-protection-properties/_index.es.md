---
title: "Trabajar con propiedades de protección de contraseña PST"
url: /es/python-net/working-with-pst-password-protection-properties/
weight: 110
type: docs
---


Microsoft Outlook permite a los usuarios proteger con contraseña los archivos PST para restringir el acceso a ellos. Aspose.Email puede detectar la protección por contraseña en un archivo PST. Este artículo muestra cómo:

- Comprobar la protección por contraseña de un PST
- Leer archivos PST protegidos por contraseña
- Validar la contraseña en un PST protegido por contraseña
- Agregar/Cambiar/Eliminar la contraseña en archivos PST
## **Comprobar la protección por contraseña**

Para verificar si un archivo PST está protegido con una contraseña, utiliza el método *is_password_protected* de la clase [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) como se muestra en el siguiente ejemplo de código: 

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"El almacenamiento está protegido por contraseña - {pst.store.is_password_protected}")
```

## **Leer archivos PST protegidos por contraseña**

Puedes leer archivos protegidos por contraseña igual que los archivos PST regulares sin protección. El siguiente fragmento de código te permite acceder a cada mensaje individual con la posibilidad de su posterior procesamiento:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

for folder in pst.root_folder.get_sub_folders():
    for msg in folder.enumerate_messages():
    # hacer algo
```
## **Validar la contraseña en un PST protegido por contraseña**

Para comprobar si una contraseña en un archivo PST es válida, Aspose.Email proporciona el método *is_password_valid(password)* de la clase [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class). Toma la cadena de la contraseña como parámetro y devuelve True si la contraseña es correcta y False si es incorrecta.

El siguiente fragmento de código demuestra el uso del método *is_password_valid(password)*.

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.from_file("my.pst")

print(f"La contraseña es válida - {pst.store.is_password_valid('Password1')}")
```

## **Agregar/Cambiar/Eliminar la contraseña en archivos PST**

El método *change_password(password)* de la clase [MessageStore](https://reference.aspose.com/email/python-net/aspose.email.storage.pst/messagestore/#messagestore-class) se utiliza para manipular contraseñas en archivos PST. El siguiente ejemplo de código muestra cómo agregar, cambiar o eliminar una contraseña:

```py
import aspose.email as ae

pst = ae.storage.pst.PersonalStorage.create("SetPasswordOnPST_out.pst", ae.storage.pst.FileFormatVersion.UNICODE)
# Agregar o cambiar la contraseña
password = "Password1"
pst.store.change_password(password)
# Eliminar la contraseña
pst.store.change_password(None)
```