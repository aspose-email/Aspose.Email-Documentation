---
title: "Trabajando con IBM Notes"
url: /es/java/working-with-ibm-notes/
weight: 120
type: docs
---


## **Acerca de IBM Notes**
IBM Notes es el cliente e IBM Domino es el servidor de una plataforma de software colaborativo cliente-servidor. IBM Notes proporciona funciones de colaboración como el correo electrónico, los calendarios, las listas de tareas pendientes, la gestión de contactos, etc. El archivo de base de datos utilizado por IBM Notes se guarda en el formato Notes Storage Facility (NSF).
## **Lea los mensajes del archivo de almacenamiento NSF**

{{% alert color="primary" %}}

Tenga en cuenta que la implementación de NSF es bastante limitada.
En general, es posible enfrentarse a algunos problemas en los siguientes casos:
 - El archivo se creó con la versión 7 y superior de Notes
 - Se utiliza la compresión LZ1

{{% /alert %}}

Aspose.Email proporciona la [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) clase para leer archivos de almacenamiento NSF. El [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) la clase proporciona la [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) método que recorre en iteración los mensajes del archivo de almacenamiento NSF. El siguiente código de ejemplo demuestra el uso del [NotesStorageFacility](https://reference.aspose.com/email/java/com.aspose.email/notesstoragefacility) clase y el [EnumerateMessages](https://reference.aspose.com/email/java/com.aspose.email/NotesStorageFacility#enumerateMessages\(\)) método para leer los mensajes del archivo de almacenamiento NSF. 



{{< gist "aspose-com-gists" "709d733586ce50505c3bca3f6e8bd18d" "Examples-src-main-java-com-aspose-email-examples-email-ReadMessagesFromNSFStorage-1.java" >}}

{{% alert color="primary" %}}

Tenga en cuenta que solo se implementa la lectura de mensajes. Todavía no se admite la lectura de carpetas debido a la falta de especificaciones.

{{% /alert %}}
