---
title: "Crear Nuevo PST en Python"
url: /es/java/create-new-pst-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Crear Nuevo PST**
Para crear un nuevo PST usando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código en Python**

``` python



\# Crear una instancia de PersonalStorage

personalStorage = self.PersonalStorage

pst = personalStorage.create(self.dataDir + "sample1.pst", 0)

\# Crear una carpeta en la raíz del pst

pst.getRootFolder().addSubFolder("myInbox")

\# Agregar mensaje a la carpeta recién creada

mapi_message = self.MapiMessage

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(self.dataDir + "Message.msg"))

print "PST creado exitosamente."

```
## **Descargar Código en Ejecución**
Descarga **Crear Nuevo PST (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)