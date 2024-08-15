---
title: "Primera aplicación con Aspose.Email.Outlook"
url: /es/net/first-application-with-aspose-email-outlook/
weight: 280
type: docs
---


En esta sección se muestra cómo usar [Aspose.Email.Mapi](http://www.aspose.com/api/net/email/aspose.email.mapi/). Creamos una pequeña aplicación que carga un archivo de mensajes de Outlook (TestMessage.msg) y muestra el asunto, las direcciones de origen y destino y el contenido del cuerpo en un formulario de Windows. Siga estos pasos para crear su primera aplicación con Aspose.Email.Outlook.

1. En Visual Studio, en el **File** menú, seleccionar **New**, entonces **Project**.
1. Elija crear una aplicación de Windows en C# o VB.NET.
1. Importe la DLL Aspose.Email en la aplicación haciendo clic con el botón derecho **Reference** en el Explorador de soluciones. Será una aplicación basada en Windows que solo mostrará la información contenida en el archivo de mensajes.
1. Crea una instancia del [MapiMessage](http://www.aspose.com/api/net/email/aspose.email.mapi/MapiMessage) clase dando la ruta del archivo de mensajes.
1. Utilice las propiedades públicas para mostrar el asunto, el origen, el destino y el cuerpo en los controles de Windows.

La implementación de los pasos anteriores se muestra a continuación en el siguiente fragmento de código. Usa el siguiente código detrás del **Cargar archivo de mensajes** botón o en el evento onLoad del formulario.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-Knowledge-Base-AsposeEmailOutlookSampleApp-AsposeEmailOutlook.cs" >}}
