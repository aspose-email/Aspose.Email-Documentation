---
title: "Trabajando con IBM Notes"
url: /es/java/working-with-ibm-notes/
weight: 120
type: docs
---


## **Acerca de IBM Notes**
IBM Notes es el cliente y IBM Domino es el servidor de una plataforma de software colaborativa cliente-servidor. IBM Notes proporciona características de colaboración como correo electrónico, calendarios, listas de tareas, gestión de contactos, etc. El archivo de base de datos utilizado por IBM Notes se guarda en el formato de Notes Storage Facility (NSF).
## **Leer mensajes del archivo de almacenamiento NSF**

{{% alert color="primary" %}} 

Nota, la implementación de NSF es bastante limitada.
En general, es posible enfrentar algunos problemas en los siguientes casos:
 - El archivo fue creado por Notes versión 7 o superior
 - Se utiliza compresión LZ1

{{% /alert %}}

Aspose.Email proporciona la clase [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) para leer archivos de almacenamiento NSF. La clase [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) ofrece el método [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) que itera sobre los mensajes en el archivo de almacenamiento NSF. El siguiente código de muestra demuestra el uso de la clase [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) y el método [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) para leer mensajes del archivo de almacenamiento NSF. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessagesFromNSFStorage-1.java" >}}

{{% alert color="primary" %}} 

Por favor, tenga en cuenta que solo se ha implementado la lectura de mensajes. La lectura de carpetas aún no está soportada debido a la falta de especificación.

{{% /alert %}}