---
title: "Crear un nuevo archivo PST y agregar subcarpetas"
url: /es/cpp/crear-nuevo-archivo-pst-y-agregar-subcarpetas/
weight: 10
type: docs
---

## **Crear un nuevo archivo PST y agregar subcarpetas**
Además de analizar un archivo PST existente, Aspose.Email proporciona los medios para crear un archivo PST desde cero. Este artículo demuestra cómo crear un archivo PST de Outlook y agregarle una subcarpeta.

1. Crear un nuevo archivo PST.
1. Cambiar la clase de contenedor de una carpeta.

Utiliza la clase PersonalStorage para crear un archivo PST en alguna ubicación en un disco local. Para crear un archivo PST desde cero:

1. Crea un PST usando el método PersonalStorage.Create().
1. Agrega una subcarpeta en la raíz del archivo PST accediendo a la carpeta Raíz y luego llamando al método AddSubFolder.

El siguiente fragmento de código te muestra cómo crear un archivo PST y agregarle una subcarpeta llamada Inbox.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-CreateNewPSTFileAndAddingSubfolders-CreateNewPSTFileAndAddingSubfolders.cpp" >}}
## **Cambiar la clase de contenedor de una carpeta**
A veces es necesario cambiar la clase de carpeta de una carpeta. Un ejemplo común es donde se agregan mensajes de diferentes tipos (citas, mensajes, etc.) a la misma carpeta. En tales casos, la clase de carpeta necesita cambiarse para que todos los elementos en la carpeta se muestren correctamente. El siguiente fragmento de código te muestra cómo cambiar la clase de contenedor de una carpeta en PST para este propósito.



{{< gist "aspose-email" "ef0db907527892c88c557bb418093cee" "Examples-EmailCPP-Outlook-ChangeFolderContainerClass-ChangeFolderContainerClass.cpp" >}}