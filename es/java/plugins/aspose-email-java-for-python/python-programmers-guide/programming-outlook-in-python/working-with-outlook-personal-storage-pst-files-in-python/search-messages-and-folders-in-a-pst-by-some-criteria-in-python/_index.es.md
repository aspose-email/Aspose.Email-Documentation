---
title: "Buscar Mensajes y Carpetas en un PST por Algunos Criterios en Python"
url: /es/java/search-messages-and-folders-in-a-pst-by-some-criteria-in-python/
weight: 60
type: docs
---

## **Aspose.Email - Buscar Mensajes y Carpetas en un PST por Algunos Criterios**
Para buscar mensajes y carpetas en un PST por algunos criterios usando **Aspose.Email Java para Python**, utiliza el siguiente código.

**Código en Python**

```python



\# Cargar el archivo PST de Outlook

personalStorage = self.PersonalStorage

pst = personalStorage.fromFile(self.dataDir + "sample1.pst")

folder = pst.getRootFolder().getSubFolder("myInbox")

builder = self.PersonalStorageQueryBuilder()

    # Mensajes de alta importancia

mapiImportance = self.MapiImportance

builder.getImportance().equals(mapiImportance.High)

messages = folder.getContents(builder.getQuery())

print "Mensajes con alta importancia:" 

print messages.size()

#builder = PersonalStorageQueryBuilder()

builder.getMessageClass().equals("IPM.Note")

messages = folder.getContents(builder.getQuery())

print "Mensajes con IPM.Note:" 

print messages.size()

\# Mensajes con archivos adjuntos Y alta importancia

builder.getImportance().equals(mapiImportance.High)

mapiMessageFlags = self.MapiMessageFlags

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Mensajes con archivos adjuntos: " 

print messages.size()

\# Mensajes con tamaño > 15 KB

builder.getMessageSize().greater(15000)

messages = folder.getContents(builder.getQuery())

print "mensajes tamaño > 15Kb:" 

print messages.size()

\# Mensajes no leídos

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

messages = folder.getContents(builder.getQuery())

print "No leídos:" 

print messages.size()

\# Mensajes no leídos con archivos adjuntos

builder.hasNoFlags(mapiMessageFlags.MSGFLAG_READ)

builder.hasFlags(mapiMessageFlags.MSGFLAG_HASATTACH)

messages = folder.getContents(builder.getQuery())

print "Mensajes no leídos con archivos adjuntos: " 

print messages.size()

```
## **Descargar Código en Ejecución**
Descarga **Buscar Mensajes y Carpetas en un PST por Algunos Criterios (Aspose.Email)** de cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)