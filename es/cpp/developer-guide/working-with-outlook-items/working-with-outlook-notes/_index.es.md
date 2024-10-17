---
title: "Trabajando con Notas de Outlook"
url: /es/cpp/working-with-outlook-notes/
weight: 100
type: docs
---

## **Creando, Guardando y Leyendo Notas**
Aspose.Email ofrece la posibilidad de crear notas de Outlook y guardarlas en disco en formato MSG. La clase MapiNote proporciona propiedades y métodos para establecer información de tareas. Este artículo muestra cómo crear, guardar y leer un MapiNote desde disco.
### **Creando y Guardando una Nota de Outlook**
Los siguientes pasos se pueden utilizar para crear y guardar una nota en disco:

1. Instanciar un objeto de la clase MapiNote.
1. Establecer varias propiedades.
1. Guardar la nota en disco como un archivo MSG.

El siguiente fragmento de código te muestra cómo crear y guardar una Nota de Outlook.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreatAndSaveAnOutlookNote-CreatAndSaveAnOutlookNote.cpp" >}}
### **Leyendo un MapiNote**
El objeto de la clase MapiNote se utiliza para convertir el objeto MapiMessage que carga una nota desde disco en formato MSG. El siguiente fragmento de código te muestra cómo leer un MapiNote.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ReadMapiNote-ReadMapiNote.cpp" >}}