---
title: "Crear un nuevo archivo PST y agregar subcarpetas"
url: /es/cpp/create-new-pst-file-and-add-subfolders/
weight: 10
type: docs
---

## **Creación de un nuevo archivo PST y adición de subcarpetas**
Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo muestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. Crear un nuevo archivo PST.
1. Cambiar la clase de contenedor de una carpeta.

Use la clase PersonalStorage para crear un archivo PST en alguna ubicación de un disco local. Para crear un archivo PST desde cero:

1. Cree un PST con el método PersonalStorage.create ().
1. Agregue una subcarpeta en la raíz del archivo PST accediendo a la carpeta raíz y, a continuación, llamando al método AddSubFolder.

El siguiente fragmento de código muestra cómo crear un archivo PST y agregar una subcarpeta denominada Bandeja de entrada.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.cpp" >}}
## **Cambiar la clase de contenedor de una carpeta**
A veces es necesario cambiar la clase de carpeta de una carpeta. Un ejemplo común es cuando se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En estos casos, es necesario cambiar la clase de carpeta para que todos los elementos de la carpeta se muestren correctamente. El siguiente fragmento de código muestra cómo cambiar la clase contenedora de una carpeta en PST para este fin.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ChangeFolderContainerClass-ChangeFolderContainerClass.cpp" >}}
