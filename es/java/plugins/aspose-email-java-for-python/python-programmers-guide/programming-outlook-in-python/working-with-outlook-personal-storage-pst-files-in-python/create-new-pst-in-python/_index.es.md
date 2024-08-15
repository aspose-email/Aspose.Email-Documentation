---
title: "Crear un nuevo PST en Python"
url: /es/java/create-new-pst-in-python/
weight: 50
type: docs
---

## **Aspose.Email - Crear un nuevo PST**
Para crear un nuevo PST usando **Aspose.Email Java para Python**, Usa el siguiente código.

**Código Python**

``` python



\# Create an instance of PersonalStorage

personalStorage = self.PersonalStorage

pst = personalStorage.create(self.dataDir + "sample1.pst", 0)

\# Create a folder at root of pst

pst.getRootFolder().addSubFolder("myInbox")

\# Add message to newly created folder

mapi_message = self.MapiMessage

pst.getRootFolder().getSubFolder("myInbox").addMessage(mapi_message.fromFile(self.dataDir + "Message.msg"))

print "Created PST successfully."

```
## **Descargar Running Code**
Download **Crear un nuevo PST (Aspose.Email)** desde cualquiera de los sitios de codificación social mencionados a continuación:

- [GitHub](https://github.com/aspose-email/Aspose.Email-for-Java/releases/tag/Aspose.Email_Java_for_Python-v1.0)
- [CodePlex](https://archive.codeplex.com/?p=asposeemailjavapython)
