---
title: "Leer un archivo de mensaje de Outlook (MSG)"
url: /es/java/reading-an-outlook-message-msg-file/
weight: 10
type: docs
---


{{% alert color="primary" %}} 

Nuestros consejos de migración muestran cómo los productos de Aspose pueden utilizarse para mejorar sus aplicaciones y liberarle de la dependencia de la automatización tradicional.

Este consejo de migración muestra cómo leer un archivo de mensaje de Microsoft Outlook y mostrar su contenido en la pantalla utilizando tanto [Automatización de Microsoft Office](#office-automation) como código de [Aspose.Email](#asposeemail-for-java). El código de muestra a continuación solo muestra el contenido en la consola para darle una idea de cómo funciona. Use los fragmentos de código en su propia aplicación de Windows, web u otra.

{{% /alert %}} 
## **Automatización de Office**
Para usar objetos de Automatización de Office para Microsoft Outlook, necesita agregar referencias a las bibliotecas de Microsoft Office y Microsoft Office Interop para Outlook a su proyecto.
### **Ejemplos de programación**
**C#**

~~~cs

// Agregar los espacios de nombres

using Microsoft.Office;

using Microsoft.Office.Interop.Outlook;

// Crear una nueva clase de aplicación

Application app = new Application();

// Crear un objeto MailItem

MailItem item = (MailItem)outlook.CreateItemFromTemplate(@"d:\temp\test.msg", Type.Missing);

// Acceder a diferentes campos del mensaje

System.Console.WriteLine(string.Format("Asunto:{0}", item.Subject));

System.Console.WriteLine(string.Format("Dirección de correo del remitente:{0}", item.SenderEmailAddress));

System.Console.WriteLine(string.Format("Nombre del Remitente:{0}", item.SenderName));

System.Console.WriteLine(string.Format("Para:{0}", item.To));

System.Console.WriteLine(string.Format("CC:{0}", item.CC));

System.Console.WriteLine(string.Format("CCO:{0}", item.BCC));

System.Console.WriteLine(string.Format("Cuerpo Html:{0}", item.HTMLBody));

System.Console.WriteLine(string.Format("Cuerpo de texto:{0}", item.Body));


~~~
## **Aspose.Email para Java**
El siguiente fragmento de código hace lo mismo que [el código anterior](/#office-automation) utilizando Aspose.Email para Java.

Para acceder a los objetos [Aspose.Email Outlook](https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage), necesita agregar una referencia a Aspose.Email en su proyecto.
### **Ejemplos de programación**

~~~java

// Crear un nuevo objeto de tipo MapiMessage
MapiMessage msg = MapiMessage.fromFile("d:\\temp\\test.msg");

// Acceder a los campos del mensaje
System.out.println("Asunto: " + msg.getSubject());
System.out.println("Dirección de correo del remitente: " + msg.getSenderEmailAddress());
System.out.println("Nombre del Remitente:{0}" + msg.getSenderName());
System.out.println("Para:{0}" + msg.getDisplayTo());
System.out.println("CC:{0}" + msg.getDisplayCc());
System.out.println("CCO:{0}" + msg.getDisplayBcc());
System.out.println("Cuerpo Html:{0}" + msg.getBodyHtml());
System.out.println("Cuerpo de texto:{0}" + msg.getBody());
System.out.println("Cuerpo Rtf:{0}" + msg.getBodyRtf());


~~~