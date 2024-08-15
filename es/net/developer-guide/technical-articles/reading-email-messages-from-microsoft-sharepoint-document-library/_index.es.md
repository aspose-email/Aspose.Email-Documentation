---
title: "Lectura de mensajes de correo electrónico de la biblioteca de documentos de Microsoft SharePoint"
url: /es/net/reading-email-messages-from-microsoft-sharepoint-document-library/
weight: 110
type: docs
---


Este artículo muestra cómo leer los mensajes de correo electrónico de una biblioteca de documentos de Microsoft SharePoint. Para acceder a los archivos de una biblioteca de documentos de SharePoint, el SDK de SharePoint debe estar instalado en el sistema. El SDK proporciona la API necesaria para iniciar sesión y acceder a los archivos de la biblioteca de documentos.
## **Lectura de mensajes de correo electrónico de SharePoint**
En los siguientes ejemplos de programación se presupone que un archivo de mensajes de Microsoft Outlook (.msg) ya está almacenado en la carpeta SharedDocument de la biblioteca de documentos de SharePoint. El SDK de SharePoint se usa para incluir el archivo de mensajes en una transmisión y, a continuación, pasar esta secuencia a una instancia de Aspose.Email [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) clase. La clase MailMessage carga la transmisión y analiza el archivo de mensajes de Outlook. Después de eso, acceda a las propiedades de la clase MailMessage, por ejemplo, el asunto, el cuerpo del texto, el cuerpo del HTML, etc., para usar la información en un proyecto de Visual Studio. Para obtener información sobre cómo instalar y configurar Microsoft SharePoint Server y el SDK, consulte las secciones correspondientes de la biblioteca de MSDN. El siguiente fragmento de código muestra cómo leer los mensajes de correo electrónico de SharePoint.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-ReadingEmailMessagesFromSharePoint-ReadingEmailMessagesFromSharePoint.cs" >}}
