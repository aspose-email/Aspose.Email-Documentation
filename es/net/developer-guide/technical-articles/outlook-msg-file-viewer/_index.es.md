---
title: "Visor de Archivos MSG de Outlook"
url: /es/net/outlook-msg-file-viewer/
weight: 50
type: docs
---


Este artículo trata sobre el análisis y la visualización de archivos MSG de Microsoft Outlook. Si necesitas manipular archivos MSG en tu proyecto o aplicación, necesitas una API para analizar el formato MSG de Outlook. O, si no tienes Microsoft Outlook instalado en tu sistema, puedes construir tu propio visor para obtener el contenido del archivo MSG.

Los ejemplos de código en este artículo muestran cómo analizar un archivo MSG de Outlook en una aplicación C# utilizando la biblioteca Aspose.Email. Aspose.Email es una biblioteca .NET disponible como DLL. Utiliza esta biblioteca para ver archivos MSG en Windows, web, consola o cualquier aplicación basada en .NET. La versión de prueba de Aspose.Email se puede [descargar fácilmente](http://www.aspose.com/downloads/email/net). El código fuente del proyecto a continuación está incluido en los ejemplos proporcionados con el instalador.
## **Demo del Visor de MSG de Outlook**
Hemos creado una aplicación demo simple que se puede usar para analizar y ver archivos MSG. La interfaz de usuario se puede ver a continuación: 

![todo:image_alt_text](outlook-msg-file-viewer_1.png)



El panel izquierdo muestra las unidades y las carpetas en el sistema, al igual que lo hace el explorador de Windows. Puedes navegar por las carpetas para mostrar o filtrar los archivos MSG. Solo los archivos MSG aparecen en el control de vista de lista superior en la carpeta correspondiente en la vista de árbol. Como puedes ver en la captura de pantalla anterior, los campos Asunto, De, Para y CC se muestran en la lista superior. Si haces clic en cualquier MSG en la lista, se abre el mensaje correspondiente y los detalles se pueden ver en la interfaz de usuario debajo del control de vista de lista. Hemos utilizado etiquetas para mostrar la información de asunto, para, cc y de.

En el panel inferior, hemos utilizado controles de pestañas para mostrar otros detalles del mensaje como el cuerpo del texto, cuerpo RTF, encabezado del mensaje, adjuntos y propiedades MAPI. Si haces clic en la pestaña **Adjuntos**, muestra la lista de adjuntos en el archivo MSG (si los hay). También puedes guardar los adjuntos en tu sistema seleccionando un adjunto y haciendo clic en el botón **Guardar**. Se abre el cuadro de diálogo Guardar Archivo. Navega a la carpeta deseada y guarda el archivo allí. La siguiente captura de pantalla muestra la vista de la pestaña **Adjuntos**. 

![todo:image_alt_text](outlook-msg-file-viewer_2.png)
## **Análisis y Visualización de Contenidos del Archivo MSG Programáticamente**
En esta sección, presentaremos el código que utilizamos en la demostración para mostrar el contenido del archivo MSG.
### **Cargando un Archivo MSG**
La biblioteca Aspose.Email proporciona la clase [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) para cargar y analizar archivos MSG. Puedes cargar el archivo MSG utilizando una sola línea de código llamando al método estático FromFile() y pasando la ruta al archivo MSG. El siguiente fragmento de código te muestra cómo cargar un archivo MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-LoadingMSGFile-LoadingMSGFile.cs" >}}
### **Obteniendo De, Para, CC y Asunto de un Archivo MSG**
La clase [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) expone propiedades y colecciones para obtener la información de asunto, de, para y cc. A continuación, el código de ejemplo para obtener estas propiedades. El siguiente fragmento de código te muestra cómo obtener De, Para, CC y Asunto de un archivo MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMessageProperties-GetMessageProperties.cs" >}}
### **Obteniendo los Cuerpos de Texto y RTF**
Podemos obtener los cuerpos de texto y RTF del mensaje utilizando las propiedades de la clase [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage). El siguiente fragmento de código te muestra cómo obtener los cuerpos de texto y RTF.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetTheTextAndRTFBodies-GetTheTextAndRTFBodies.cs" >}}
### **Obteniendo Adjuntos de un Archivo MSG y Guardando en Disco**
La clase [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) proporciona la colección [Attachments](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/attachments) para obtener todos los adjuntos en el archivo de mensaje (MSG). La propiedad MapiMessage.Attachments devuelve un objeto de tipo MapiAttachmentCollection. Puedes usar un bucle for-each para iterar a través de la colección de adjuntos y listar los adjuntos. La clase Attachment contiene el método Save() para guardar el adjunto individual en disco. El siguiente fragmento de código te muestra cómo obtener la lista de adjuntos y guardarlos.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetAttachmentsFromMSGFile-GetAttachmentsFromMSGFile.cs" >}}
### **Obteniendo las Propiedades MAPI del Archivo MSG**
Puedes obtener las propiedades MAPI del archivo MSG utilizando la colección Properties de la clase [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage). El código de ejemplo a continuación muestra cómo obtener todas las propiedades MAPI en el archivo de mensaje.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMAPIProperties-GetMAPIProperties.cs" >}}