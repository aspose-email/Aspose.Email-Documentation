---
title: "Lectura de mensajes de correo electrónico de la biblioteca de documentos de Microsoft SharePoint"
url: /es/net/lectura-de-mensajes-de-correo-electronico-de-la-biblioteca-de-documentos-de-microsoft-sharepoint/
weight: 110
type: docs
---


Este artículo muestra cómo leer mensajes de correo electrónico de una biblioteca de documentos de Microsoft SharePoint. Para acceder a archivos en una biblioteca de documentos de SharePoint, el SDK de SharePoint debe estar instalado en el sistema. El SDK proporciona la API necesaria para iniciar sesión y acceder a los archivos de la biblioteca de documentos.
## **Lectura de mensajes de correo electrónico desde SharePoint**
Los ejemplos de programación a continuación suponen que un archivo de mensaje de Microsoft Outlook (.msg) ya está almacenado en la carpeta SharedDocument de la biblioteca de documentos de SharePoint. Se utiliza el SDK de SharePoint para obtener el archivo de mensaje en un flujo y luego pasar este flujo a una instancia de la clase [MailMessage](http://www.aspose.com/api/net/email/aspose.email/mailmessage) de Aspose.Email. La clase MailMessage carga el flujo y analiza el archivo de mensaje de Outlook. Después de eso, acceda a las propiedades de la clase MailMessage, por ejemplo, asunto, cuerpo de texto, cuerpo HTML, etc., para utilizar la información en un proyecto de Visual Studio. Para obtener información sobre cómo instalar y configurar Microsoft SharePoint Server y el SDK, consulte las secciones respectivas en la biblioteca de MSDN. El siguiente fragmento de código muestra cómo leer mensajes de correo electrónico desde SharePoint.



{{< gist "aspose-email" "9e8fbeb51a8cbc4129dc71ca8cd55f0b" "Examples-CSharp-ReadingEmailMessagesFromSharePoint-ReadingEmailMessagesFromSharePoint.cs" >}}