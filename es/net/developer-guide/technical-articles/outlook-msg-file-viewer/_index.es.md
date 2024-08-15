---
title: "Visor de archivos MSG de Outlook"
url: /es/net/outlook-msg-file-viewer/
weight: 50
type: docs
---


Este artículo trata sobre el análisis y la visualización de archivos MSG de Microsoft Outlook. Si necesitas manipular archivos MSG en tu proyecto o aplicación, necesitas una API para analizar el formato MSG de Outlook. O bien, si no tiene Microsoft Outlook instalado en su sistema, puede crear su propio visor para obtener el contenido del archivo MSG.

Los ejemplos de código de este artículo muestran cómo analizar un archivo MSG de Outlook en una aplicación de C# mediante la biblioteca Aspose.Email. Aspose.Email es una biblioteca.NET disponible como DLL. Utilice esta biblioteca para ver los archivos MSG en Windows, la web, la consola o cualquier aplicación basada en .NET. La versión de prueba de Aspose.Email puede ser [se descarga fácilmente](http://www.aspose.com/downloads/email/net). El siguiente código fuente del proyecto se incluye en los ejemplos proporcionados con el instalador.
## **Demostración de Outlook MSG Viewer**
Hemos creado una aplicación de demostración sencilla que se puede utilizar para analizar y ver archivos MSG. La interfaz de usuario se puede ver a continuación:

![todo:image_alt_text](outlook-msg-file-viewer_1.png)



El panel izquierdo muestra las unidades y carpetas del sistema, al igual que el explorador de Windows. Puede explorar las carpetas para mostrar o filtrar los archivos MSG. Solo los archivos MSG aparecen en el control de vista de lista superior de la carpeta correspondiente en la vista de árbol. Como puedes ver en la captura de pantalla anterior, los campos Asunto, De, Para y Cc aparecen en la lista superior. Si haces clic en cualquier mensaje de la lista, se abre el mensaje correspondiente y los detalles se pueden ver en la interfaz de usuario situada debajo del control de visualización de listas. Hemos utilizado etiquetas para mostrar la información de asunto, dirección, cc y origen.

En el panel inferior, hemos usado controles de pestañas para mostrar otros detalles del mensaje, como el cuerpo del texto, el cuerpo RTF, el encabezado del mensaje, los archivos adjuntos y las propiedades de MAPI. Si hace clic en el **Attachments** pestaña, muestra la lista de archivos adjuntos en el archivo MSG (si los hay). También puede guardar los archivos adjuntos en su sistema seleccionando un archivo adjunto y haciendo clic en **Save** botón. Abre el cuadro de diálogo Guardar archivo. Navegue hasta la carpeta deseada y guarde el archivo allí. La siguiente captura de pantalla muestra el **Attachments** vista de pestañas.

![todo:image_alt_text](outlook-msg-file-viewer_2.png)
## **Análisis y visualización del contenido del archivo MSG mediante programación**
En esta sección, presentaremos el código que utilizamos en la demostración para mostrar el contenido del archivo MSG.
### **Carga de un archivo MSG**
La biblioteca Aspose.Email proporciona [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) clase para cargar y analizar archivos MSG. Puedes cargar el archivo MSG usando una sola línea de código llamando al método estático fromFile () y pasando la ruta al archivo MSG. El siguiente fragmento de código muestra cómo cargar un archivo MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-LoadingMSGFile-LoadingMSGFile.cs" >}}
### **Obtener el origen, el destino, el cc y el asunto de un archivo MSG**
The [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) La clase expone propiedades y colecciones para obtener la información del asunto, el origen, el destino y el cc. A continuación se muestra el código de ejemplo para obtener estas propiedades. El siguiente fragmento de código muestra cómo obtener el origen, el destino, el cc y el asunto de un archivo MSG.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMessageProperties-GetMessageProperties.cs" >}}
### **Obtención de los cuerpos de texto y RTF**
Podemos obtener los cuerpos de texto y RTF del mensaje usando las propiedades del [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) clase. El siguiente fragmento de código muestra cómo obtener cuerpos de texto y RTF.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Outlook-GetTheTextAndRTFBodies-GetTheTextAndRTFBodies.cs" >}}
### **Obtener archivos adjuntos del archivo MSG y guardarlos en el disco**
The [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) la clase proporciona la [Attachments](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessageitembase/properties/attachments) colección para obtener todos los archivos adjuntos del archivo de mensajes (MSG). La propiedad MAPIMessage.attachments devuelve un objeto de tipo MAPIAttachmentCollection. Puede usar un bucle para cada uno para recorrer en iteración la colección de archivos adjuntos y enumerar los archivos adjuntos. La clase Attachment contiene el método Save () para guardar el adjunto individual en el disco. El siguiente fragmento de código muestra cómo obtener la lista de archivos adjuntos y cómo guardarlos.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetAttachmentsFromMSGFile-GetAttachmentsFromMSGFile.cs" >}}
### **Obtener las propiedades MAPI del archivo MSG**
Puede obtener las propiedades de MAPI del archivo MSG mediante [MapiMessage](https://apireference.aspose.com/email/net/aspose.email.mapi/mapimessage) colección de propiedades de clase. El código de ejemplo que aparece a continuación muestra cómo obtener todas las propiedades de MAPI en el archivo de mensajes.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-GetMAPIProperties-GetMAPIProperties.cs" >}}
