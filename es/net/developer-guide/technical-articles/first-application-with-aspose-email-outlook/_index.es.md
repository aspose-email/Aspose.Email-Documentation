---
title: "Primera aplicación con Aspose.Email.Outlook"
url: /es/net/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---

Esta sección demuestra cómo utilizar [Aspose.Email.Mapi](http://www.aspose.com/api/net/email/aspose.email.mapi/). Creamos una pequeña aplicación que carga un archivo de mensaje de Outlook (TestMessage.msg) y muestra el asunto, las direcciones de origen y destino, y el contenido del cuerpo en un formulario de Windows. Siga estos pasos para crear su primera aplicación utilizando Aspose.Email.Outlook.

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo**, luego **Proyecto**.
1. Elija crear una aplicación de Windows en C# o VB.NET.
1. Importe el DLL de Aspose.Email en la aplicación haciendo clic derecho en **Referencia** en el Explorador de soluciones. Esta será una aplicación basada en Windows que solo mostrará la información contenida en el archivo de mensaje.
1. Cree una instancia de la clase [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.mapi/MapiMessage) proporcionando la ruta del archivo de mensaje.
1. Utilice las propiedades públicas para mostrar el asunto, de, para y el cuerpo en los controles de Windows.

La implementación de los pasos anteriores se demuestra a continuación en el siguiente fragmento de código. Use el siguiente código detrás del botón **Cargar archivo Msg** o en el evento OnLoad del formulario.

{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailOutlookSampleApp-AsposeEmailOutlook.cs" >}}