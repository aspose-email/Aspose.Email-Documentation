---
title: "Creación y Guardado de Archivos MSG"
url: /es/python-net/creando-y-guardando-archivos-msg/
weight: 10
type: docs
---

Aspose.Email admite la creación de archivos de mensaje de Outlook (MSG). Este artículo explica cómo:

- Crear mensajes MSG.
- Crear mensajes MSG con archivos adjuntos.
- Crear un mensaje MSG con un cuerpo RTF.
- Guardar un mensaje como borrador.
- Trabajar con la compresión del cuerpo.
## **Creación y Guardado de Mensajes de Outlook**
La clase MailMessage tiene el método Save() que puede guardar archivos MSG de Outlook en disco o en un flujo. Los fragmentos de código a continuación crean una instancia de la clase MailMessage, establecen propiedades como de, para, asunto y cuerpo. El método Save() toma el nombre del archivo como un argumento. Además, los mensajes de Outlook se pueden crear con un cuerpo RTF comprimido utilizando MapiConversionOptions. Para configurarlo, crea una nueva aplicación de Windows y agrega una referencia a la dll de Aspose.Email en el proyecto.

1. Crea una nueva instancia de la clase MailMessage y establece las propiedades De, Para, Asunto y Cuerpo.
1. Llama al método FromMailMessage de la clase MailMessage, que acepta un objeto del tipo MailMessage. El método FromMailMessage() convierte el MailMessage en un MailMessage (MSG).
1. Llama al método MapiMessage.Save() para guardar el archivo MSG.

Escribe el siguiente código en el evento de clic del control de botón de la aplicación de Windows.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingAndSavingOutlookMSG-CreatingAndSavingOutlookMSG.py" >}}
## **Creación de Archivos MSG Con Archivos Adjuntos**
En el ejemplo anterior, creamos un archivo MSG simple. Aspose.Email también admite guardar archivos de mensaje con archivos adjuntos. Todo lo que necesitas hacer es agregar los archivos adjuntos a la instancia de MailMessage. Agrega archivos adjuntos llamando al método Add() en la colección MailMessage.Attachments. Agrega un cuadro de lista al formulario creado anteriormente y añade dos botones, uno para agregar y otro para eliminar archivos adjuntos. La aplicación que agrega archivos adjuntos funciona así:

1. Cuando se hace clic en el botón **Agregar Adjuntos**, se muestra un **Diálogo de Apertura de Archivo** para ayudar a los usuarios a explorar y seleccionar el archivo adjunto.
1. Cuando se ha seleccionado un archivo, la ruta completa se añade a una lista.
1. Cuando se crea el archivo MSG, las rutas de los archivos adjuntos se obtienen de la lista y se añaden a la colección MailMessage.Attachments.

Escribe el siguiente código en el evento de clic del botón **Agregar Adjuntos**.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingMSGAttachments-AddingMSGAttachments.py" >}}

Agrega el código para añadir los archivos adjuntos a la instancia de MailMessage. El código final para la función Write Msg se escribe a continuación.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-AddingMSGAttachments-AddingMSGAttachments.py" >}}

## **Creación de Archivos MSG Con Cuerpo RTF**
También puedes crear archivos de mensaje de Outlook (MSG) con cuerpos de texto enriquecido (RTF) utilizando Aspose.Email. El cuerpo RTF admite el formato de texto. Crea uno configurando la propiedad MailMessage.HtmlBody. Cuando conviertes una instancia de MailMessage en una instancia de MailMessage, el cuerpo HTML se convierte en RTF. De esta manera, se preserva el formato del cuerpo del correo electrónico.

El siguiente ejemplo crea un archivo MSG con un cuerpo RTF. Hay un encabezado y se aplica formato de negrita y subrayado en el cuerpo HTML. Este formato se mantiene cuando el HTML se convierte en RTF.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-CreatingMSGFilesWithRtfBody-CreatingMSGFilesWithRtfBody.py" >}}
## **Guardando Mensaje en Estado de Borrador**
Los correos electrónicos se guardan como borradores cuando alguien ha comenzado a editarlos pero desea volver a ellos para completarlos más tarde. Aspose.Email admite guardar mensajes de correo electrónico en estado de borrador configurando una bandera de mensaje. A continuación se muestra un código de ejemplo para guardar un mensaje de correo electrónico de Outlook (MSG) como borrador.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SavingMessageInDraftStatus-SavingMessageInDraftStatus.py" >}}
## **Implicaciones de la Compresión del Cuerpo**
El método de compresión del cuerpo RTF se puede utilizar para generar un MSG de tamaño más pequeño. Sin embargo, esto resulta en una velocidad más lenta. Para crear mensajes con mayor velocidad, establece la bandera en falso. Esta bandera, a su vez, tiene efecto en los PST creados: archivos MSG más pequeños resultan en PST más pequeños, y archivos MSG grandes devuelven una creación de PST más lenta.

{{< gist "aspose-email" "356f0e128b9d45a7ee779fc813eb87e5" "Examples-WorkingWithOutlookMSGs-SetBodyCompression-SetBodyCompression.py" >}}